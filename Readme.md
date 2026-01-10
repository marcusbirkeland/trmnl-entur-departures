# TRMNL Entur Departures

Shows departures from any specific stop (quay) for public transport in norway. Uses the free and publicly available
[Entur GraphQL API](https://api.entur.io/graphql-explorer/journey-planner-v3).

## How to use

1. Adjust parameters in the graphql request to change quay (station).

    - QuayID may be found by inspecting the responses in your browsers network tab from using [Entur Departures](https://entur.no/kart)

2. Set up a Recipe in your BYOS instance.

    - Data Strategy: Polling
    - Polling Url: <https://api.entur.io/journey-planner/v3/graphql>
    - Polling Verb: POST
    - Polling Body: Format your GraphQL query to JSON. Example:

  ```json
  {"query":"# Avganger\n\n{\n  quay(id: \"NSR:Quay:74792\") {\n    id\n    name\n    estimatedCalls(timeRange: 72100, numberOfDepartures: 16,  includeCancelledTrips: true) {     \n      realtime\n      \n      aimedArrivalTime\n      aimedDepartureTime\n      expectedArrivalTime\n      expectedDepartureTime\n      date\n      destinationDisplay {\n        frontText\n      }\n      quay {\n        id\n      }\n      serviceJourney {\n        directionType\n        journeyPattern {\n          line {\n            id\n            transportMode\n            publicCode}}\n      }\n    }\n  }\n}\n"}
  ```

- Copy the contents of `markdown.liquid`, and paste into the Markup section.

## Demo

<img width="1441" height="862" alt="image" src="https://github.com/user-attachments/assets/3b9bdb3a-9c0c-48b3-94d8-e412eb8f63bb" />
