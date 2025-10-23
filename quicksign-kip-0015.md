---
description: >-
  Additional quicksign endpoint to the kadena-signing-api that allows wallets to
  show the user multiple transactions at once for signature approval.
---

# Quicksign: KIP-0015

[https://github.com/kadena-io/KIPs/blob/jam/quicksign/kip-0015.md](https://github.com/kadena-io/KIPs/blob/jam/quicksign/kip-0015.md)

## QuickSign 'Command':

This API allows to sign multiple transactions at once and ask for a signature approval to the user.

## QuickSign 'Request':

QuickSign request: If you want to do a quick sign, use the `kda_requestQuickSign` request:

```
window.kadena
  .request({
    method: 'kda_requestQuickSign',
    data: {
      networkId: 'mainnet01',
      commandSigDatas: [
        {
          sigs: [/** sigs */],
          cmd: JSON.stringify(cmd),
        },
		{
          sigs: [/** sigs */],
          cmd: JSON.stringify(cmd2),
        }
      ],
    },
  })
```

`commandSigDatas` is an array of CommandSigData objects.\
\
The schema for a `CommandSigData` object is:

```
//{
  "sigs": [Signer],
  "cmd": string
}
```

The "cmd" string represents a json-encoded payload type, specified here: [https://api.chainweb.com/openapi/pact.html#tag/model-payload](https://api.chainweb.com/openapi/pact.html#tag/model-payload)\
\
The Signer schema instead:

```
{
  "pubKey": string,
  "sig": string //optional; its omission represents a signature that has not yet been acquired
}
```

* The `pubKey` field is a lowercase base-16 encoded public key
* The `sig` element is either a lowercase base-16 encoded signature or a null value (representing a request for signature).

## QuickSign 'Response':

In case of a success sign you'll get a success response from eckoWALLET in the quickSigndata array (one element for each requested signing command)

```
{
  status: 'success',
  quickSignData: [
    {
      commandSigData: {
        cmd: '{{ cmdString }}',
        sigs: [
          {
            pubKey: 'publicKey',
            sig: '{{ sig }}',
          },
          {
            pubKey: 'other publicKey',
            sig: null,
          },
        ],
      },
      outcome: {
        hash: '{{ hashString }}',
        result: 'success',
      },
    }
 ]
}
```

The signature will be added in the correct `sig` record that contains the public key of the eckoWALLET account. In case of any error, the response status will be `fail`

```
{
    "status": "fail",
    "error": "QuickSign fail: wallet public key not found"
}
```
