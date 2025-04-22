# Add Appointments


## Requiriments

You must send the following parameters in JSON format:

- `services`: (array) Id list of services to book.
- `date`: (string) Appointment date (format: YYYY-MM-DD).
- `time`: (string) Appointment time (format: HH:mm).
- `business_id`: (string) Business ID.
- `worker_id`: (string) Worker ID.

## Endpoint
```typescript
POST https://www.onreservy.com/api/mobile/appointments/addAppointments
```

## Use

```json
{
  "services": ["service1", "service2"],
  "date": "2025-04-21",
  "time": "14:00",
  "business_id": "12345",
  "worker_id": "67890"
}
```

## Responses

### <span style={{color: "rgb(161, 255, 39)"}}>Success</span>

```json
{
  "message": "Appointment created successfully",
  "user": {
    "_id": "user_id",
    "user": "user_full_name",
    "email": "user@email.com",
    "name": "user_name",
    "password": "password",
    "lastName": "user_last_name",
    "phone": null,
    "avatar": "user_avatar_url",
    "liked_business": ["business_id_1", "business_id_2"],
    "verified": false,
    "googleId": "google_id",
    "createdAt": "created_at_date",
    "updatedAt": "updated_at_date",
    "__v": 0,
    "notifications": [
      {
        "business_data": {
          "name": "business_name",
          "avatar": "business_avatar_url",
          "_id": "business_id"
        },
        "status": "status",
        "appointment_id": "appointment_id",
        "message": "Nmessage",
        "read": false,
        "_id": "notification_id",
        "createdAt": "notification_created_at"
      }
    ]
  },
  "appointments": [
    {
      "_id": "appointment_id",
      "services": [
        {
          "name": "service_name",
          "description": "service_description",
          "price": 0,
          "duration": 0,
          "image": [],
          "_id": "service_id"
        }
      ],
      "date": "YYYY-MM-DD",
      "time": "HH:mm:ss",
      "duration": 0,
      "client_id": "user_id",
      "business_id": "business_id",
      "status": "pending",
      "payment_status": "unpaid",
      "price": 0,
      "notes": "notes",
      "createdAt": "created_at_date",
      "updatedAt": "updated_at_date",
      "__v": 0
    }
  ]
}
```

### <span style={{color: "rgb(255, 39, 39)"}}>Failure</span>

Below are the possible error responses and their meanings:

```json
{
  "message": "Empty body"
}
```
The request body is missing.

```json
{
  "message": "no autorizado"
}
```
The request is not authorized. The token is missing or invalid.

```json
{
  "message": "Invalid JSON"
}
```
The request body is not valid JSON.

```json
{
  "message": "All fields are required"
}
```
One or more required fields (`services`, `date`, `time`, `business_id`) are missing.

```json
{
  "message": "Client not found"
}
```

The `business_id` provided does not match any existing business.

```json
{
  "message": "Business not found"
}
```
The `services` array is missing or empty.

```json
{
  "message": "Services are required"
}
```
An unexpected server error occurred.

```json
{
  "message": "Error in signup route",
  "error": {}
}
```