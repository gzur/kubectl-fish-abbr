<!---
# Copyright 2019 Google Inc.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     https://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#
# This file was edited by Simon Johansson on 2019-10-13.
-->

# kubectl-fish-abbr

This adds many convenient kubectl abbrevations to your fish shell.
This file and the rest of the repository is based on [ahtmed/kubectl-aliases](https://github.com/ahmetb/kubectl-aliases).

### Examples

[![asciicast](demo.gif)](https://asciinema.org/a/4ylDea4mKFlFSp5nHurnkZwnV)

Some of the generated abbreviations are:

```fish
abbr -a -g -- k 'kubectl'
abbr -a -g -- kg 'kubectl get'
abbr -a -g -- kgpo 'kubectl get pod'

abbr -a -g -- ksysgpo 'kubectl --namespace=kube-system get pod'

abbr -a -g -- krm 'kubectl delete'
abbr -a -g -- krmf 'kubectl delete -f'
abbr -a -g -- krming 'kubectl delete ingress'
abbr -a -g -- krmingl 'kubectl delete ingress -l'
abbr -a -g -- krmingall 'kubectl delete ingress --all-namespaces'

abbr -a -g -- kgsvcoyaml 'kubectl get service -o=yaml'
abbr -a -g -- kgsvcwn 'watch kubectl get service --namespace'
abbr -a -g -- kgsvcslwn 'watch kubectl get service --show-labels --namespace'

abbr -a -g -- kgwf 'watch kubectl get -f'
```

See [the full list](conf.d/kubectl-fish-abbr.fish).

### Installation

Install with [fisher](https://github.com/jorgebucaran/fisher).

```fish
fisher install DrPhil/kubectl-fish-abbr
```

### Syntax explanation

* **`k`**=`kubectl`
  * **`sys`**=`--namespace kube-system`
* commands:
  * **`g`**=`get`
  * **`d`**=`describe`
  * **`rm`**=`delete`
  * **`a`**:`apply -f`
  * **`ex`**: `exec -i -t`
  * **`lo`**: `logs -f`
* resources:
  * **`po`**=pod, **`dep`**=`deployment`, **`ing`**=`ingress`,
    **`svc`**=`service`, **`cm`**=`configmap`, **`sec`=`secret`**,
    **`ns`**=`namespace`, **`no`**=`node`
* flags:
  * output format: **`oyaml`**, **`ojson`**, **`owide`**
  * **`all`**: `--all` or `--all-namespaces` depending on the command
  * **`sl`**: `--show-labels`
  * **`w`**=`-w/--watch`
* value flags (should be at the end):
  * **`n`**=`-n/--namespace`
  * **`f`**=`-f/--filename`
  * **`l`**=`-l/--selector`
  
### FAQ

- **Doesn't this slow down my shell start up?** It probably does. This measurement suggests that it will steal around 250ms from my life on each shell-startup. YMMV

```console
$ source conf.d/kubectl-aliases.fish
$ echo $CMD_DURATION
244

```
