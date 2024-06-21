## Model 1
### Predict Pallette
- URL
  - https://capstone-uwrmimd5cq-et.a.run.app/predict_palette
- Method:
  - POST
- Header
  - Content-Type: multipart/form-data
- Body
  - file (wajib): File gambar yang berisi wajah. Format yang didukung termasuk JPEG, PNG, dll.
- Status : Sukses (200 OK):
- Response
  ```
  {
    "extracted_skin_tone": "#aabbcc",
    "predicted_palette": ["#123456",
     "#654321",
     "#abcdef",
     "#fedcba",
     "#0f0f0f"]
  }
  ```
- Status : Kesalahan (400 Bad Request):
- Response
  ```
  {
    "error": "No file part"
  }
  ```
- Status : No File Sended 
- Response
  ```
  {
    "error": "No selected file"
  }
  ```
## Model 2
### macthing color pallete
- URL
  - https://capstone-model-2-uwrmimd5cq-et.a.run.app/color_matcher
- Description:
  - This endpoint accepts an image file and a list of colors. It processes the image to remove its background, determines the dominant color, and predicts a matching color from the provided palette.
- Method:
  - POST
- Request
  - Content-Type: multipart/form-data
- Parameter
  - image (file): The image file to be processed. This is a required parameter.
color_list (string): A JSON string representing a list of colors in hexadecimal format. This is a required parameter
- Status : Sukses (200 OK):
- Response:
  - Content-Type: application/json
- Response : Succesfull
  - Status Code: 200 OK

  ```
  {
    "dominant_color": "#hex_color",
    "predicted_color": "#predicted_color_hex"
  }
  ```
- Response : Error
  - Status : 400 Bad Request
  
Missing Image File:
```
{
  "error": "Image file is missing"
}
```

Missing Color List:
```
{
  "error": "Color list is missing"
}
```

Invalid Color List Format:
```
{
  "error": "Invalid color list format"
}
```

- Status Code: 500 Internal Server Error
```
{
  "error": "Error message"
}
```
