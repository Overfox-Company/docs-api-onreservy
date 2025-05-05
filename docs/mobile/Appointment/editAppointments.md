# Edit Appointments

## Requirements

A session token is required in the request header to edit an appointment.

## Endpoint

```typescript
POST https://www.onreservy.com/api/mobile/appointments/editAppointments
```

## Request Body

Send the following parameters in JSON format. Only `appointment_id` is required; other fields are optional and will be updated if provided.

- `appointment_id`: (string, required) The ID of the appointment to edit.
- `services`: (array, optional) List of service IDs to update.
- `workers`: (string, optional) Worker ID to assign.
- `date`: (string, optional) New appointment date (format: YYYY-MM-DD).
- `time`: (string, optional) New appointment time (format: HH:mm).
- `status`: (string, optional) Appointment status (`pending`, `confirmed`, `completed`, `canceled`).

### Example

```json
{
  "appointment_id": "appointment_id_1",
  "services": ["service_id_1", "service_id_2"],
  "workers": "worker_id_1",
  "date": "2025-05-10",
  "time": "15:30",
  "status": "confirmed"
}
```

## Responses

### <span style={{color: "rgb(161, 255, 39)"}}>Success</span>

```json
{
  "message": "Your appoiment has been updated succesfully",
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
          "original_service_id": "service_id",
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
      "status": "confirmed",
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
  "message": "unauthorized"
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
The `appointment_id` field is missing.

```json
{
  "message": "Appointment not found"
}
```
The provided `appointment_id` does not match any existing appointment.

```json
{
  "message": "Business not found"
}
```
The business associated with the appointment does not exist.

```json
{
  "message": "Some service IDs are invalid for this business",
  "invalidServiceIds": ["invalid_service_id_1"]
}
```
One or more provided service IDs do not belong to the business.

```json
{
  "message": "No valid services found"
}
```
None of the provided service IDs are valid for the business.

```json
{
  "message": "Error in signup route",
  "error": {}
}
```
An unexpected server error occurred.