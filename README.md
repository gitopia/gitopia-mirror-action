# Gitopia Mirror Action

[![Gitopia](https://img.shields.io/endpoint?style=&url=https://gitopia.org/mirror-badge.json)](https://gitopia.org/#/address/gitopia)

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
        with:
          fetch-depth: 0
      - uses: actions/setup-node@v1
        with:
          node-version: 12
          registry-url: https://registry.npmjs.org/
      - name: Test action
        uses: gitopia/gitopia-mirror-action@v0.1.1
        with:
          gitopiaWallet: "${{ secrets.GITOPIA_WALLET }}"
          branch: "master"
          remoteUrl: "gitopia://z_TqsbmVJOKzpuQH4YrYXv_Q0DrkwDwc0UqapRrE0Do/gitopia-mirror-action"

```

Add Arweave Wallet contents to github secrets called `GITOPIA_WALLET`

Update values of

- `gitopiaWallet`: Your wallet file saved as a Github secret,
- `branch`: The branch you want to push in Gitopia (optional, default:'master'),
- `remoteUrl`: Your Gitopia repository remote_url created from https://gitopia.org
