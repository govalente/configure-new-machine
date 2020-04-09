*Guide for background screenshots on Mac*

1. Turn off sound effects in System Preferences -> Sound -> Uncheck Play user interface sound effects.
2. Install `tmux`.
```
brew install tmux
```
3. Create a directory for the screenshots and check if there's enough disk space for a lot of screenshots.
4. Create the following script:
```
#!/bin/bash

while :
do
    screencapture -T 30 ~/Pictures/screenshots/raw_test/test_$(date +"%Y%m%d%H%M%S").jpg
done
```
* Replace with the desired path for the screenshots.
* The time between screenshots is adjusted with the -T flag. In the example, `-T 30` means there will be a screenshot every 30s

5. Create new `tmux` session:
```
tmux new -s <session_name>
```
6. Run the script inside the new session. It may be necessary to make the script exectuable with:
```
chmod +x script.sh
```
7. Exit the `tmux` session with Ctrl+b & d.
8. When you want to stop the screenshot process kill the `tmux` session with:
```
tmux kill-session -t <session_name>
```
