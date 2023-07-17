# zkCompanions

## Description
zkCompanions are NFTs that represent AI #companions modelled on the a16z crypto AI companions app starter. This MVP was completed for the zkSync Buidlera hackathon. 

## Smart Contracts
- The Mint Pass NFT is an instance of BaseCappedRoyaltyNFTFC.sol deployed and verified at: https://goerli.explorer.zksync.io/address/0x2BC96F27618Da97A0113afA8EC1d6d36dA24887F#contract
- The zkCompanions NFT is an instance of BaseCappedRoyaltyNFTFC.sol deployed and verified at: https://goerli.explorer.zksync.io/address/0x389C769883dECa0743fdF63c0CAf40787036b138#contract
-> to see a sample tokenURI, you can click on READ and use 23. tokenURI with tokenId = 1 and hit Query. This returns an Arweave link you can view the current metadata json file for the NFT at, e.g. https://arweave.net/iFqIuQHrFJB8ni8Jwomk-bhDoN9Y5xNySmH8WLlJEbs
- The ZKC token is an instance of MyERC20.sol deployed deployed and verified at: https://goerli.explorer.zksync.io/address/0x4a248ef75c909B990F251a02D8F9eB4E26C329Fa#contract 
- The ERC20Paymaster is an instance of ERC20fixedPaymaster.sol deployed and verified at: https://goerli.explorer.zksync.io/address/0xbbDF698Cc1B86D5AF67Ba674aC3fEa7E668C32c6#contract with the ZKC token address as its parameter
- The ERC721 Paymaster is an instance of ERC721gatedPaymaster.sol deployed and verified at: https://goerli.explorer.zksync.io/address/0x5396C3151F54D907E4743996C499621Bb403A1AE#contract with the Mint Pass NFT address as its parameter

## Using The System
- Users can start by minting a mint pass on Twitter with a tweet by following the instructions at: (To be added)
- Once they have a mint pass NFT they can visit https://zkc.idexo.com/zkcmint and mint their companion. The paymaster checks if they have a mint pass NFT and if they do, pays their gas fee for this transaction. 
- Now that they have their NFT they can start talking to their AI. This is accomplished through back-end calls to a microservice that connects to the ChatGPT API. Values that are stored on their NFT TokenURI are added to the prompt that accomplishes this. 
- When they complete their new chat, they may want to update their chat history on their NFT. They can do this with 5 ZKC - i.e. it calls the ERC20Paymaster and handles the gas for a payment of 5 ZKC. To do this requires creating a new metadata file link for the TokenURI. This is accomplished by passing the old and the new to the https://npmjs.com/idexo-sdk which is handled on the backend API that returns the new TokenURI and the NFT contract method setTokenURI(tokenId, tokenURI) is called through the paymaster. 

