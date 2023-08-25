# General Energy Transaction Workflow #1

## Overview
This implementation guide outlines the energy transaction process where Sheru (Energy Aggregator) purchases energy from individuals or crowds using the Beckn Protocol. The guide provides step-by-step instructions on how Sheru interacts with the Unified Energy Interface (UEI) to discover energy sources, select providers, initiate transactions, confirm orders, and monitor status updates.

Bear in mind that this is just an example workflow for a simple Energy Transaction, where Sheru buys the Energy from the individuals/crowd using UEI.

(Note: Here, User -> Sheru and Provider -> Individual/Crowd who is providing energy.)

A typical workflow for EV Charging & Battery Swapping consists of the following steps:

#### Step 1: Discovery of Electricity
The user provides the amount of energy needed in kwh (which will act as a filter for the search).

#### Step 2: Provider sends catalogs of EV Chargers nearby
The UEI sends all the catalogs to the user.
The list of catalogs consists of:
   - Individuals/Crowds from whom energy can be bought.
   - Locations where energy can be purchased.
   - Available areas/locations for energy purchases

#### Step 3: Sheru selects an Provider
User selects a suitable individual/crowd provider from the provided catalogs.
The UEI notifies the chosen individual that Sheru intends to buy energy

#### Step 4: Provider selects mode of Energy Transfer
The provider will select the mode of energy transfer
1. Automatic Dispatch
- Complete control of discharge is given to the UEI/DENT Protocol.
2. Manual Dispatch
- Commit to providing the required energy; penalties for non-compliance are applicable.

#### Step 5: Initiating the transaction
The user initializes the order by declaring the required amount of energy in units

#### Step 6: Provider sends draft order
The provider sends the draft order with the payment and fulfillment terms to the user's side.
UEI calculates a quote and sends the payment amount based on tariffs and taxes
Payment link is sent to user for completing the payment

#### Step 7: Provider confirms to satisfy the fulfillment terms
If Provider selects Automatic Dispatch, no additional confirmation is needed.
If Provider selects Manual Dispatch:
  - Provider confirms commitment to fulfillment terms.
  - If energy provision fails, a penalty is applicable.
Upon provider's confirmation, UEI notifies Sheru and requests payment
#### Step 8: User activates order by payment
The user makes the payment and sends a confirmation to UEI.
UEI replies with a confirmation of fulfillment and payment status.
The UEI will activate the order and informs user that the order is activated

#### Step 9: User checks the status of the order
The user requests to fetch the order status/amount of dispatched energy 

#### Step 10: UEI sends the status of the order
UEI provides status updates for the order.
UEI can send reminders to the provider for upcoming energy dispatch (manual or automatic).

## Search (Searching for Provider)
1. The user declares the intent for buying energy to the providers
2. Providers publish the catalogs

### User-side Actions
A user can declare their intent for buying energy in many ways like:
- Searching for  Providers based on location
- Searching for Providers based on quantity required (energy in kwh)
- Searching for Providers based on Name or Code of provider
- Searching for Providers based on ratings
- Viewing the catalog/details of services provided by a particular charging/Battery Swap providers

### Provider-side Actions
In this interaction, the Provider publishes their catalog. The catalog mainly consits of :
- Individuals or crowds from whom energy can be bought.
- Locations where energy can be purchased (Address)
- Full Name, Phone Number, Email-ID
  
### Logical Workflow
```mermaid
    sequenceDiagram
    User->>Provider: Declare Intent to buy energy
    Provider->>User: Publish Catalog of providers
```
### Beckn Protocol API Workflow
In beckn protocol, the search intent generated by the User Platform (BAP) is typically published on the gateway (BG) that broadcasts the intent to multiple Provider platforms (BPPs). Each of the BPPs returns their catalogs directly to the BAP via asynchronous callbacks. The workflow for that is shown below.
```mermaid
    sequenceDiagram
    User Platform (BAP)->>Gateway (BG): Declare Intent to buy charging ( search )
    Gateway (BG)->>Registry: Lookup Provider Platforms (lookup)
    Registry->>Gateway (BG): List of Provider Platforms in 'x'km radius and 'y'kwh energy quantity required (200 OK)
    Gateway (BG)->>Provider Platform 1 (BPP1): Declare Intent to buy energy (search)
    Gateway (BG)->>Provider Platform 2 (BPP2): Declare Intent to buy energy (search)
    Gateway (BG)->>Provider Platform n (BPPn): Declare Intent to buy energy (search)
    Provider Platform 1 (BPP1)->>User Platform (BAP): Publish Catalog of Provider 1 (on_search)
    Provider Platform 2 (BPP2)->>User Platform (BAP): Publish Catalog of Provider 2 (on_search)
    Provider Platform n (BPPn)->>User Platform (BAP): Publish Catalog of Provider n (on_search)
```

## Select and On_Select
1. User selects a Provider from the list which satisfies the requirements
2. The BAP notifies the chosen Provider and requests the provider to select the mode of energy transfer
   - Automatic Dispatch
   - Manual Dispatch
   
### User-side Actions
- Selecting Provider after viewing catalogs
- BAP notifies the providr and requests Provider to select the mode of energy transfer

### Provider-side Actions
- Receive user's selection
- Selecting mode of energy transfer (Manual or Automatic Dispatch)

### Logical Workflow
The below diagram illustrates the logical interactions between a User and Provider during the Selection stage
```mermaid
    sequenceDiagram
    User->>Provider: Selects a provider and notifies the provider
    Provider->>User: Receives user selection
    User->>Provider: Request to select mode of energy transfer
    Provider->>User: Selects mode of energy transfer
```

### Beckn Protocol API Workflow
```mermaid
   sequenceDiagram
   User Platform (BAP)->> Provider 1 (BPP): Select Provider after seeing catalogs of all providers (select)
   Provider 1 (BPP)->>User Platform (BAP): Publish Provider 1 catalog (on_select)
   User Platform (BAP)->> Provider 1 (BPP): Request for selection in mode of transfer (on_select)
   Provider 1 (BPP)->>User Platform (BAP): Selects mode of energy transfer (select)
```

## Order Initialization
In this stage, the User provides the required information and initiates the order

### User-side Actions
- User provides the value of the required amount of energy in kwh 
- User provides the billing details `Name`, `Email ID` and `Phone Number`
- User updates the payment details and initiates the order
  
### Provider-side Actions
- Request for billing details
- Receive billing details from the user
- Send draft order with payment and fulfillment terms
- Sends the payment link to the user along with breakdown of price and taxes

### Logical Workflow
```mermaid
    sequenceDiagram
    User->>Provider: Provides amount of energy needed (kwh)
    Provider->>User: Request for billing details 
    User->>Provider: Provides billing details like Name, Email ID and Phone Number 
    Provider->>User: Send draft order with payment transcript and fulfillment terms
    User->>Provider: Updates payment details and initiates the order
    Provider->>User: Sends the payment link to the user
```

### Beckn Protocol API Workflow
```mermaid
    sequenceDiagram
    User Platform (BAP)->> Provider 1 (BPP): BAP updates amount of energy needed (in kwh) and billing details (init)
    Provider 1 (BPP)->>User Platform (BAP): BPP sends draft order with breakdown and fulfillment terms (on_init)
    User Platform (BAP)->> Provider 1 (BPP): BAP Updates payment details and initiates the order
    Provider 1 (BPP)->>User Platform (BAP): BPP Sends the payment link to the BAP
```

## Fulfillment (Payment and Order Confirmation)
Provider has to give confirmation of the fulfillment terms if he chooses Manual Dispatch 
The, the User will check the order details and confirm the order with payment (might also update the order)
Post payment UEI will activate the confirmed order

### User-side Actions
- Confirms(\updates) the order by checking the order details and agreeing to fulfillment terms

### Provider-side Actions
- If provider chosen Manual Dispatch: Provider has to confirm that he accepts the terms and conditions upon that only user can confirm the order and satisfy the fulfillment terms.
- Receive order confirmation from the user
- Send active confirmed order to the user

## Status Updates and Monitoring

### User-side Actions

- Request to fetch the latest order status or amount of dispatched energy.
- Sends remainders to the provider for upcoming energy dispatch (manual or automatic)

#### Provider-side Actions

- Provide the latest status of the order to the user
### Logical Worklow
```mermaid
    sequenceDiagram
    Provider->>User: Confirms the agreement to the terms and conditions.
    User->>Provider: Confirms the order and pays the the price
    Provider->>User: Send active confirmed order
    User->>Provider: Request for latest status of order
    Provider->>User: Sends the latest status of order
    User->>Provider: Sends remainders to the provider for upcoming energy dispatch
```

### Beckn API Workflow
```mermaid
    sequenceDiagram
    Provider 1 (BPP)->>User Platform (BAP): BPP confirms to the terms and conditions (confirm)
    Provider 1 (BPP)->>User Platform (BAP): BPP requests for order confirmation and payment update (on_confirm)
    User Platform (BAP)->>Provider 1 (BPP): BAP confirms the order by fulfillment (confirm)
    Provider 1 (BPP)->>User Platform (BAP): BPP sends activation of confirmer order (on_confirm)
    User Platform (BAP)->>Provider 1 (BPP): Request for updates on status of order (status)
    Provider 1 (BPP)->>User Platform (BAP): BPP provides the latest status of the order to BAP (on_status)
    User Platform (BAP)->>Provider 1 (BPP): Remainder to the BPP of an upcoming dispatch of energy (status)
    Provider 1 (BPP)->>User Platform (BAP): BPP acknowledges the remainder from BAP (on_status)
```