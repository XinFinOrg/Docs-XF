**Technicalities and Specifications of XinFin Delegated Proof of Stake**

Delegated Proof of Stake (DPOS) is the fastest, most efficient, decentralized, and flexible consensus model available. DPOS leverages the power of stakeholder to resolve consensus issues in a fair and democratic way. The Self KYC feature added in XinFin DPoS is more enterprise and regulator friendly.

**Definitions**

DPoS: Delegated Proof of Stake: a mechanism for the selection of network Validators by coin holders delegating their votes Validator: (usually denoted L) a node on the network responsible for producing and validating blocks. Nominator: a coin holder who stakes and delegates their coins to one or more Validators. Epoch: (usually denoted 𝑁) corresponds to 𝐿∈ℕ blocks: it is a cycle of a few blocks in which Validators create blocks in turn.

# **Validators Registration**

Any network participant will be able to register as a Validator.

>A specified value REGISTRATION_VALUE (in the native token) will be sent to a registerfunction on the contract. It will be burnt in order to limit the number of participants.
>The validator is required to add KYC document at the time of staking XDC token.
>A hard limit to the total number of registered Validators MAX_REGISTERED_VALIDATORSshould be specified.
>Any Validator registering will have to wait for the beginning of epoch N+2(current epoch being N) to be eligible.
>A Validator’s total stake must be greater than the MIN_TOTAL_STAKE in order for it to be eligible.
>The top validators(by a total stake) in a given epoch are chosen as the Active Validator Set: those Validators that produce blocks in the next epoch.

**KYC Compliance:**

We would like to add Know your customer (KYC) identification as it falls under the responsibility of financial institution and/or regulated company. Validator needs to upload self KYC document and this document will be visible on the open public network.

# **Choosing Validators**

choose L Validators for a certain epoch N

# **Fork Perversion, Malicious or Double Spends:**

To prevent fork, we add a feature to revalidate transaction. Every transaction will have 2 signatures. One signature will be by block creator and the other signature will be by block verifier (both separate validator). So the block verifier will check for malicious or double spends etc.

# **Slashing**

In order for the network to be secure, misbehaviours must be detected and punished.

1. Off-chain: Off-chain detection of misbehaviour is easier to implement and can be used for tricky misbehaviour detections.
In the contract, there will be a reportBenign method (part of the Validator Set Contract) that only Validators can call, passing a message and a block-number, and a slashing will execute if more than 2/3 of the Validators agree on the misbehaviour.
These might include but are not limited to: Validators consistently propagating blocks late __ Validators being offline for more than 24 hours.
It could slash a portion of the stakes, eg. only 4%

2. On-chain: A slashing condition that can be verified on-chain is that a Validator signed-off 2 blocks with the same step (equivocation). Anyone could call this reportMalicious method with the right data, being the two signatures of the Validator, and the message signed, which would contain the step of the blocks. This method would thus include an RLP decoder.
We could also detect if a Validator hasn’t signed any block for the past 256 blocks on-chain, by challenging the Validator to submit the block he signed along with the signature. However, only the last 256 block hashes are available in the EVM, so it might be limited in this context of around 1,000-blocks epochs.
There may be other on-chain slashable conditions.

3. Wrong KYC Detail Enter by Validator Node: In the contract, there will be a reportMalicious method that only Validators can call, passing a message and a block-number, and a slashing will execute if more than 2/3 of the Validators agree on the reportMalicious. It could slash a portion of the entire 100% stakes of Validator Node.


# **Parameters**

Suggested parameter values from requirements: 

MIN_STAKE: 10,000,000

XDC VALIDATOR_REWARD: 0.01370% (Daily) 

VALIDATOR_SET_SIZE:  

REWARDS_TRANSFER: Every next block of an epoch 

WITHDRAWAL_PERIOD: Set of Epoch ( 1 Epoch = 900 blocks) 

MAX_REGISTERED_VALIDATORS: 5000

# **Upgradability:**

Contracts should be upgradeable, could be implemented with Proxy contracts.

Contract state would need to be transferred to the new version of the contract, either through a migration process or a persistent storage pattern.

