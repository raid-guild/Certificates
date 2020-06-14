# Maker Badges

## Glossary

* Badges: participation in governance and Maker Protocol activities rewards badges associated with levels of participation. Most activities have tiers to associate the depth of engagement for each participant.

## Backend Service

`GET /address/{ADDRESS}`

### returns

An example of what the backend service provides is available here. The endpoint is currently public.

* badges.json - example data provided by merkle service

### Backend Schema

| Field Name | Description |
| ---------- | ----------- |
| id | Badge Id |
| parent | Activity that unlocks access to complete this badge |
| tier | Level or rank of the badge in comparison to it's class or activity |
| name | Abbreviated name when space is limited |
| longName | Longer name to appear when space is available |
| description | Longer description of the activity |
| resource | The best place to start completing this challengc |
| steps | An object with sequential steps for completing this activity |
| imgPath | An image for association |
| redeemed | This address has redeemed the current badge. 1 for True |
| unlocked | This address has unlocked the current badge. 1 for True |
| progress | The progress this address has made. 1 for Complete |
| proof | The proof required to redeem this badge, when applicable |
| root | The merkle tree root |

## Contract Addresses

```
const addresses = {
  badgeFactory: {
    kovan: "0x14D0DBd853923b856c000E4070631e4828E99DaE",
    mainnet: ""
  },
  manager: {
    kovan: "0x07857c2aA3804965CC2951E6c2EB5945dCE6C513",
    mainnet: ""
  }
};
```
_TODO: update to v3_

## Reading Badges On-Chain

### Check total supplyof badges

Get total supply of badges  
`let badgeSupply = factory.totalSupply()`

### Iterate through badges to get owned IDs
```
let redeemedBadges = [];

for (let i=0; i < badgeSupply; i++) {
  if (userAddress === factory.ownerOf(i)) {
    redeemedBadges.push(i)
  }
}
```

### Check IDs for Template IDs
```
let redeemedTemplates = redeemedBadges.map(badgeId => {
  factory.getBadgeTemplate(badgeId).toNumber()
})
```

## Activate Badges

### Check Challenges

When a user comes that is actively completing the challenge can use the on-chain check to prove their completion.

```
manager.potChallenge(templateId)
```

### Activate Badge

```
// @param proof Merkle Proof
// @param templateId Template Id
// @param tokenURI IPFS Hash for data storage
factory.activateBadge(proof, templateId, tokenURI)
```

## Deployment

Mainnet [WIP]  
Kovan https://badges.on.fleek.co/

Local development on Kovan. Check env.example for necessary environment variables.

### Source

* Contracts: [https://github.com/naszam/maker-badges](https://github.com/naszam/maker-badges)
* Merkle Service: [https://github.com/scottrepreneur/mb-merkle-service](https://github.com/scottrepreneur/mb-merkle-service)
* Front-end: [https://github.com/scottrepreneur/mb-frontend](https://github.com/scottrepreneur/mb-frontend)
* Dai Subgraph: [WIP]

### Demo

For more visualization, check the Demo: Update coming soon.

![](https://i.imgur.com/b9dhfcB.png)

![](https://i.imgur.com/H8fAUED.png)

## Researching

- Maker Badge Subgraph
- Gas is stupid expensive. Is this feasible/worthwhile as NFTs? DIDs?
- Roll-ups make a stronger security guarantee?
- Proxy signatures instead of Merkle Trees to save gas.

## Project Team
Scott Herren and Nazzareno Massari, Maker DAO Community Development Working Group
