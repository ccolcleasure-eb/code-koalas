# Services Suggestions

## Add functionality to existing endpoints.

It should be a pattern to maintain existing endpoints, rather than creating new ones.

In one example case, we have `/applicant-interview-service/interviewdetails` that
accepts parameters to filter the current user's appointments (_not limited to interview
type appointments_) based on their status and whether or not they are pending (future dated).
This endpoint also accepts a parameter for the appointment id, to fetch one specifically.

Yet, another appointment was created to handle fetching appointments based on an `extTalentId`.
This endpoint, `/applicant-interview-service/interviewdetailsByExtTalentId` accepts one parameter,
`extTalentId`, and the main difference between the existing endpoint and this one is that it does
not use the auth token to perform its work.

The logic inside of the `/interviewdetails` could have simply been updated to determine that, if
the parameter `extTalentId` is provided, take the logical path that doesn't end up using the authToken.

