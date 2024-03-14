Generate Image URL API
======================

The Generate Image URL API is provided by Focalx and can be called by the client's backend system or frontend to generate image URLs for uploading images.

.. contents::
   :local:
   :depth: 2

Request
-------

**Content Type**: ``application/json``

- **Method**: ``POST``
- **URL**: ``/signedurls``

**Header Parameters**:

- **Authorization**: 
    - *Type*: Bearer Token
    - *Required*: Mandatory
    - *Description*: Client must send the token received from the previous API.

- **Content-Type**: 
    - *Type*: application/json
    - *Description*: The request should be of JSON data type.

**Input Parameters**:

- **images**: 
    - *Type*: List of Image Objects
    - *Description*: List of images to generate URLs for.

**Image Object Details**:

- **name**: 
    - *Type*: String
    - *Description*: Name of the image.
    
- **imageposition**: 
    - *Type*: String
    - *Description*: This is an optional field

    Example:

    .. code-block:: json
      
      {
        "images": [
          {
               "name": "09e800a6-ffd0-4282-9c71-034f68e0b164.jpg",
               "imageposition": "" // This is an optional field 
          }
       ]
     }

Response
--------

- The response is a JSON array, each element containing:

    - **image_name**: 
        - *Type*: String
        - *Description*: Name of the image.
    - **generated_url**: 
        - *Type*: String
        - *Description*: URL generated for the image.

    Example:

    .. code-block:: json

        [
            {
                "image_name": "rwsr",
                "generated_url": "hrrpa"
            }
        ]

Status Codes
------------

- **2xx**: Success
- **400**: Application Error
- **401**: Unauthorized error
- **500**: Server Error


Response Error (when status code is 400)
----------------------------------------

- **error**: 
    - *Type*: String
    - *Description*: This will provide a JSON error indicating that parameters are missing or incorrect.

   example:
       
       .. code-block:: json

            {
                "error": "Missing vehicle data item",
            }