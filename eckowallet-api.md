---
description: >-
  Welcome to eckoWALLET’s Developer Documentation. eckoWALLET is a user-friendly
  and robust Kadena-native wallet designed for seamless interaction with dApps
  on the Kadena network.
---

# eckoWALLET API

#### \`Detecting eckoWALLET

To verify if the browser is running eckoWALLET use `window.kadena:`

```
/**
       * Check if is X-Wallet installed
       */
       const isXWalletInstalled = () => {
        const { kadena } = window;
        return Boolean(kadena && kadena.isKadena);
      };
 
      const initialize = async () => {
        if (isXWalletInstalled()) {
        // You will start here
        }
      };
      window.addEventListener('load', initialize);
```

#### Connecting to eckoWALLET

Connecting to eckoWALLET effectively means to access the user's Kadena account(s).

```
kadena.request({
  method: 'kda_connect',
  networkId: NETWORK_ID,
});
```

With this code, a pending promise for `kadena.request()` was created. `NETWORKID` could be `mainnet01` or `testnet04` for example.

#### Check Connection status

To check the connection status you can send a `kda_checkStatus` request:

```
kadena.request({
  method: 'kda_checkStatus',
  networkId: NETWORKID,
});
```

If the selected account on eckoWALLET is connected with current DAPP, the response will be

```
{
    "result": {
      "status": "success",
      "message": "Connected successfully",
      "account": {
        "account":
       "k:2e6a4789e51156cf6hf1c377bc8157fcds6d20698b83f30ad2f1828a8b74940e",
        "publicKey":
 "2e6a4789e51156cf6hf1c377bc8157fcds6d20698b83f30ad2f1828a8b74940e"
      }
    },
    "target": "kda.dapps",
    "action": "res_checkStatus"
  }
```

If not, the response will be:

```
 {
    "result": {
      "status": "fail",
      "message": "Not connected"
    },
    "target": "kda.dapps",
    "action": "res_checkStatus"
  }

```

#### Get network info

To get eckoWALLET network info you can use kadena.request function with kda\_getNetwork method.

```
kadena.request({
  method: 'kda_getNetwork',
});
```

You will receive the network info from eckoWALLET:

```
{
    "explorer": "https://explorer.chainweb.com/mainnet",
    "id": "0",
    "isDefault": true,
    "name": "Mainnet",
    "networkId": "mainnet01",
    "url": "https://api.chainweb.com"
  }

```

#### Get account information

To retrieve the current account data from eckoWALLET just send a request with `kda_requestAccount` method.

```
kadena.request({
  method: 'kda_requestAccount',
  networkId,
});
```

You will receive a response like this:

```
 {
    "status": "success",
    "message": "Get account information successfully",
    "wallet": {
      "account": 
        "k:2e6a4789e51156cf6hf1c377bc8157fcds6d20698b83f30ad2f1828a8b74940e",
      "publicKey": 
         "2e6a4789e51156cf6hf1c377bc8157fcds6d20698b83f30ad2f1828a8b74940e",
      "connectedSites": [
        "swap.kaddex.com"
      ],
      "balance": 10.431761673543
    }
  }
```

#### Disconnect from eckoWALLET

If you want to disconnect your DAPP from eckoWALLET, simply send a disconnect request

```
kadena.request({
        method: 'kda_disconnect',
        networkId: 'mainnet01 ',
 
      });

```

#### Send Tokens to another account

Example request If users want to send Kadena tokens to another account

```
         kadena.request({
      method: 'kda_sendKadena',
      data: {
            networkId: 'mainnet01',
            account: '{{ accountName }}',
            sourceChainId: '0',
            chainId: '2',
            amount: 10.23,
            },
      });
```

#### Sign command

If you want to sign custom command, you have to use `kda_requestSign` request method.

```
kadena.request({
        method: 'kda_requestSign',
        data: {
          networkId,
          signingCmd,
        },
      });

```

(eckoWALLET will open a confirmation window for the user).

#### EckoWALLET events

This sections details the events emitted via that eckoWALLET API. There are many events triggered by eckoWALLET, you can listen for events such as the above ones:

#### Account changed

Triggered when user switches account

```
kadena.on('res_accountChange', (event) => {
        console.log(event);
      });

```

The `res_accountChange` event payload is

```
{
     result: { status: "success", message: "Account changed" },
     target: "kda.dapps",
     action: "res_accountChange",
 };

```

#### Status changed

Triggered on `kda_checkStatus` event dispatch

```
kadena.on('res_checkStatus', (event) => {
        console.log(event);
      });

```
