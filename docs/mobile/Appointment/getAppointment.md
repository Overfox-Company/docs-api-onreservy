# Get Appointments


## Requirements

A session token is required in the request header to retrieve the appointment information.


## Endpoint
```typescript
POST https://www.onreservy.com/api/mobile/appointments/getAppointments
```



## Responses

### <span style={{color: "rgb(161, 255, 39)"}}>Success</span>

```json
{
  "message": "List of appointments",
  "appointments": [
    {
      "_id": "appointment_id_1",
      "services": [
        {
          "name": "Service name",
          "description": "Service description",
          "price": 25,
          "duration": 30,
          "image": [],
          "_id": "service_id_1"
        }
      ],
      "date": "YYYY-MM-DD",
      "time": "HH:mm:ss",
      "duration": 30,
      "client_id": "client_id_1",
      "business_id": "business_id_1",
      "status": "pending",
      "payment_status": "unpaid",
      "price": 25,
      "notes": "",
      "createdAt": "YYYY-MM-DDTHH:mm:ss.sssZ",
      "updatedAt": "YYYY-MM-DDTHH:mm:ss.sssZ",
      "__v": 0
    }
  ]
}
```

### <span style={{color: "rgb(255, 39, 39)"}}>Failure</span>

This error occurs when the authorization token is missing, invalid, or could not be verified.
```json
{
  "message": "no autorizado"
}
```

