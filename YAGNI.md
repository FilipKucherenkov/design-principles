## You Aren't Gonna Need It (YAGNI)

### Principle Explanation:
The YAGNI principle emphasizes that you should not build features or components unless they are explicitly required. 
This helps maintain focus on current requirements, minimizes complexity, and avoids speculative work that may never be needed.

### Scenario:
Imagine you are implementing a feature in a distributed system to check if a person is over 18 or not. For this purpose, the product team has chosen to use a 3rd-party API with the following contract:

#### 3rd-party API Contract:
```
Request: { firstName: string, lastName: string }
Response: { age: int, gender: string, maritalStatus: string, ... }
```
Since your feature only requires checking if a person is over 18, your service should abstract this API and expose functionality relevant to this specific requirement.

### What to Implement
You should design a single, focused endpoint to meet the exact need:
#### Endpoint:
```
POST /applicant/checkAge  
Request: { firstName: "Filip", lastName: "Kucherenkov" }  
Response: { isOver18: true/false }
```

This endpoint will
- Take the user’s firstName and lastName.
- Interact with the 3rd-party API to retrieve the person’s age.
- Return true if the person is over 18, otherwise false.
Any additional functionality (e.g., exposing age, gender, or maritalStatus) would violate the YAGNI principle, as these are not required by the feature.

Why This Adheres to YAGNI? 
- Focus on the immediate requirement: You are only building the functionality to check if a person is over 18.
- Avoid speculative complexity: Adding endpoints to expose unused data (e.g., gender, maritalStatus) assumes future needs that may never materialize, making the system unnecessarily complex.
- Maintain simplicity and clarity: The service is purpose-driven and avoids unnecessary abstractions or features.

