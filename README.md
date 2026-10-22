# Property Inquiry API

A MuleSoft (Mule 4.12) practice project built in Anypoint Studio.
It uses sample data only. No real customer or company data is included.

## Endpoints

| Method | Path | Description |
|---|---|---|
| GET | /properties | Lists properties. Optional filters: `city`, `maxPrice` |
| POST | /inquiries | Submits an inquiry and returns a reference number |

## Run locally

1. Open the project in Anypoint Studio.
2. Right-click the canvas and choose **Run project**.
3. The API listens on port 8082.

## Examples

```
curl.exe "http://localhost:8082/properties?city=Dubai"

curl.exe -i -X POST http://localhost:8082/inquiries -H "Content-Type: application/json" -d "{\"name\":\"Test User\",\"email\":\"test@example.com\",\"propertyId\":1}"
```

If name, email or propertyId is missing, the API returns HTTP 400 with `{"error":"name, email and propertyId are required"}`.

## Concepts used

HTTP Listener, Choice router, DataWeave, variables, status codes, Logger.

## Planned

Trigger an RPA bot from /inquiries using Anypoint RPA Manager.
