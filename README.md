# dgit-action

Github action to mirror your Github repos to Dgit

Use it as the following mirror.yml

```
name: Dgit Mirror

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
      - name: Dgit mirror action
        uses: thetechtrap/dgit-action@master
        # The action should not publish any real changes, but should succeed.
        with:
          dgitWallet: "${{ secrets.DGIT_WALLET }}"
          branch: "master"
          remoteUrl: "dgit://7yFP2o906A3nDl5eCMtN4Ycs9m5otfRrJDAGoGKDoHk/dgit-action"

```

Add Arweave Wallet contents to a wallet and add it in secrets

Update values of
`dgitWallet` - your wallet file pointing to the secret containg your wallet,
`branch` - the branch to dgit your want to push,
`remoteUrl` - your repository remote url created from https://dgit.sh
