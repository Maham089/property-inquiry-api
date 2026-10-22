# Property Inquiry API

A MuleSoft (Mule 4.12) practice project built in Anypoint Studio.
It uses sample data only. No real customer or company data is included.

## Endpoints

| Method | Path | Description |
|---|---|---|
| GET | /properties | Lists properties. Optional filters: `city`, `maxPrice` |
| POST | /inquiries | Submits an inquiry. Returns 201 and a reference number |
| GET | /inquiries/{reference} | Returns a saved inquiry, or 404 if not found |

## Run locally

1. Open the project in Anypoint Studio.
2. Right-click the canvas and choose **Run project**.
3. The API listens on port 8082.

## Examples

```
curl.exe "http://localhost:8082/properties?city=Dubai"

curl.exe -i -X POST http://localhost:8082/inquiries -H "Content-Type: application/json" -d "{\"name\":\"Test User\",\"email\":\"test@example.com\",\"propertyId\":1}"

curl.exe -i "http://localhost:8082/inquiries/INQ-12345"
```

## Responses

| Case | Status | Body |
|---|---|---|
| Inquiry created | 201 | reference, name, email, propertyId, receivedAt |
| Missing name, email or propertyId | 400 | `{"error":"name, email and propertyId are required"}` |
| Unknown reference | 404 | `{"error":"Inquiry not found"}` |

Inquiries are stored in memory using Object Store, so they are lost when the app restarts.

## Concepts used

HTTP Listener, Choice router, DataWeave, variables, status codes, Object Store, error handling (On Error Continue), Logger.

## Planned

Trigger an RPA bot from /inquiries using Anypoint RPA Manager.
