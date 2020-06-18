# Multisig Deposit Vault 
# for Decentralized Digital Asset Tokenization
*Design proposal*

## What it is
Multisig Deposit Vault is needed to allow decentralized automated tokenization - exchanging of crypto coins to their equivalent tokenized by Lyra, which then can be used for processing real time payments and trading. For example, a user wants to exchange GRFT to BTC. The user sends an amount of GRFT to the address of the multisig wallet provided by the current authorization sample. Once transfer is done, the sample issues an equivalent amount of Lyra GRAFT tokens which can securely reside and instantly circulate inside the Lyra network. (The transfer from GRAFT wallet to the multisig wallet can be done via RTA transaction, which makes the entire issuing process instant.) Then Lyra GRAFT tokens can be instantly traded to Lyra BTC tokens, and the user can either keep those tokens or convert them to BTC (using similar multisig BTC wallet).   
## Solution
Lyra decentralized network is based on DPoS with a limited and fixed number of authorizer nodes, carefully selected by voting process, which provides some degree of trust necessary and significant enough to secure the network. This feature allows using multi signature wallet functionality, which is present in many cryptocurrencies, to implement decentralized multisig deposit vaults that store the balances of cryptocurrencies that are being exchanged to Lyra equivalents. 
## How it works
Authorizers create a multisig “M-of-N” wallet for crypto deposit, where at least M authorizers are required to process a transaction with a vault. Each authorizer holds only one key. It means that 1) at least M authorizers must be responsive at the time of transaction, and 2) the system can tolerate N-M irresponsible authorizers (for example, losing or compromising their keys, trying to sabotage the network, or simply going offline). The system also can tolerate up to M-1 dishonest authorizers attempting to attack and compromise the system.

For a “10-of-15” wallet, 10 keys (authorizers) are required to sign the multisig transaction. It means at least 10 authorizers must be responsive and responsible in order to maintain the vault, meaning being able to process crypto payouts and transfer a vault funds when the sample is changing).     

## Issues 

### Security Risks
When the funds are transferred between the old and new sample wallets, there is a risk of not getting a quorum to process the transfer transaction. Therefore, the sample change should be limited to only one authorizer at the time (one leave one enters). In this case, the old wallet will be temporarily degraded to “10-of-14” (the outgoing authorizer does not participate in the transaction). However, all 15 authorizers from the new sample must be present in order to form a new wallet properly (the incoming and all the remaining authorizers must participate). If any authorizer is not responsive, it must be replaced by the next candidate in the queue (and the transition will be delayed).

Another risk is losing assets if N authorizers are rogue or lost.   

Possible risk mitigation - collateral in different vault (based on similar technology).

### Fees

When the authorization sample is changing based on the voting results, it means at least one authorizer leaves the sample, and a new authorizer enters instead. The vault funds must be transferred from the current sample’s wallet to the upcoming sample’s wallet. This transaction has an associated transfer fee which must be covered by the current wallet. 

There are at least two options to resolve this issue:
The fee will be covered by a new member of the authorization sample as a condition to enter the sample. The newly elected authorizer is motivated to enter the sample because of potential income in the form of Tx fees, and therefore it should not be an issue to require a “membership payment”.    
The fee will be covered by the fees collected from withdrawals (crypto payouts). When a user wants to withdraw (exchange the Lyra deposit tokens back to a real world crypto), the withdrawal fee should exceed the associated network fee. The difference accumulated on the vault account can be used to pay dividends to the authorizers as well as cover the costs of maintenance transfers between the samples. 
