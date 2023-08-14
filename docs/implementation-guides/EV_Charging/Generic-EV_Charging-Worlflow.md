# Generic EV Charging Application Workflow

## Overview

This document outlines the workflow for a generic Electric Vehicle (EV) Charging using the Beckn Protocol. The workflow includes interactions between the EV charging provider and the EV owner (user) for search, select, book, and completing an EV charging session.

Bear in mind, this is just an example workflow for a simple EV Charing workflow between a EV User and a EV Charging Provider.

A typical workflow for a EV Charging consists of the following steps

### Step 1: User searches for EV Chargers
The user provides his/her current location and specific requirements (These requirements will act as filters for EV Charging Providers) to find the nearest EV Chargers to charge his/her EV vehicle

### Step 2: Provider sends catalogs of EV Chargers nearby
The provider sends all the EV Charger providers and their catalogs nearby to the user.
The catalog will consists of all the services provided by the provider such as charging types, connector types and battery swapping services etc.,

### Step 3: User selects EV Charger
Selects the EV provider which satisfies his requirements.
In this stage user may select additional features such as:
1. User can block/reserve the charger for a certain time slot along with start and duration time of the Charging session.
2. User can select the charger type he wants to use such as A.C. or D.C.
3. User can select the connecter type such as CCS2 etc.,
4. User selects the vehicle type of his electrical vehicle (2-wheeler/3-wheeler/4-wheeler) and sends the information of the user EV.

### Step 4: Provider sends quoted price
The provider will receive the order based on the user requirements.
The user gets the quoted price, including the breakup of the price details.
The breakup should include:
  - Tariff per unit (i.e., INR/KWh), the tariff per unit might change by the charger type and location of Energy Charger Provider
  - Price for block/reservation

### Step 5: User initiates the order
User initializes the order by providing billing details. 
Here, the user will provide their `Name`, `Email ID` and `Phone Number` and updates the payment details

### Step 6: Provider sends draft order
The provider sends the draft order with the payment and fulfilment terms to the user-side.
Based on how much units of Electrical Energy user used during charging as tariff_per_unit as already mentioned above in INR/KWh
If the user also done the block/reservation the transaction includes the price for block/reservation price as well 
The tariff_per_unit might change with the charger type as we know that A.C. charger type has different price compared to D.C. charger type.

### Step 7: User confirms the order
User sees the draft order and confirms it by agreeing to the payment and fulfilment terms and conditions
The confirm status will sent to the provider saying that user has paid the price

### Step 8: Provider sends the order activation
The provider will activates the order and informs user that the order is activated

### Step 9: User checks the status of the order
The user requests to check the updates/status of his/her order

### Step 10: Provider sends the status of the order
The provider will send the order updates with current status to the user

## 1. Search (Searching for EV Chargers)

#### User-side Actions
- Searching for EV Charging Providers based on current location of user
- Searching for EV Charging Providers based on Charing types/Connector types
- Searching for EV Charging Providers based on Name/Code of provider
- Searching for EV Charging Providers based on ratings
- View list of energy sources, such as EV chargers, Solar Farms providing EV charging, Houses, etc.
- Viewing the catalog/details of services provided by a particular energy charging provider

#### Provider-side Actions
- Publish list of energy sources and EV chargers including Solar Farms providing EV charging, Houses, etc.
- Publish list of provders in 5Km radius of user
- Publish list of provders with the requested Charing types/Connector types
- Publish catalog/details of services provided by energy charging providers
- Publish catalog of services provided by a particuar energy charging providers

### 2. Ordering (Select and Book Charging)

#### User-side Actions

- Select an EV charger from the list of energy sources
- Choose charging type (block/reserve charger or use immediately)
- Select charger type (A.C. or D.C.)
- Select vehicle type (2-wheeler, 3-wheeler, 4-wheeler)
- Choose start and end time of charging (if reservation is made)

#### Provider-side Actions

- Receive user's selection and preferences
- Send draft order to the selected EV charging provider with quoted price

### 3. Fulfillment (Order Initialization)

#### User-side Actions

- Provide billing details (Name, email ID, Phone Number)

#### Provider-side Actions

- Receive billing details from the user
- Send draft order with payment and fulfillment terms

### 4. Fulfillment (Order Confirmation)

#### User-side Actions

- Confirm the order by agreeing to terms

#### Provider-side Actions

- Receive order confirmation from the user
- Send active confirmed order object to the user

### 5. Status Updates and Monitoring

#### User-side Actions

- Fetch the latest status of the order

#### Provider-side Actions

- Provide the latest status of the order to the user

## Beckn Protocol API Workflow

Refer to the diagrams below for visual representations of the Beckn Protocol API workflows for each stage.

Please note that these interactions are illustrative and can vary based on real-world scenarios and platforms.
