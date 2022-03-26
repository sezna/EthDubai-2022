1. Storage
beginning up to contracts in solidity docs

simple solidity contract w/ one state variable and a getter/setter


emphasize indirection for accessing storage variables


abi special behavior: can't call self, must have one arg at most


special functions: we have no block timestamp, no chain id, no difficulty, no tx.origin
add: coin color

we don't need ABI encoding/decoding
we don't have overloading


storage references in library functions and associated storage data in abis 
abi functions dont accept storage pointers because storage is not shared across calls
