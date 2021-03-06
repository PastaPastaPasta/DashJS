## Using a different account 

Because the SDK uses mostly a mnemonic to initialize itself, you can access to the other account defined by the [BIP44](https://github.com/bitcoin/bips/blob/master/bip-0044.mediawiki).

As an helper for users and internal reference for `sdk.platform`. 
By default, accessing to `sdk.account` is equivalent of `sdk.wallet.getAccount({index:0})`. 
Therefore usage might varies if you need to deal with platform or not. 


### Access to account without platform
```js  
   const accountIndex = 1;
   const account = sdk.wallet.getAccount({index:accountIndex});
   await account.isReady();
```

### Access to account with platform.

You will actually need to replace `sdk.account` to get platform to correctly fetch the right account to use for signing and fetching UTXOs.

```js
async function changeAccount(){
   sdk.account = sdk.wallet.getAccount({index:1});
   await sdk.account.isReady();
}
```
