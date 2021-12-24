# fvn
Federation Verification Node - a proposal for a verification standard for federated networks that use public proof-of-authorship

## Rough protocol outline

* Users create a new keypair that will be used to sign all content (call this Pubkey2/Privkey2)
* User signs new keypair using an existing wallet (i.e. WalletConnect to sign with an Ethereum keypair, Pubkey1/Privkey1)
* Every time a user posts a message, Pubkey1, Pubkey2, the Privkey1-signed Pubkey2 & the Privkey2-signed message are published
* This way users can sign each message without needing the main identity wallet to be involved (Metamask, walletconnect etc.) except for the first step

## Challenges

1. To avoid users from sending messages with spoofed timestamps, measures need to be taken
    * One option is to create a pseudo-blockchain for each federation i.e. Each service provider also signs each message and creates an append-only hash-chain
2. Validating nodes would need to sync entire history from a particular node they are interested in. Checkpoints are possible but consensus can be difficult
3. A global identity service is necessary for achieving single-sign-on across federated nodes.
    * ENS is an ideal contender for this since usernames are already globally unique and provable using wallets. Without ENS or similar, identities will have to be wallet addresses, which are not human-readable. Non-human-readable addresses put the responsibility of assigning usernames to federated nodes which can lead to clashes very quickly. This can potentially be avoided if each username also has a DNS name attached much like e-mail.

## Next steps

I will publish more details & code here in this repository soon
