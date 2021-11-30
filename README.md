# Randomized SNIP-721 Mint Impl
This contract is a reference implementation using [Baedriks SNIP-721 impl](https://github.com/baedrik/snip721-reference-impl) as a framework, optimized for randomly minting SNIP-721s in to buyers using SNIP-20 tokens as payment.

Fields that you will want to edit for your particular launch include:

`MINT_COST` u128 in `contract.rs`. It is written in the lowest denomination of your SNIP-20 token of choice. The Address and Hash of the SNIP contract must be included in the init msg.

`PreLoad` struct in `state.rs`. It defines the datatypes of the public and private data you will want to store when using the `pre_load()` function to load the tokens into the contract. 

`mint()` in `contract.rs` list the components of the public and private metadata as `None`. Change the components you want to fill with the `PreLoad` data to read `Some(token_data.<INSERT_PRE_LOAD_COMPONENT_NAME>)`

New functions to understand:

`pre_load()` is used to store a `Vec<PreLoad>` for the token data used when minting. Each `PreLoad` in the Vec is the data for a single token.

`receive()` is used when minting. Rather than calling the `mint()` function itself, users will interact with the SNIP-20 contract which will send tokens to the SNIP-721 contract along with address of the person paying.




