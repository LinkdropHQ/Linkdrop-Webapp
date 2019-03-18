# Technical specification

### Core Architecture

#### Escrow Smart Contract

Ethereum Smart Contract based on ERCXX1 \(WIP, Interface for Linkdrop Escrow Contract\). Escrow Smart Contract is deployed by a Dapp/Web App.

#### Relayer

Server that calls an Escrow Smart Contract on behalf of receiver and pays the gas for the transaction. 

#### Web app

Web app that can be used to send and receive ether/tokens via links. 

### One-to-One Linkdrop URI standard

A standard to for Linkdrop URI based on ERCXX2 \(WIP\). 

Sender transfers ether or token to an Escrow Smart Contract compliant with ERCXX1 and gets a claiming link. Any mobile wallet or dapp that is compliant to ERCXX2 is able to claim the link by assembling together the required parameters.

```http
https://{webappHost}/{webappPath}?type={linkdropType...}&key={linkdropKey...}&chain={1}
```



|  parts | Notes |
| :--- | :--- |
| _webappHost_ | Linkdrop Web App Host |
| _webappPath_ | Claim Link Path for the Web App |
| _k_ | Linkdrop Key, ephemeral private key used to sign receiver address.  |
| _c_ | Ethereum address of the Escrow Contract |
| _chain_ | Ethereum Chain Id \(eg. 1\), by default Ethereum Mainnet |

Other query string parameters are all optional.

```http
// Example URL
https://app.linkdrop.org/claim?k=f3ce2b9b0252e7acf2c598e05628c7e87306ef6e236ad5f23b13db4f4afd7a84&c=0xf9377237024f172a1718f7958181e0835724b71a
```

