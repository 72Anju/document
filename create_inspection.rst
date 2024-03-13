CreateInspection API
====================

The CreateInspection API is provided by Focalx and can be called by the client's backend system or frontend to create an inspection.

.. contents::
   :local:
   :depth: 6

Prerequisites
-------------

- A valid token is required to call this API.

Request
-------

**Content Type**: ``multipart/form-data``

- **Method**: ``POST``
- **URL**: ``/Create-Inspection``

**Header Parameters**:

- **Authorization**: 
    - *Type*: Bearer Token
    - *Required*: Mandatory
    - *Description*: Client must send the token received from the previous API.

- **Content-Type**: 
    - *Type*: multipart/form-data
    - *Description*: The request should be of form data type.

**Input Parameters**:

- **provider**: 
    - *Type*: String
    - *Description*: Customer ID (provided by Client).

- **frame_number**: 
    - *Type*: String
    - *Description*: Customer Frame number (provided by Client).

- **userid**: 
    - *Type*: String
    - *Description*: ID of user in Focalx backend.

- **registration number**: 
    - *Type*: String
    - *Description*: Vehicle plate number.

- **name**: 
    - *Type*: String
    - *Description*: User name.

- **email**: 
    - *Type*: String
    - *Description*: User email.

- **phone**: 
    - *Type*: String
    - *Description*: User phone number.

- **mileage**: 
    - *Type*: String
    - *Description*: Vehicle mileage.

- **meta_data**: 
    - *Type*: String
    - *Description*: JSON data in string format received from client.

- **make**: 
    - *Type*: String
    - *Description*: Car manufacturer.

- **model**: 
    - *Type*: String
    - *Description*: Car model.

- **color**: 
    - *Type*: String
    - *Description*: Color of the car.

- **body_type**: 
    - *Type*: String
    - *Requirement*: ``Mandatory``
    - *Available Types*: ``suv,sedan,hatchback,station,lcv``
    - *Description*: ``Car body type.It should select from only Available types specified above.``

   example:
       
       .. code-block:: form-data

            curl --location 'https://clientname.focalx.ai/createinspection/' \
            --header 'Authorization: Bearer eyJ0eXAiOiJK' \
            --form 'make="austrianwfgw"' \
            --form 'model="megawala"' \
            --form 'year="2023"' \
            --form 'registration_number="BB20972hjjhjh"' \
            --form 'mileage="12345"' \
            --form 'vin="5LGX6PBB6K6KLI854SOM"' \
            --form 'body_type="suv"' \
            --form 'color="yellowblack"' \
            --form 'energy_type="petrol"' \
            --form 'process_id="8H4PKG7XAX18"' \
            --form 'platform="IOS"' \
            --form 'body_size="medium"' \
            --form 'meta_data="\"\""' \
            --form 'current_time_zone="GMT2"'



Response
--------

**Response Parameters**:

- **inspection**: 
    - *Type*: Inspection Object
    - *Description*: Contains the inspection results with inspection ID.

- **car**: 
    - *Type*: Car Object
    - *Description*: Car information.

- **car_master**: 
    - *Type*: Car Master Object
    - *Description*: Car properties.

**Inspection Object Details**:

- **id**: 
    - *Type*: String
    - *Description*: Inspection ID.

- **latitude**: 
    - *Type*: String
    - *Description*: Latitude where the inspection took place.

- **longitude**: 
    - *Type*: String
    - *Description*: Longitude where the inspection took place.

- **process_id**: 
    - *Type*: String
    - *Description*: Process ID related to the client's data.

- **platform**: 
    - *Type*: String
    - *Description*: Platform from which images were generated.

- **thumbnail_url_public**: 
    - *Type*: String
    - *Description*: Public URL of the inspection thumbnail.

- **is_user_approved**: 
    - *Type*: Boolean
    - *Description*: Indicates whether the user has approved the inspection.

- **name**: 
    - *Type*: String
    - *Description*: Client's name.

- **phone_number**: 
    - *Type*: String
    - *Description*: Client's phone number.

- **email**: 
    - *Type*: String
    - *Description*: Client's email address.

- **meta_data**: 
    - *Type*: String
    - *Description*: JSON string containing metadata sent by the client.

**Car Object Details**:

- **vin**: 
    - *Type*: String
    - *Description*: Vehicle Identification Number.

- **registration_number**: 
    - *Type*: String
    - *Description*: Vehicle's registration number.

- **color**: 
    - *Type*: String
    - *Description*: Color of the vehicle.

**Car Master Object Details**:

- **make**: 
    - *Type*: String
    - *Description*: Manufacturer of the car.

- **model**: 
    - *Type*: String
    - *Description*: Model of the car.

- **year**: 
    - *Type*: String
    - *Description*: Manufacturing year of the car.

   Example (responce):
       
        .. code-block:: json

            {
                "inspection": {
                    "id": "ea90225d-4ab1-4376-ba1a-68826835f246",
                    "latitude": null,
                    "longitude": null,
                    "mileage": 12345.0,
                    "process_id": "EEMUX2AI77W3",
                    "platform": "IOS",
                    "thumbnail_url_public": "https://s3.eu-central.assets/images/car.png",
                    "is_user_approved": false,
                    "is_pdf_ready": false,
                    "pdf_url_public": null,
                    "name": null,
                    "phone_number": null,
                    "email": null,
                    "is_report_submitted": false,
                    "meta_data": "\"\"",
                    "is_active": true,
                    "created_on": "2024-01-17T09:35:52.896778Z",
                    "updated_on": "2024-01-17T09:35:52.896806Z",
                    "car_item": "1b4c90d8-74d2-4789-a22e-c12ae9508814",
                    "created_by": "69abc05c-ebab-4e1a-bc0f-f5c103bf0f3f",
                    "updated_by": "69abc05c-ebab-4e1a-bc0f-f5c103bf0f3f"
                },
                "car": {
                    "id": "1b4c90d8-74d2-4789-a22e-c12ae9508814",
                    "vin": "JK9EDR84UREDJA1MU92H",
                    "registration_number": "BB20972hjjhjh",
                    "first_registration_year": 0,
                    "color": "yellowblack",
                    "is_active": true,
                    "created_on": "2024-01-17T09:35:52.885482Z",
                    "updated_on": "2024-01-17T09:35:52.885513Z",
                    "car_master_item": "44e8f815-22f3-45e4-ae34-8a057a8b6614",
                    "created_by": "69abc05c-ebab-4e1a-bc0f-f5c103bf0f3f",
                    "updated_by": "69abc05c-ebab-4e1a-bc0f-f5c103bf0f3f"
                },
                "car_master": {
                    "id": "44e8f815-22f3-45e4-ae34-8a057a8b6614",
                    "make": "austrianwfgw",
                    "model": "megawala",
                    "year": 2023,
                    "body_size": null,
                    "segment": null,
                    "length": null,
                    "width": null,
                    "height": null,
                    "max_length": null,
                    "max_width": null,
                    "max_height": null,
                    "is_active": true,
                    "created_on": "2023-06-02T09:54:05.504903Z",
                    "updated_on": "2023-06-02T09:54:05.504934Z",
                    "body_type_master_item": {
                        "name": "SUV",
                        "slug": "suv"
                    }
                },
                "inspection_stats": {
                    "id": 3,
                    "active_images": 0,
                    "inactive_images": 0,
                    "close_shot_images": 0,
                    "beauty_shot_images": 0,
                    "internal_images": 0,
                    "custom_images": 0,
                    "external_processable_images": 0,
                    "external_unprocessable_images": 0,
                    "processed_images": 0,
                    "offside_damages": 0,
                    "manually_added_accepted_damages": 0,
                    "manually_added_rejected_damages": 0,
                    "ai_detected_accepted_damages": 0,
                    "ai_detected_rejected_damages": 0,
                    "total_damages": 0,
                    "damages_accuracy": "0.00",
                    "damages_precision": "0.00",
                    "damages_recall": "0.00",
                    "average_inference_time": "00:00:00",
                    "total_inference_time": "00:00:00",
                    "total_inspection_time": "00:00:00",
                    "is_active": true,
                    "created_on": "2024-01-17T09:35:52.906973Z",
                    "updated_on": "2024-01-17T09:35:52.906998Z",
                    "inspection_item": "ea90225d-4ab1-4376-ba1a-68826835f246"
                }
            }

Status Codes
------------

- **2xx**: Success
- **400**: Application Error with parameter issue
- **401**: Unauthorized error
- **500**: Server Error

Response Error (when status code is 400)
----------------------------------------

- **error**: 
    - *Type*: String
    - *Description*: This will provide a JSON error indicating that parameters are missing or incorrect

    
