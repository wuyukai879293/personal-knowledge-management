## Homebrew permissions issue
I was able to solve the problem by using chown on the folder:

`sudo chown -R "$USER":admin /usr/local`
Also you'll (most probably) have to do the same on /Library/Caches/Homebrew:

`sudo chown -R "$USER":admin /Library/Caches/Homebrew`
Apparently I had used sudo before in a way that altered my folder permission on /usr/local, from here on forward all installations with brew have proven to be successful.
`brew link libpng`

from [stackoveflow](http://stackoverflow.com/questions/16432071/how-to-fix-homebrew-permissions/16450503#16450503)

This answer comes courtesy of gitHub's homebrew issue tracker 
