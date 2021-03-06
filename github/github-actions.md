# GitHub Actions

간략한 소개: <https://github.com/features/actions>

공식 문서: <https://help.github.com/actions>

저장소: <https://github.com/actions>

Github Actions 오픈소스 목록: <https://github-actions.netlify.com/>

## Articles

- [GitHub Actions now supports CI/CD, free for public repositories](https://github.blog/2019-08-08-github-actions-now-supports-ci-cd/)
- [GitHub Actions: First impressions — Martian Chronicles, Evil Martians’ team blog](https://evilmartians.com/chronicles/github-actions-first-impressions)
- [Guide to a custom CI/CD with GitHub Actions - ITNEXT](https://itnext.io/https-medium-com-marekermk-guide-to-a-custom-ci-cd-with-github-actions-5aa0ff07a656)
- [Trying GitHub Actions | Better world by better software](https://glebbahmutov.com/blog/trying-github-actions/)
- [How to use GitHub Actions in GitKraken](https://support.gitkraken.com/git-workflows-and-extensions/github-actions/)
- [An Unintentionally Comprehensive Introduction to GitHub Actions CI - DEV Community 👩‍💻👨‍💻](https://dev.to/bnb/an-unintentionally-comprehensive-introduction-to-github-actions-ci-blm)

## CI/CD

```yaml
name: CI
on: [push, pull_request]
jobs:
  build:
    runs-on: ubuntu-18.04
    strategy:
      matrix:
        node-version: [12.x]
    steps:
      - name: Checkout
        uses: actions/checkout@v1
      - name: Install dependencies
        run: npm ci
      - name: Lint
        run: npx eslint .
      - name: Run tests
        run: npm test
      - name: Build
        run: npm run build
      - name: Deploy
        if: github.ref == 'refs/heads/master'
        uses: JamesIves/github-pages-deploy-action@releases/v3
        with:
          ACCESS_TOKEN: ${{ secrets.ACCESS_TOKEN }}
          BASE_BRANCH: master
          BRANCH: gh-pages
          FOLDER: dist
```

예제: <https://github.com/microprotect/microprotect.com/blob/master/.github/workflows/ci.yml>
