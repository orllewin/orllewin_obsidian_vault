My memory...

### Remove Git

I always forget this:

```
rm -rf .git
```

## Quick Git Push
```
## Quick Git Push
Obviously not for projects that need a readable git history, but for blogs and similar:
```sh
#!/bin/bash

timestamp=$(date +%s)
echo "Saving: $timestamp"
git add .
git commit -m "$timestamp"
git push origin main
```

Save as `p.sh` and make executable: `chmod a+x p.sh` then run with `./p.sh`

## Repoclean
Hack to delete the commit history of a repo: `sh repoclean.sh`
```bash
#!/bin/bash

git checkout --orphan tmp
git add -A
git commit -m '...'
git branch -D main
git branch -m main
git push -f origin main
```

## Banish .DS_Store
```
find . -name .DS_Store -print0 | xargs -0 git rm -f --ignore-unmatch
echo .DS_Store >> .gitignore
git add .gitignore
git commit -m "DS_Store begone"
```
## Find String in Files
Will scan recursively in current directory
```sh
grep -r 'Orllewin' .
```

# Images/ImageMagick
## Resize and Crop
```bash
convert 'Healing Is A Miracle.jpg' -resize 350x155^ -gravity Center -crop 350x155+0+0 +repage output.jpg
```

## Batch Image Desaturate
Requires ImageMagick. Desaturate all images in a project: `desat.sh`. 

Usage, copy to project folder, pass image extension to convert: `sh desat.sh gif`

Works with animated gifs so useful for removing the sepia tone added to recordings from the [Playdate](https://play.date) simulator.

```bash
#!/bin/bash

find . -name "*.$1" -print0 | while read -d $'\0' file
do
convert -modulate 100,0,100 "$file" "${file%.*}.$1"
done
```

## Switch ssh identities
Pushing to personal and work repos from the same computer, both on Github? You can set this up to be more automatic but I always forget how and it's complicated. This however is simple:

* Add a different cert to each repo
* Add a config file in .ssh: `./.ssh/config`:
```
Host github.com
  AddKeysToAgent yes
  IdentityFile ~/.ssh/id_rsa
```
* Edit the IdentityFile for the repo you want to work with
* Then run `ssh-add -D`
