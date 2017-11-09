# Terminal

![My Terminal](https://github.com/amajor/workstation/blob/master/bash-profile/Terminal.png)

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

When you open a new Terminal window, you should see the new prompt.

I also like to change the styling on my Terminal app.

Go to **Terminal** > **Preferences** and click on the **Profiles** tab of the window.

If I stick with one of the themes provided by macOS, then I'll stick with something dark, like **Pro**. Highlight the theme you want, then click **Default** at the bottom of the list to set it as your terminal default theme.

Voila!
