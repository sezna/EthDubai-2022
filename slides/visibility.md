### Visibility

----
1. External
1. Public
1. Internal
1. Private

Note: Solidity has four visibility modes.
External functions are part of the contract interface, which means they can be called from other contracts and via transactions.

Public functions are part of the contract interface and can be either called internally or via messages. For public state variables, an automatic getter function (see below) is generated.

Those functions and state variables can only be accessed internally (i.e. from within the current contract or contracts deriving from it), without using this. This is the default visibility level for state variables.

Private functions and state variables are only visible for the contract they are defined in and not in derived contracts.

We have handled this differently.

----

1. External: in an abi block
1. Public: A library function that can be called from an ABI block.
1. ~~Internal~~
1. ~~Private~~

Note: 
We found it unnecessary to draw these divides and went for a more intuitive approach. If you want shared behavior, just put it in a library. Internal and private are not relevant as we don't follow the same inheritence model.
