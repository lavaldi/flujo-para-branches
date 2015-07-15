de
prod->prod: git branch staging origin/prod
prod-->pre: git checkout pre
pre->pre: git push -u origin pre
pre->pre: git branch dev origin/pre
pre-->dev: git checkout dev
dev->dev: git push -u origin dev
dev->dev: git pull
dev->dev: git branch [branch]_[type]_[issue_number]_summary origin/dev
dev-->[branch]_[type]_[issue_number]_summary: git checkout [branch]_[type]_[issue_number]_summary
Note right of [branch]_[type]_[issue_number]_summary: Do your work
[branch]_[type]_[issue_number]_summary-->dev: git checkout dev
dev->dev: git pull
dev-->[branch]_[type]_[issue_number]_summary: git checkout [branch]_[type]_[issue_number]_summary
[branch]_[type]_[issue_number]_summary->[branch]_[type]_[issue_number]_summary: git rebase -i origin/dev
[branch]_[type]_[issue_number]_summary->[branch]_[type]_[issue_number]_summary: git push -u origin [branch]_[type]_[issue_number]_summary
Note right of [branch]_[type]_[issue_number]_summary: Ready for Code Review
Note left of [branch]_[type]_[issue_number]_summary: If Code Review was  declined.\n Fix the errors.
[branch]_[type]_[issue_number]_summary-->dev: git checkout dev
dev->dev: git pull
dev-->[branch]_[type]_[issue_number]_summary: git checkout [branch]_[type]_[issue_number]_summary
[branch]_[type]_[issue_number]_summary->[branch]_[type]_[issue_number]_summary: git rebase -i origin/dev
[branch]_[type]_[issue_number]_summary->[branch]_[type]_[issue_number]_summary: git push origin +[branch]_[type]_[issue_number]_summary
Note left of [branch]_[type]_[issue_number]_summary: If Code Review was approved.\n Do Pull Request
[branch]_[type]_[issue_number]_summary-->dev: git checkout dev
dev->dev: git merge [branch]_[type]_[issue_number]_summary
dev-->pre:git checkout pre
pre->pre: git pull
pre->pre: git merge dev
pre->pre: git push origin pre
Note left of pre: Test Cases from QA
pre-->prod: git checkout prod
prod->prod: git pull
prod->prod: git merge pre
prod->prod: git push origin prod
prod-->pre: git checkout pre
pre->pre: git pull
pre->pre: git rebase -i origin/prod
pre->pre: git push origin +pre
pre-->dev: git checkout dev
dev->dev: git pull
dev->dev: git rebase -i origin/pre
dev->dev: git push origin +dev
```

Image caption
-------

> **git branch [new_branch] [parent_branch]:** Create new branch based on parent branch.
> **git push -u [branch]: ** Push your changes and set up the stream between the local and the remote branch.
> **git pull: ** Combination of *git fetch*, which connects to the remote repository and fetches new commits, and *git merge* (or *git rebase*) which incorporates the new commits into your local branch. 
> **git rebase -i [parent_branch]:** Update your current branch based on the parent branch, so the commits from the parent branch are placed first that the commits from the current branch. The ‘-i’ option enables the the [interactive mode](http://git-scm.com/docs/git-rebase#_interactive_mode) .
> **git push origin +[branch]:** Force update to the remote branch with the local branch.
