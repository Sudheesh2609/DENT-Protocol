# Battery Swapping Workflow

## Overview
This document outlines the workflow for Battery Swapping using the Beckn Protocol. The workflow includes interactions between the Battery Swapping Service provider and the EV owner (User) for search, select, and completing an Battery Swapping session.

Bear in mind, this is just an example workflow for a simple EV Charing workflow between a EV User and a Battery Swap Provider.

A typical workflow for Battery Swapping consists of the following steps

#### Step 1: User searches for Battery Swapping service Providers
The user provides his/her current location and specific details (These details will act as filters for searching Battery Swapping services) to find the nearest Battery Swapping service for EV

#### Step 2: Provider sends catalogs of nearby Battery Swapping service Providers
The provider sends all the nearby Battery Swap service Providers and their catalogs to the user.
The catalog will consist of all the services provided by the provider, such as charging types, connector types, battery swapping services etc.,

#### Step 3: User selects a Provider for Battery Swap
Selects the provider that satisfies his/her requirements.
In this stage, the user may select additional features such as:
1. The user can block the time slot along with the start and end times.
2. The user can select the EV battery type and vehicle type of the EV.

#### Step 4: Provider sends quoted price
The provider will receive the order based on the user's requirements.
The user gets the quoted price, including the breakdown of the price details.
The breakdown should include:
  - Battery Swap Service price, and GST & taxes etc;
  - Price for reservation (if not used reservation this will be 0 INR)

#### Step 5: User initiates the order
User initializes the order by providing billing details. 
Here, the user will provide their `Name`, `Email ID` and `Phone Number` and updates the payment details

#### Step 6: Provider sends draft order
The provider sends the draft order with the payment and fulfillment terms to the user-side.
If the user done the reservation the transaction includes the price for that price as well

#### Step 7: User confirms the order
User sees the draft order and confirms it by agreeing to the payment and fulfilment terms and conditions
The confirm status will sent to the provider saying that user has paid the price

#### Step 8: Provider sends the order activation
The provider will activates the order and informs user that the order is activated

#### Step 9: User checks the status of the order
The user requests to fetch the updates/status of his/her order

#### Step 10: Provider sends the status of the order
The provider will send the order updates with current status to the user

## Search (Searching for EV Chargers)
1. The user declares the intent for Battery Swap service request to the providers
2. Providers publish their catalogs
