# Moloch Badges and Certificates
Gamified Dao engagement

## Glossary

* Badges: onchain data and events inform the badge awards. things like voted on a proposal once, voted ten times, votes 100 times. This is powered by the Daohaus subgraph and has all Daos in the Moloch universe.
* Certificates and Achievements: Through the use of a Moloch Minion the ERC721 contract can be owned by the dao. This allows minting of new nfts to only be done through a passing proposal. Good use cases for this could be (Achievements), a Dao deciding a member or group of members deserve a special call out for some tasks that they did. Another use case (Certificates) would be to issue possible status in the dao, for example apprentice, journeyman, master. NFT metadata and images are stored on IPFS to insure validity and the ERC721 contract has also been modified to only allow these NFTs to be transferred in a 'Bag', meaning they can only be transferred to a new address all at the same time (not individually). this is to help insure NFTs are tied to a single identity but not lose the full erc721 compatibility all together (still displays in NFT wallets).

## Files

* badges.json - registry of badges and metadata IPFS hashes
* certs.json - registry of badges and metadata IPFS hashes

## Badge Subgraph

[daohaus subgraph playground](https://thegraph.com/explorer/subgraph/odyssy-automaton/daohaus)

### example query

`
  query($addr: String!) {
    badges(where: { memberAddress: $addr }) {
      memberAddress
      voteCount
      summonCount
      proposalSponsorCount
      proposalSubmissionCount
      rageQuitCount
      jailedCount
      dissents
      assents
      memberships
    }
  }
`

## Contract Addresses

```
const addresses = {
  badgeNFT: {
    kovan: "0xCB7d0E68D86AC5D05083e835C697BbB71236F8a1",
    mainnet: "0xAA65E7c8BBf3F2C6d2d8634Fc830F050a55BBbF9"
  },
  certNFT: {
    kovan: "0xC7A137d45983bf9E38A06cbC77C7a73f5C8DA004",
    mainnet: "0x7b408ad9019c20c5a1222Bf7f7e58A6Fa00A086a"
  }
};
```

## schema
TODO

## Demo Project Description
Experiment to gamify the Moloch DAO universe with badges, Certificates and leaderboards.

3box integration is used to display profiles on member detail pages and leader boards. there is also the ability to 'favorite' any of the NFTs to your 3box profile so these claims can easily be shared across dapps.


### Deployment:

Mainnet https://badges.raidguild.org/

local dev on Kovan:
```
REACT_APP_INFURA_URI=https://mainnet.infura.io/v3/<infura id>
REACT_APP_CHAIN_ID=42
REACT_APP_GRAPH_URL=https://api.thegraph.com/subgraphs/name/odyssy-automaton/daohaus-kovan
```

#### github

* front end: [https://github.com/raid-guild/moloch-dao-badges](https://github.com/raid-guild/moloch-dao-badges)
* Subgraph: [https://github.com/odyssy-automaton/daohaus-supergraph](https://github.com/odyssy-automaton/daohaus-supergraph)
* Certificate contract: [https://gist.github.com/dekanbro/06e49a31dd5ec3cf13683c20ab49fe3d](https://gist.github.com/dekanbro/06e49a31dd5ec3cf13683c20ab49fe3d)

#### demo

For more visualization, check the Demo: [https://youtu.be/yqwH3omETf0](https://youtu.be/yqwH3omETf0)

![](https://i.imgur.com/lBQDHva.png)

![](https://i.imgur.com/9E6pbQE.png)

### next steps
* Site design and badge illustrations

#### Project Team*
Dekan Brown And Sam Kuhlmann of RaidGuild
