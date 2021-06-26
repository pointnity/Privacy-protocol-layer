# Privacy-protocol-layer
This is the operational category of PointNity Network-related cross-chain privacy agreement, which contains detailed descriptions, which is the main work!
# Pointnity Network
> [Pointnity.network](https://www.pointnity.online/)
## Project Overview
Pointnity Network protects payment anonymity and confidentiality on the blockchain. It will be composed of a front-end client and a back-end smart contract algorithm. They act as an institution with proven security and privacy by using a complete encryption protocol.

Pointnity Network will apply [Zether Framework] (https://eprint.iacr.org/2019/191) to build a second-layer decentralized anonymous payment module. Then import it as a substrate-based smart contract. Similar to the Zether framework, it will have three technical modules: mint, transfer and redemption. The mint module converts the basic token to its anonymous version, and the redeem module converts the anonymous token back to its original form. The transmission module is a module that realizes the anonymous transmission of anonymous tokens. This process will hide the transaction amount and guarantee the anonymity of the sender and receiver.

## Project structure
The minting module will create a Pointnity account by running the minting contract and deposit anonymous tokens into the Pointnity account. Each Pointnity account is identified by a public key "pk", and the minting module will generate a ciphertext under the account public key, which encrypts the number of minted coins. If the account already exists before the coinage operation, the generated ciphertext will be homomorphically added to the existing ciphertext to increase the amount of encryption.

Since the balance and transaction amount of each Pointnity account are encrypted and therefore hidden, the remaining problem of the transfer module is how to hide the identities of the relevant parties. Similar to the anonymous transfer module of the Zether solution, we hide the identities of the participants through the "multiple choice" proof. The "one-to-many" proof is conceptually close to a ring signature. It proves that the transaction is initiated by one of the multiple parties in the anonymity set (or ring) without revealing who is the sender or the recipient of the transaction, thereby hiding theirs Identity. The zkp of the transfer module will also prove the consistency of the payment and provide a proof of scope to prove that the transaction does not involve a negative amount, which may allow the opponent to create money out of thin air.

The redemption module converts the anonymous token back to its original form. The exchange module also needs to call the zero-knowledge proof function to prove that the user who initiated the exchange module knows the secret key of the corresponding Raze account and the exchange amount is less than the balance of the Pointnity account.

In summary, Pointnity uses public key homomorphic encryption to ensure the confidentiality of transaction details, and uses "one-to-many" proof to hide the identity of the sender and receiver. Some other zero-knowledge proof schemes are also used to guarantee payment. Consistency. Whenever a user deposits a certain amount of tokens by calling the mint module, the tokens are no longer traceable.
