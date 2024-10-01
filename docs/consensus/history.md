In the blockchain world, consensus is a crucial mechanism that enables a decentralized network of nodes to agree on the state of the blockchain, ensuring that all nodes have the same version of the blockchain. There are currently many consensuses with their own solutions solving the trilemma problem. The most well-known consensus is [Proof of Work (PoW)][bitcoin_whitepaper] which uses computer power to solve a complex mathematical puzzle which is considered a fair mechanism to reach consensus but it still consumes a lot of energy and has low scalability. [Proof of Stake (PoS)][ethereum_2.0] was created to address the limitations of PoW by introducing the concept of probabilistically creating the next block based on the amount of cryptocurrency staked. On the other hand, PoS still raises concerns about its centralization because the more tokens a particular entity has staked, the higher the chance of being chosen to create the next block.

One of the great features of blockchain is that it can validate something even without a deep sense of what is being validated. This feature might bring to the witness whether this thing is the original truth or not. An obvious problem is a fraudulent smart contract deployed by a fraudster. There is nothing to do with this problem because the blockchain is open to any entities with any purposes, even malicious intent towards others. Therefore, any system or blockchain itself must have some mechanisms to validate the source of truth and incentivize honest behavior and give all entities some kind of confidence in the first place. In this paper, it is introduced as Proof of Reputation for a trustless reputation system.

Proof of Reputation (PoR) is designed to leverage the reputation of participants in the network as a determinant of their influence on the consensus process. The idea behind PoR is to assign mining power or voting rights based on the reputation of the participants, which is a reflection of their past behavior, contributors, and trustworthiness within the network.

## Related Work

**Reputation-Based Consensus Algorithms**

Historically, reputation systems have been known as a means of harnessing some form of reputation data. They function by facilitating the collection, aggregation, and distribution of data about a specific entity. This data can thereafter be used to characterize and predict that entity’s future actions. Essentially, users within a network can decide who they will trust and to what extent by referring to reputation data. A reputation system, in addition to the foregoing, is a socially corrective mechanism, as the incentive of positive reputation and the disincentive of negative reputation will generally encourage good behavior in the long run. After a reputation system collects reputation data, it can be shared among users, who can then use it to evaluate other users before making decisions about intended or future interactions, without ever having previously interacted. Examples of the practical application of this system can be found on eCommerce websites like Amazon or eBay where reputation attributed to a seller is influenced by ratings through previous transactions. Another use case is in government where a country like China incentives the behavior of the citizens through a social credit score system. Earlier works proposed possibilities of applying a reputation-based model to distributed computing. The downside was that the approach was not completely decentralized.

In the blockchain context, a reputation-based consensus mechanism works in a way where reputation serves as the incentive for good behavior and the node with the highest reputation gets to publish a new block. [1] proposed the Blockchain Reputation-Based Consensus (BRBC) mechanism in which a node in the network must have a reputation score higher than a set threshold to be able to publish a new block. Also, a judge is randomly selected that is responsible for updating node reputation values. However, none of these addresses the behavior of a node on a transactional basis as it interacts with other nodes in the network.

**Fair Proof of Reputation consensus (FPoR)** [2]

Current permissionless consensus protocols suffer centralization, unfairness and performance challenges. All PoW, PoS, DPoS can cause centralization issues, which is unfair to new participant nodes and contrary to the decentralization nature of blockchain. Besides, performance of permissionless consensus is still lower than permissioned consensus. FPoR is presented as a reputation-based consensus, which takes advantage of collateral, committee-based consensus, reputation-based node selection, PBFT, incentive mechanisms with reward and penalization.

The FPoR consensus protocol includes following main steps:

  - **Collateral**: Nodes who want to participate in consensus need collateral as security deposit, and only nodes with collateral can be candidate consensus nodes.
  - **Consensus group selection** Candidate consensus nodes with collateral are randomly selected based on reputation to form a consensus group, who is responsible for the new block proposal.
  - **PBFT** in consensus group: Nodes in the consensus group run PBFT protocol to verify and agree on the new block.
  - **Block propagation**: The block verified by the consensus group will propagate to the blockchain network, and be known to all participant nodes.

## References:
[1] M. T. de Oliveira, L. H. Reis, D. S. Medeiros, R. C. Carrano, S. D. Olabarriaga, and D. M. Mattos, “Blockchain reputation-based consensus: A scalable and resilient mechanism for distributed mistrusting applications,” Computer Networks, vol. 179, p. 107367, 2020.

[2] Tao Zhang, Zhigang Huang. “FPoR: Fair proof-of-reputation consensus for blockchain”


[bitcoin_whitepaper]: https://bitcoin.org/bitcoin.pdf "Bitcoin Whitepaper"
[ethereum_2.0]: https://ethereum.org/en/developers/docs/consensus-mechanisms/pos "Ethereum 2.0"