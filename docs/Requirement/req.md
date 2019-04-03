
##**On-Chain Governance for XinFin DPOS**

#**Overview**
Built-in Public governance mechanism where any changes in network (update_proposal) will get approved by 2/3 of register_validator (Master-node holder) by voting_system to incorporate those changes in network.

#**Product Perspective**
On-chain governance (by calling proxy contract ?), a formalized way in which a group of people can make changes by voting through the protocol,The purpose behind it is to provide a clear-cut path to consensus. 


* update_proposal: Any entity that register as  masternode is able to vote on update_proposal with proposed vote_period
* vote_type: Identity-based 1-register_validator (Masternode) = 1-vote
* vote_period: between 15-90 days
* vote_condition: more then 1/10 register_validator should participate to vote otherwise update_proposal should be void.


#**How it Works?**
On-chain governance systems solely work online. Changes to a blockchain are proposed through code updates. Subsequently, nodes can vote to accept or decline the change. all nodes have equal voting power.  If the change is accepted by ⅔ validator_node, it is included in the blockchain and baselined. In some instances of on-chain governance implementation, the updated code may be rolled back to its version before a baseline, if the proposed change is unsuccessful.


#**Pre-defined Update:**

* Update the block time
* Update with vote_period
* Update with vote_type
* Update with vote_condition
* Update the WITHDRAWAL_PERIOD 
* Update with MAX_REGISTERED_VALIDATORS 
* Reduce VALIDATOR_REWARD
* Update with REWARDS_TRANSFER period
* Update/Upgrade Smart contract address
* Update MIN_STAKE
* Update WITHDRAWAL_PERIOD 
* Update function reportMalicious 
* Time Based limitation to add any changes in network
* Changes in the existing protocol and parameters of a blockchain.
* Retroactively make changes to the state of the blockchain.
* Distribution of subsidies when relevant.
* Update Hard Coded value:

    -HashLength

    -AddressLength

    -MasternodeVotingSMC

    -BlockSigners

    -RandomizeSMC

    -FoudationAddr

    -TeamAddr

    -VoteMethod

    -UnvoteMethod

    -ProposeMethod

    -ResignMethod

    -SignMethod

    -RewardMasterPercent

    -RewardVoterPercent

    -RewardFoundationPercent

    -HexSignMethod

    -HexSetSecret

    -HexSetOpening 

    -EpocBlockSecret

    -EpocBlockOpening

    -EpocBlockRandomize

    -MaxMasternodes

    -LimitPenaltyEpoch

    -BlocksPerYear

    -LimitThresholdNonceInQueue

    -DefaultMinGasPrice

    -MergeSignRange

    -RangeReturnSigner

    -MinimunMinerBlockPerEpoch

    -MinGasPrice


Contract State Transfer: Contract state would need to be transferred to the new version of the contract, either through a migration process or a persistent storage pattern.

Current TestNet Link: [Click here](https://XinFin.Network)

GitHub Code: [Click here](https://github.com/XinFinOrg/XDPoS-TestNet-Apothem)

Smart-Contract Link: [Click here](https://github.com/XinFinOrg/XDPoS-TestNet-Apothem/tree/master/contracts)

Right now, Full node have to upload Valid Self-KYC document (using IPFS) to be a Validator_Node and stake 10Million XDC.

#**Current self KYC Flowchart**

Smart-Contract code: [Click here](https://github.com/XinFinOrg/XDPoS-TestNet-Apothem/blob/master/contracts/validator/contract/XDCValidator.sol)


2.2. KYC Functions
The following list of function descriptions explains the major features of the XDPOS KYC SmartContract.

2.2.1.  Function UploadKYC
User can upload its kyc documents and this documents will be processed converted into bytes and will be added in a transaction data  and finally to a block

2.2.2.  Function VoteInvalidKYC
This function will be used by the Masternode Candidate who can view the submitted kyc and vote against it 	

2.2.3.  Function getLatestKYC
This function will be used to retrieve the latest  uploaded kyc of the mentioned user 

2.2.4.  Function getHashcount 
This will return the number of count of uploaded kyc.

2.2.5.  Function GetAllKYC
It will return an array of kyc data submitted by the mentioned user 


Google Doc: [Click here](https://docs.google.com/document/d/1GagNsOJaNgMj7UTMsUSKyJ_rBX9MjyDD5abd6dp1eOM/edit?usp=sharing_eil&ts=5c778823)

![WorkFlow](/assets/flow.jpg)