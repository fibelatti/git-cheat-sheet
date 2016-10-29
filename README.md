# git cheat sheet

Simple cheat sheet used to remember a few useful git commands

## general flow

	1. git fetch origin
	2. git merge origin/BRANCH_TO_BE_MERGED (git diff BRANCH origin/BRANCH to see changes)
	3. git checkout -b BRANCHNAME
	
	4. git add
	5. git commit -m "MESSAGE"
	6. git push -u origin BRANCHNAME
	7. (Web) PR (link do freshdesk, comentar 'CR [mention do reviwer])
	
	8. git rebase -p origin/BASEBRANCH
	9. git push -f

	(web)
	10. (Web) Merge PR -> Delete branch
	11. git checkout develop
	12. git fetch origin
	13. git merge origin/develop
	
	(command line)
	10. git checkout develop
	11. git merge --no-ff BRANCHNAME
	12. Resolve conflits if any with 'subl filepath' then git add . and git commit
	13. git push origin develop
	
	14. git branch -d BRANCHNAME
	15. (web) delete branch
	16. git tag TAGNAME
	17. git push --tags

## git stashing

	1. git stash save STASHNAME
	2. git stash list
	3. git stash apply stash@{POS}
	4. git stash drop stash@{POS}

	3. git stash pop

## git rewriting history !!! NOT SAFE !!!

	1. git reset COMMITHASH
	2. git push -f	

## git deleting tags
	1. git tag -d TAGNAME (local)
	2. git push --delete origin TAGNAME (remote)

## git search by commit message
	1. git log --all --grep='TERM' 

## git search by code
	1. git log -p --all -S 'CODE_SNIP' --until=YYYY.MM.DD

## git show most changed files
	1. git effort --above COMMITCOUNT -- --after="one month ago" 

## git check last versioning 
	1. git log -p --all --follow PATH (source/build.gradle for android)

## git update remotes list
	1. git remote prune origin 

## git applying gitignore for repository existing files (http://stackoverflow.com/a/7532131)
	1. git ls-files -ci --exclude-standard
	2. git ls-files -ci --exclude-standard -z | xargs -0 git rm --cached
	3. apply-gitignore = !git ls-files -ci --exclude-standard -z | xargs -0r git rm --cached