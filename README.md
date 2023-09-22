# Decentralized Energy Transaction Protocol (DENT)

The Decentralized Energy Transaction (DENT) Protocol is an adaptation of [beckn protocol](https://github.com/beckn/protocol-specifications) for transactional use cases in the energy sector.

[release-v0.2.0 branch - main repo](https://github.com/beckn/DENT-Protocol/tree/release-v0.2.0) || [Link to PR](https://github.com/beckn/DENT-Protocol/pull/10)

---

## Release History

| Version | Release Date        | Adaptation to Core Spec Version | Authors      |
|:-------:|---------------------|---------------------------------|--------------|
| 0.2.0   | 1st September, 2023 | 1.1.0                           | Ravi Prakash, Akhil Jayaprakash |
| 0.1.0   | 24th June, 2023     | 1.1.0                           | Ravi Prakash |

## Working Group Members

| Name              | Role                           | Github Username |
|-------------------|--------------------------------|-----------------|
| Ravi Prakash      | Maintainer, Protocol Architect | @ravi-prakash-v |
| Pramod Varma      | Maintainer, Reviewer           | @pramodkvarma   |
| Sujith Nair       | Reviewer                       | @sjthnrk        |
| Akhil Jayaprakash | Subject Matter Expert          | @pulse-aj       |
| Ankit Mittal      | Subject Matter Expert          |                 |


## Introduction

The energy sector is of prime, global importance and is highly regulated. A core common objective of nongovernmental entities is to improve the functioning of the sector and make energy and fuel consumption more efficient. As a result, energy companies and energy infrastructure are increasingly targeted by private enterprises through energy transactions <sup>[[1](https://www.dentons.com/en/find-your-dentons-team/industry-sectors/energy/energy-trading-marketing-and-derivatives/energy-transactions)]</sup>

DENT Protocol (or simply DENT) enables the creation of a decentralized / federated network of platforms that perform interoperable commercial transactions that result in the transfer of energy from a energy producer to an energy provider. The energy producer isn't necessarily the energy generator, rather an entity that represents the energy supply. Similarly, an energy consumer isn't necessarily an appliance or a household, but more like a consumer that represents the energy demand. For example, an energy producer can be a Charging Point Operator that supplies energy to electric vehicles, or a Distribution Company that supplies energy to homes. Similarly, an energy consumer can be a vehicle that needs charging; a home appliance that needs electricity to run; or even the distribution company than needs energy from the power generation companies (like power plants). 

An important thing to note here is that when it comes to electrical energy, the energy transfer is not always from power plants to the appliances. In many cases, simple households with an energy surplus can also feed it back to the electricity grid and avail commercial benefits like reduced electricity bills. DENT Protocol enables creation of such contracts as well. 

Just like physical goods can be consumed or stored, energy can _also_ be _consumed_ or _stored_. DENT allows creation of energy contracts that not only enable the consumption of energy, but also the storage of energy (in batteries, capacitors, etc). 

> **Note :** DENT Protocol does NOT transfer "Energy" in its physical form. Enery transfer is still done via physical infrastructures like Generators, transmission lines, transformers, inverters, adaptors etc. DENT only facilites the creation of the energy transfer contract (order) that ultimately results in the physical transfer (fulfillment).

## Implementing the specification

To understanding how to implement the specification click [here](./docs/5_Implementation_Guide.md)

## Acknowledgements

The author(s) of this specification would like to thank the following volunteers for their contribution to the development of this specification

### Version 0.2.0
- Akhil Jayaprakash - Pulse Energy (pulseenergy.io)
- Ankit Mittal - Sheru (sheru.se)
- Sudheesh Kumar Potla - IIT Kharagpur ([@Sudheesh2609](https://github.com/Sudheesh2609))
- Sujith Nair - FIDE (fide.org)
- Pramod Varma - FIDE (fide.org)

## References
1. Energy Transactions - https://www.dentons.com/en/find-your-dentons-team/industry-sectors/energy/energy-trading-marketing-and-derivatives/energy-transactions
