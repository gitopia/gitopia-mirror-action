# Gitopia Mirror Action

Github action to mirror your Github repos to Gitopia

Use it as the following gitopia-mirror.yml

```
name: Mirror to Gitopia

on:
  push:
    branches: [master]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v2
      - uses: actions/setup-node@v1
        with:
          node-version: 12
          registry-url: https://registry.npmjs.org/
      - name: Test action
        uses: gitopia/gitopia-mirror-action@master
        with:
          gitopiaWallet: "${{ secrets.GITOPIA_WALLET }}"
          branch: "master"
          remoteUrl: "gitopia://jf9rQRuE_TnKi5stRHbGk8pjtVKQ_0ikFs8tfYyZLMs/gitopia-mirror-action"

```

Add Arweave Wallet contents to github secrets called `GITOPIA_WALLET`

Update values of

- `gitopiaWallet`: Your wallet file saved as a Github secret,
- `branch`: The branch you want to push in Gitopia (optional, default:'master'),
- `remoteUrl`: Your Gitopia repository remote_url created from https://gitopia.org
