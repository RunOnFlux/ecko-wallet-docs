# FAQ

### How do I install eckoWALLET?

Go to [https://eckowallet.com](https://eckowallet.com) or you can also go directly to the Chrome store, Google Play store, and Apple App Store (soon).

### How do I create a new wallet?

Three main steps; (1) set password, (2) record recovery phrase and (3) verify recovery phrase.:

* Set password: Create a strong, secret, and unique password. See the Basic Safety Tips section for suggestions on password generation.
* Save/Download recovery phrase: Download and safely guard your 12 word recovery phrase.
* Verify recovery phrase: Enter each word in the correct order to verify that you have correctly recorded your recovery phrase.

### How to restore existing wallet from recovery phrase?

Three main steps; (1) enter recovery phrase, (2) set new password, (3) re-generate keys:

* Select restore from secret recovery phrase.
* Enter recovery phrase: Enter your 12-word recovery phrase, with a space between. To do this, copy and paste your recovery phrase on a text editor, and then copy into the input field. Extension won’t allow users to enter spaces manually, use any text editor, and paste onto eckoWALLET extension.
* Set new password: Input a new password for your existing wallet.
* Re-generate keys: From the Account Name section, select the Create Wallet button to restore keys. These keys are deterministically generated meaning that the same keys will always appear in the same order by using the recovery phrase as a master seed. Repeat selecting the Create wallet button until all necessary keys are restored.

### How do I transfer my existing KDA network tokens to eckoWALLET?

You can send KDA and KDA tokens from another wallet to a new eckoWALLET account. Simply copy your new eckoWALLET public address and go to your existing wallet or exchange to send funds to your new wallet address.

You can find your eckoWALLET address under account name (in the format a81a50f711….6ab50).

### How do I send KDA and other network tokens?

Open the extension, and from the home screen, click Send. Enter destination account information, chain ID, preview your transaction and send.

### How to deposit / receive / send?

On the extension app, to send or receive KDA, use the home screen button “Send or Receive ''. To send or receive with other tokens, first select a token from the home screen then click Send or Receive.

### Which tokens does eckoWALLET support?

KDA and any KDA based tokens. You may need to manually list some tokens to see them within eckoWALLET.

### What is my public address?

A Kadena address is a unique identifier that serves as a virtual location for your KDA and KDA-based tokens. Think of it like your bank account number.

### What are Kadena accounts composed of?

1. Account Name
2. Keys
3. Predicate

### What is my account name?

In simple terms, “account name” refers to your unique name on the blockchain, and “keys” refers to the public/private keypairs that grant access to your account. In other words, it is the keys that determine ownership of an account.

With most blockchains, accounts are modelled as simply public/private keypairs (ie. your account name is the same as your public key). This “one-to-one” model keeps things simple, but runs into problems when you want to use multiple keys for a single account, such as with jointly-owned or majority-ruled accounts. Kadena natively supports multiple keys governing the same account name, and thus the distinction between “keys” and “account name” becomes important.

### What are Keys & Predicates?

“Predicate” is something that determines how many signatures are required to transfer coins from the account. The three built-in predicate options are `keys-all`, `keys-any`, and `keys-2`. Most KDA holders will never see, or even know about, their account’s predicate because they will have a traditional single-key account wherein keys-all and keys-any do the same thing.

However, the predicate becomes more important with multi-signature accounts. For example, the `keys-2` predicate requires that at least 2 keys in the account must sign in order to authorize a transaction.

For more info, check out: [https://medium.com/kadena-io/beginners-guide-to-kadena-accounts-keysets-fb7f32104291](https://medium.com/kadena-io/beginners-guide-to-kadena-accounts-keysets-fb7f32104291)

### Who can access your account?

Anyone with your wallet's password, private keys or recovery phrase can access your account. Passwords, private keys, and recovery phrases are in the users’ hands and are the users’ responsibility. eckoWALLET is simply an interface that allows you to more easily interact with your accounts and the Kadena blockchain.

### Questions not answered - How do I contact support?

Tweet us @eckoWALLET, or use our discord [https://discord.com/invite/QSJpHRFDcv](https://discord.com/invite/QSJpHRFDcv).
