**Guia para tirar print screens em background no Mac**

1. Desligar sound effects em System Preferences -> Sound -> Uncheck Play user interface sound effects
2. Instalar o tmux, e.g.
```
brew install tmux
```
3. Criar uma pasta para guardar os prints todos (vão ser muitos) e garantir que temos uns 5GB livres no pc para não haver stress de espaço, já estou a dar muita margem
4. Criar o seguinte script:
```
#!/bin/bash

while :
do
    screencapture -T 30 ~/Pictures/screenshots/raw_test/test_$(date +"%Y%m%d%H%M%S").jpg
done
```
. Lembrar de substituir o caminho por um que exista no teu computador

5. Criar uma nova sessão no tmux:
```
tmux new -s <session_name>
```
6. Dentro da nova sessão, pôr o script a correr. Pode ser preciso torná-lo executável com
```
chmod +x script.sh
```
7. Para sair da sessão do tmux, Ctrl+b e depois d
8. No final, para parar o script, matar a sessão do tmux com
```
tmux kill-session -t <session_name>
```
Podemos variar o tempo entre screenshots com a flag -T. No exemplo -T 30 significa que tira print de 30 em 30 segundos.
