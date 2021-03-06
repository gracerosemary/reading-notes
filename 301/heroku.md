[Getting Started on Heroku with Node.js](https://devcenter.heroku.com/articles/getting-started-with-nodejs)

1. Created Heroku account
2. Install for Windows instead of Ubuntu (ubuntu install error: "Interacting with snapd is not yet supported on Windows Subsystem for Linux.")
3. Went back to pre-work setup instructions to make sure Heroku was downloaded since it didn't appear when I called for the version (sudo curl [https://cli-assets.heroku.com/install.sh](https://cli-assets.heroku.com/install.sh) | sh)
4. Successfully logged into heroku within Ubuntu 
5. Clone local version of sample application

```bash
$ git clone https://github.com/heroku/node-js-getting-started.git
$ cd node-js-getting-started
```

6. Create an app on Heroku → prepares Heroku to receive source code → git remote (Heroku) is created and associated with your local git repository

```bash
$ heroku create (youCanEnterCustomName)
```

7. Deploy your code

```bash
$ git push heroku main
```

8. Ensure at least one instance of the app is running

```bash
$ heroku ps:scale web=1
```

9. Visit the app at the URL generated by its app name

```bash
$ heroku open
```

^ran into issues → set a default browser (set to Chrome) → [https://github.com/microsoft/WSL/issues/2413](https://github.com/microsoft/WSL/issues/2413)

```bash
$ export BROWSER=/mnt/c/Program\ Files\ \(x86\)/Google/Chrome/Application/chrome.exe
```

^fixed issue and was able to open URL

10. View logs - streams of time-ordered events aggregated from the output streams of all your app and Heroku components, providing a single channel for all of the events (Press Control+C to stop streaming the logs)

```bash
$ heroku logs --tail
```

## Bookmark

[Node.js For Beginners. Deploy Your Blog to Heroku](https://howtonode.org/deploy-blog-to-heroku)