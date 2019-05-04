# CrossChainSwaps

Experimental implementation of several different cross chain swaps

HTLC Hash TimeLock Contracts:
- ERC 1630 Ethereum proposal for standard HTLC:  https://github.com/ethereum/EIPs/issues/1631
- Simplified HTLC in ethereum

Atomic swap protocol with HTLC
1. Alice creates hash and digest and agrees in expiration time
2. Both HTLCs are deployed on both chains
3. Cryptocurrency is transferred to the contracts
4. Alice reveals secret by unlocking the other contract and getting the fund
5. Bob see the secret on the chain as it is public, so he can also unlock the contract and get the fund
 


