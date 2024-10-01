## PoR for A Trustless Reputation System

### Assessment

Assessment can refer to a variety of activities, including evaluating the identity reputation, data validation, and authenticity of digital identities. The assessment process involves verifying the integrity and accuracy of data stored on the system, as well as ensuring that the network and its nodes are functioning as intended.

Here is some major assessment in a trustless reputation system:

  - **Data validation**: Verifying the accuracy and integrity of the data stored on the system, including data encoding, decoding and processing.
  - **Identity Verification**: Verifying the authenticity of digital identities.
  - **Reputation Assessment**: Evaluating the historical honest behaviors in the form of a reputation score. 

### Consensus group

In order to prevent potential malicious behaviors and promote fairness and contribution to the system, consensus nodes in consensus group are randomly selected based on reputation, which means all consensus nodes have equal opportunity to engage in the consensus process regardless of its reputation. Probability of a consensus node selected in a consensus group depends on its current reputation Cu_R and cumulative reputation Cl_R which measures a node’s continuous contribution to blockchain, and Cu_R is to promote fairness of nodes selected in consensus group.

```math
p(i) = (α * Cl_R(i) + β * Cu_R(i)) / (∑Cl_R(i) + ∑Cu_R(i))
```
Where α+β=1,α>β>0

To avoid potential attacks and centralization, cumulative reputation and current reputation of a consensus group should meet the following requirements:

  - Average of cumulative reputation of a consensus group 1/N * ∑Cl_R(i) should be no less than average cumulative reputation of all candidate consensus nodes 1/n * ∑Cl_R(i)
  
```math
1/N * ∑Cl_R(i) ≥ 1/n * ∑Cl_R(j)
```
  
  where N is the number of nodes in the consensus group, n is the number of nodes in candidate consensus nodes pool.

  - Average of current reputation of a consensus group 1/N * ∑Cu_R(i) should be no less than average current reputation of all candidate consensus nodes 1/n * ∑Cu_R (i)

```math
1/N * ∑Cu_R(i) ≥ 1/n * ∑Cu_R(j)
```

  - To balance performance and scalability, nodes of a consensus group should be no less than n if n ≥ 16 and 4 if n < 16 [4]
  - To promote fairness, no participant node should create the majority of the blocks. The same node should not be selected in a consensus group to process two consecutive blocks. Besides, α should be larger than β.

### PBFT in consensus group

**PBFT** has an advantage of performance and efficiency with a few nodes. To improve performance, the size of consensus group committees should be limited. The minimum number of nodes in the consensus group is confined to n (n ≥16). In the consensus group, PBFT is run to generate a new candidate block. Detailed procedures are as follows:

  - In each consensus round, nodes in the consensus group elect a single leader node as block proposer.
  - The leader node proposes a candidate block with a set of transactions. Then broadcast the candidate block to other nodes in the consensus group.
  - When receiving the candidate block, other nodes in the consensus group validate and approve the block. If the candidate block gets supermajority approval (e.g., 2/3), it will be broadcasted to the entire blockchain network.

### Incentive

Reward is to economically incentive consensus nodes to behave honestly. The first incentive is block reward in forms of tangible asset (tokens), all consensus nodes selected in a consensus group successfully create a new block can get reward. And the second is reputation (intangible and non-transferable) which is changed over stages:

  - **Initial quick increase**. When consensus nodes in consensus group behave honestly, both current reputation and cumulative reputation will update according to following rules:

    Rule 1: Cu_R = Cu_R + 2^γ * R_reward
    
    Rule 1: Cl_R = Cl_R + Cu_R

    In each round, current reputation value of honest node will add 2^γ* R_reward cumulative reputation of honest nodes will add updated current reputation value.  is reputation factor which can be adjusted, R_reward  is a fixed reward value for block generation.

  - **Slow increase in mid-life for quick reward of mature participants**. To distinguish mature participants and new participants,  is adjusted to be smaller to make current reputation value increase slower.

  - **Prevention of over-control**. To prevent potential centralization and promote fairness, consensus nodes are not allowed to propose two consecutive blocks. Thus, the increase of reputation in consensus nodes is relatively evenly.

### Punishment

Punishment mechanism is adopted to penalize bad behaviors. There are two kinds of punishment, including collateral and reputation, which can be on all nodes in the consensus group or the node with malicious behaviors. If nodes in the consensus group behave maliciously, and other honest nodes in the consensus group do not detect malicious behaviors, then all nodes in the consensus group should be penalized. If honest nodes in the consensus group detect malicious behaviors of malicious nodes, only nodes with malicious behaviors will be penalized. Malicious behaviors will have a negative impact on reputation Cl_R = Cl_R / 2. The cumulative reputation will be halved and current reputation will be reset to 0, as Cu_R = 0
