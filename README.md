# awesome-git
A opiniated list of tips to power master git

Git as the rest of code and tools should serve features and not over-engineered project management.
It should be easy to use and save you time, not consume time.

- name branch using commitlint prefix `git checkout -b "feat/..."`
- create temporary commit `gwip` with [oh my zsh git aliases](https://github.com/ohmyzsh/ohmyzsh/blob/master/plugins/git/git.plugin.zsh)
- push code: `git push origin/feat/... ` or `ggp`
- fetch merge request: `git mr 1234` with git alias 
- delete mr branches `git mrc`
- list branches: `git branch` or `gb`
- come back to working branch `gco feat/<TAB>` with git alias 
- uncreate temporary commit `gunwip`
- create normal commit with autofilled template `git commit -a`
- commit title based on [angular conventional commitlint](https://github.com/conventional-changelog/commitlint/tree/master/@commitlint/config-conventional#type-enum)
- git extension ([Git lens on VS code](https://gitlens.amod.io/))
- go to develop to rebase `git dev` then `git pull --rebase` or `gpr`
- `git rebase origin/develop` 
- resolve conflict 
- update branch then commit `git commit -a --amend` or `gca!`
- for push `git push --force origin/feat/... ` or `ggf`

## How to configure git

```sh
git config alias.mr '!sh -c '\''git fetch $1 merge-requests/$2/head:mr-$1-$2 && git checkout mr-$1-$2'\'' -'
git config alias.mrc '!sh -c '\''git branch | grep -w -i '\''mr-.*'\'' | xargs git branch -D'\'' -'
git config alias.wip '!sh -c '\''git add -A && git commit --no-verify --no-gpg-sign -m '\''--wip-- [skip ci]'\'''\'' -'
git config alias.unwip '!sh -c '\''git log -n 1 | grep -q -c -- "--wip--" && git reset HEAD~1'\'' -'
git config alias.dev '!sh -c '\''git checkout develop'\'''
git config --bool checkout.guess false

git config commit.template ".gitlab/merge_request_templates/Default.md"
```

