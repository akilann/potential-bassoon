# Enabling SSO/SAML for GitHub.com

These notes are my best memory of how I got it to work (on March 27, 2018). Your mileage very well may vary.

## MAC

1. Nav here: https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/
1. Follow the instructions in this sub section: "Creating a token", steps 1 - 9 (that is, not step 10 (although a detailed review of that might be a big help, who knows?))
1. In my case, I deleted a bunch of old tokens, too, btw, before creating the new one
1. COPY SAVE DOCUMENT BE EXTRA SURE TO SAVE THAT NEW TOKEN SOMEWHERE GOOD
1. ALSO - leave this browser open and logged in to your GitHub.com profile
1. Nav here: https://help.github.com/articles/updating-credentials-from-the-osx-keychain/
1. Follow the instructions as best you can
1. In my case,
    - it was in the "login" keychain
    - I found multiple entries for github.com. The trick was finding the one that indicated `internet password` in the "Kind" column
1. double click it
1. check the "Show password:" box (on the "Attributes" panel)
1. delete my password (after making sure it looks familiar and such)
1. paste in the token that you saved
1. click "Save Changes" (you can kill the KeychainAccess app now if you like)
1. nav to a terminal window and attempt to access github.com via command line (clone, pull, etc)
1. pay extra attention to the spew of a crazy error message
1. inside there somewhere is a big long URL link, copy it
1. in a new browser tab, in the same window as above, paste the link from above error message and nav there
1. follow those instructions, click click click, SSO stuff
1. go back to your terminal window and try again
1. in my case, it worked at that point
1. GOOD LUCK

## WIN

1. Use the same token as above (if you don't have one, see the top steps above)
1. make sure your git for windows and git bash are updated and modern versions and such
1. open a `git bash` terminal window
1. type `cd ~` to nav to your "home" directory
1. manually update or create a file called `.git-credentials` somehow or other in that same directory (your "home" directory)
    - mine looks like `/c/Users/220038648` in bash and `C:\Users\220038648` in windows command prompt (in case you need that info to create the file)
1. the content should be `https://<your github username>:<your access token>@github.com`
    - mine looks like: `https://mssonger:abadcafe1234567890bingo42notreally@github.com`
1. in the same `git bash` window, type `git config --global credential.helper 'store'`
    - note the single quotes around 'store'
1. now try some sort of github.com command line access (clone, pull, etc)
1. hopefully you will get a prompt for user name
1. type in your GitHub.com user name (NOT your SSO)
1. Next you need to type in your token that you just created (way above)
    - in my case, I had to search and search behind all sorts of other windows for a tiny pop up dialog box. Once you find that, paste in your token and continue
1. go back to your terminal window and try again
1. in my case, it worked at that point
1. GOOD LUCK

## Linux

Beels says:
```
Chris Beeler [2:00 PM]
I just did `nano ~/.git-credentials` and took my password out and put my PAT in, no problems yet
```

## Eclipse

Paul says:

![Secure Storage dialog](https://github.com/mssonger/potential-bassoon/blob/master/images/eclipseSecureStorage.png "Secure Storage dialog")

Delete secure storage entries for GitHub, then re-enter when you pull, clone, etc.
