# Serve on Github

**package.json**
```json
{
  ...
  "homepage": "https://de314.github.io/ac-notes",
  "scripts": {
    ...
    "predeploy": "npm run build",
    "deploy": "gh-pages -d build"
  }
}
```

```shell
npm i  -D gh-pages
npm run deploy
```

## Resources

- https://medium.com/the-andela-way/how-to-deploy-your-react-application-to-github-pages-in-less-than-5-minutes-8c5f665a2d2a
- https://www.npmjs.com/package/gh-pages
- https://gauger.io/fonticon/
