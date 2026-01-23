# Presentation Notes

## Slide 1 (11s)
Good Day Ladies and Gentlemen, Stakeholders and alike, Today I will be discussing our "Conference room booking system API", how we set up our contract and how we validated it.

---

## Slide 2 (32s)
On today's Agenda, we will be discussing the following key topics, first is the problem & context which covers the problems we could face if we don't have an API and the reason it needs to be implemented. Secondly I will be covering the high level architecture regarding where it'll fit within the booking system, after that I'll quickly run through our use of OpenAPI 3.0 and the authentication used, then I'll dive deeper into the contract of our API, lastly I'll show proof of how we validated our API functions as expected.

---

## Slide 3 (1m 06s)
The Problem we would have if we had no API wpuld be that without a clear specification, frontend developers and backend developers could misinterpret data formats, leading to integration bugs, so by adopting a "Contract-First" approach, we defined the api-documentation.yaml first, thus ensuring that endpoints like /bookings have strict requirements and error messages are standardized. With this implementation, we avoid the misinterpretation of the different data formats meaning that there won’t be integration bugs.

---

## Slide 4 (20s)
The structure and flow of our architecture is from the client (where the user makes their booking), to the API (which is responsible for sending the requests to the backend), to the backend (which validates the requests received from API), to the data layer(which stores all bookings and related information). The API is important in this structure because it specified routes to all requests passing through it.

---

## Slide 5 (23s)
The Api was specified using OpenAPI 3.0.3 using YAML format, we set it up to authenticate users using JWT Bearer token for login and for accessing different functions. The tools we used were Swagger Editor to better interact with the document because of the visual feedback we receive, and we used Postman's mock servers and environments to test our API's functionality.

---

## Slide 6 (40s)
In this slide, I will be discussing the core of our API. The way we structured the API was into logical groups using "Tags" so that developers can easily find what they need. We also used "Reusable Schemas" for the data models, what this means is that we essentially defined the shape of the "Room" object in one place and the endpoints will reference that single definition. Lastly to explain how it works, by looking at the "Availability" endpoint, we can see how our API/Contract enforced strict rules, for example, the "date" parameter isn't optional, it's required and it accepts a specific date format, this prevents bad data from ever entering the system.

---

## Slide 7 (30s)
Now to tackle instances where edits need to me made to the API, If edits need to be made(for example adding a function to add a projector to the room), then it should be validated and ran through Postman and also ensuring that the tests that were already present do not break, then generate the full document to share with the team. The benefit of this is that it prevent failures where the changes break other sections of the API thus affecting the frontend.

---

## Slide 8 (31s)
Lastly to highlight the common API development traps and how developing a contract-first approach helped us avoid them. Instead of vague messages, we use a strict error schema that returns clear messages and codes. Sensitive write operations were secured through a Bearer Token to ensure that users that are authenticated can make bookings or view bookings. Inconsistent data was removed by reusing and referencing the same schemas between the different endpoints to guarantee consistency.

---

## Slide 9 (25s)
To validate our API, we used Postman, we already have a mock server set up and I will pass this following script to test and retrieve a list of the rooms should be returned because I'm sending 200 which is a success code, and as we see, it returns a list of the rooms.

---

## Slide 10 (32s)
In summary, the API we created shows how a contract-first approach improved clarity and reliability. By having clear specification upfront, we removed integration misunderstandings, and enforced consistency with data and error handling. Reusable schemas make sure that there's consistency between all endpoints, while Postman and Swagger Editor make the process of testing, maintaining and evolving the API simpler without breaking the frontend.