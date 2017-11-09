Insert this into the file `~/.bash_profile` to set up your terminal.

```bash
PROMPT_COMMAND=build_prompt

function build_prompt {
  TIMESTAMP="\t"
  USER="\u"
  WORKING_DIRECTORY="\W"
  WORKING_PATH="\[\033[32m\]\w\[\033[33m\]"
  WORKSTATION_NAME="\h"
  GIT_BRANCH="\$(parse_git_branch)\[\033[00m\]"

  # Set the primary prompt
  PS1="${USER} ${WORKING_PATH}${GIT_BRANCH} -> "
}

function parse_git_branch() {
  git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
}
```
