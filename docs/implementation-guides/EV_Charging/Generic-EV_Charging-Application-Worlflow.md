# Generic EV Charging Application Workflow

## Overview

This document outlines the workflow for a generic Electric Vehicle (EV) charging application using the Beckn Protocol. The workflow includes interactions between the EV charging provider and the EV owner (user) for searching, selecting, booking, and completing an EV charging session.

A typical workflow for a loan application consists of the following steps

### Step 1: User searches for EV Chargers
The user provides his/her current location to find the nearest EV Chargers to charge his EV vehicle

### Step 2: Provider sends nearby EV Chargers
The provider sends all the EV Charger providers and their catalogs nearby to the user.

### Step 3: User selects EV Charger
Selects the EV provider which satisfies his requirements.
In thi stage user may select additional features such as:
[i] User can block/reserve the charger for a certain time slot
[ii] If the user is a fleet driver he will just comes and connects the charger whenever the charger is ready to use
[iii] User can select the charger type he wants to use such as A.C. or D.C.
[iv] User selects the vehicle type of his electrical vehicle (2-wheeler/3-wheeler/4-wheeler)
[v] User can select the start time and end time of the charging - (While in the case of reservation done by user)

### Step 4: Provider sends quoted price
The provider will receive the order based on the user requirements.
The user gets the quoted price, including the breakup of the price details.

### Step 5: User initializes the order
User initializes the order by providing billing details 
The BAP will send the billing details the BPP to initialize the order. 
Here, the user will provide their ```Name, email ID and Phone Number``` and updates the payment details

### Step 6: Provider sends draft order
The provider sends the draft order with the payment and fulfilment terms to the BAP.
Based on how much units of energy user used during charging as `tariff_per_unit`
If the user also done the reservation the transaction includes the reservation price as well 
The `tariff_per_unit` might change with the charger type as we know that A.C. charger type has different price compared to D.C. charger type.

### Step 7: User 

## Workflow Stages

### 1. Discovery (Search for EV Chargers)

#### User-side Actions

- Search for EV chargers based on criteria (e.g., location, charger type)
- View list of energy sources, such as EV chargers, Solar Farms providing EV charging, Houses, etc.

#### Provider-side Actions

- Publish catalog of energy sources and EV chargers

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
