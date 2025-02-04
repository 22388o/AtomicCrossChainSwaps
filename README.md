# CrossAtomicChainSwaps with Solidity

Experimental implementation of several different cross chain atomic swaps

workshop slides can be found at: 
https://docs.google.com/presentation/d/1v2pJ5A90hEDm7kPlvFesA6z0LAYHrx0cUSVHkJMBBhM/edit?usp=sharing

HTLC Hash TimeLock Contracts:
- 01. Alice HTLC on Chain 1
  (simple contract creation with parameters, like : 0x14723a09acff6d2a60dcdf7aa4aff308fddc160c, "0x558FA4A7D00B6EC794475955E49AE6C4732A2E7F6EC4C251718C68CA68619338", 1 )
- 02. Bob HTLC on Chain 2
- 03. Simplified HTLC in ethereum
- 04. ERC 1630 Ethereum proposal for standard HTLC:  https://github.com/ethereum/EIPs/issues/1631
- 05. Asset transfer contract on chain 2 transferring the ownership of Bob's house
- 06. Time patched solidity contracts for demo

Simple atomic swap protocol with HTLC for money transfer
1. Alice creates hash and digest and agrees in expiration time with Bob
2. Alice deploys AliceHTLC_Chain1 contract on chain 1 and transfers money to the contract (meaning that the money has been conditionally transferred to Bob)
3. Bob deploys BobHTLC_Chain2 on chain 2 and transfers money to the contract (meaning that the money has been conditionally transferred to Alice)
4. Alice claims her money from Bob on chain 2 unveiling the secret by calling the BobHTLC_Chain2 contract. 
5. Bob see the secret key, so he can claim his money from Alice on chain 1 by calling the claim function of the AliceHTLC_Chain1 contract with the secret. 
 
Creating test scenario like with the following parameters: 
AliceHTLC_Chain1: 0x14723a09acff6d2a60dcdf7aa4aff308fddc160c, "0x558FA4A7D00B6EC794475955E49AE6C4732A2E7F6EC4C251718C68CA68619338", 1
BobHTLC_Chain2: 0xca35b7d915458ef540ade6068dfe2f44e8fa733c, "0x558FA4A7D00B6EC794475955E49AE6C4732A2E7F6EC4C251718C68CA68619338", 1

Simple atomic swap protocol with HTLC for asset exchange
1. Alice creates hash and digest and agrees in expiration time with Bob
2. Alice deploys AliceHTLC_Chain1 contract on chain 1 and transfers money to the contract (meaning that the money has been conditionally transferred to Bob)
3. Bob deploys BobHouse_Chain2 on chain 2 and initiates the house transfer by calling the initializeHouseTransfer function that conditionally transfers the house to Alice
4. Alice claims the house from Bob on chain 2 unveiling the secret by calling the BobHouse_Chain2 contract. 
5. Bob see the secret key, so he can claim his money from Alice on chain 1 by calling the claim function of the AliceHTLC_Chain1 contract with the secret. 

Simple multihop payment routing
1. Alice creates hash and digest and agrees in expiration time with Bob
2. Alice deploys AliceHTLC_Chain1 contract on chain 1 and transfers money to the contract (meaning that the money has been conditionally transferred to Bob)
3. Bob deploys BobHTLC_Chain2 on chain 2 and transfers money to the contract (meaning that the money has been conditionally transferred to Charlie)
4. Alice reveals the secret to Charlie
5. Charlie claims her money from Bob on chain 2 unveiling the secret by calling the BobHTLC_Chain2 contract. 
5. Bob see the secret key, so he can claim his money from Alice on chain 1 by calling the claim function of the AliceHTLC_Chain1 contract with the secret. 




