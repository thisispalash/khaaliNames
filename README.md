# khaaliNames

> [!WARNING]
> This repository is now archived! Please refer to the following repos for
> current development:
> - Deprecation Util :: 
> [khaaliDimaag/khaaliSemVerV2-eth](https://github.com/khaaliDimaag/khaaliSemVerV2-eth)
> - Names Util (Contains Dictionary) :: 
> [khaaliDimaag/khaaliNamesV2-eth](https://github.com/khaaliDimaag/khaaliNamesV2-eth)
> - Onchain AppStore :: 
> [khaaliDimaag/khaaliStoreV1-eth](https://github.com/khaaliDimaag/khaaliStoreV1-eth)



Onchain user management library, powered* by 
[ENSv2](https://docs.ens.domains/ensv2/overview/).

<details>

  <summary>See past iterations of this idea</summary>
  
  > note that both iterations have low to none ENS support 

  - march 2026: 
  [first iteration](https://github.com/khaaliDimaag/khaaliNames/tree/v1)
  - rootstock builder camp: 
  [on rootstock](https://github.com/thisispalash/rootcamp-capstone/tree/master),
  [7579](https://github.com/thisispalash/rootcamp-capstone/tree/account)

</details>

## What this is

In its simplest form, this project is to help manage users onchain with a lot of
complexities and annoyances handled by khaaliNames. The core module is an 
onchain utility to generate random names according to milestones, with 
additional modules on top to apply this utility for user management and 
transparent contract discoverability. The latter also makes it possible to 
create a true onchain appstore as we control the registrar for the contract 
naming, making version upgrades explicit. For more, please see the [video going 
over the architecture](./assets/video.mov).

### Modules

**Deprecation Util (V1)**

While upgradeable contracts are immensely useful in terms of bug fixes, one 
glaring issue with them is that of _rug pulls_; ie, a contract deployer may 
change the core contracts of an app without any intimation to the app users. 
The deprecation utility is aimed at making that explicit.

Additionally, this util is how an onchain appstore is really possible since we 
control the registrar for the contract naming.

**Dictionary (V2)**

The dictionary uses solady's SSTORE2 to store data in the bytecode in an effort 
to reduce deployment costs. V2 now allows for arbitrary dictionaries instead of 
a fixed set as in V1. It additionally inherits the deprecation util, which would
lock the read functions on an upgrade, and a `migrate` functionality for admins 
to migrate to the names to the new dictionary.

**Names (V2)**

This is the core module in this repo. The change in V2 is to allow for arbitrary
dictionaries and milestones so an app developer has maximum flexibility. Also 
introduced is a bitmask system which informs how to generate names from the 
given dictionaries at a certain milestone.

**Avatar**

_incomplete_

**[Ethereum] Name Service**

_incomplete_

**Smart Contract Account**

_incomplete_

**Commerce**

_incomplete_

## Who this is for

The first user of this project is me (via @khaaliDimaag) to have user management
without the need for rebuilding the same thing multiple times, while also having
the users loosely connected with the same ecosystem.

More broadly, this project is for anyone building onchain applications where 
they need to address issues like smart contract accounts, non offensive 
usernames, user owned profiles, and progressive customisability.

## How to use

Currently this project is incomplete and this repo is abondoned. To try out V1
of this concept, please refer to 
[khaaliDimaag/khaaliNamesV1](https://github.com/khaaliDimaag/khaaliNamesV1) or 
interact with the contract directly at 
[`0xa0715EC44766D28ec2Bc8c7e94716A202937d4F2`](https://sepolia.etherscan.io/address/0xa0715ec44766d28ec2bc8c7e94716a202937d4f2#readContract).

Future work will be carried out in the following repos:
- khaaliDeprecation :: [khaaliDimaag/khaaliSemVerV2-eth](https://github.com/khaaliDimaag/khaaliSemVerV2-eth)
- khaaliNames :: [khaaliDimaag/khaaliNames-eth](https://github.com/khaaliDimaag/khaaliNames-eth)
- khaaliStore :: [khaaliDimaag/khaaliStoreV1-eth](https://github.com/khaaliDimaag/khaaliStoreV1-eth)

## License
> View full license text [in repo](./LICENSE) instead

Copyright 2026 @thisispalash

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
