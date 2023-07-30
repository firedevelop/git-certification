# git-certification

#  Installation
https://gist.github.com/Klerith/90a612344dc2d4e4455ea810fdacbe69

# Update/upgrade git on mac
brew install git
brew upgrade git


## Free eBook
https://git-scm.com/book/en/v2 

# Commands
git version
git --version

git help

- / abreviation
-- // full words
### create local repository
create the folder .git
`git init`

### in color red the files peding to commint
git status

![alt text](https://github.com/firedevelop/git-github-certification/blob/main/images/1.png?raw=true)


git log

### add all files
git add .

### exclude the file exclude.txt
git reset exclude.txt
// Now is missing the file
```
git status
```

```ruby
require 'redcarpet'
markdown = Redcarpet.new("Hello World!")
puts markdown.to_html
```

### comit
git commit -m "first commit"

### restore file
git checkout -- .

### U
means untrack, when git no le da seguimiento a ese archivo  