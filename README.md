# Croppie Demo 

Cropppie lib. give as a feature to crop any image as you want.
## Installation
Import css
```html
<link rel="stylesheet" href="croppie.css" />
```
Import Jquery
```html
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
```
Import Js
```html
<script src="croppie.js"></script>
```
After More useful style we use Boostrap for it So import Boostrap.

## Working

```html
<input type="file" name="upload_image" id="upload_image" accept="image/x-png,image/gif,image/jpeg"/>
```

```js
$("#upload_image").on("change", function () {
          if (typeof $image_crop === "object") {
            $image_crop.croppie("destroy");
          }
          var reader = new FileReader();
          reader.onload = function (event) {
            $image_crop = $("#image_demo").croppie({
              enableExif: true,
              viewport: {
                width: 200,
                height: 200,
                type: "square", //circle
              },
              boundary: {
                width: 300,
                height: 300,
              },
            });

            $image_crop.croppie("bind", {
              url: event.target.result,
            });
          };
          reader.readAsDataURL(this.files[0]);
          $("#uploadimageModal").modal("show");
          $(".crop_image").click(function (event) {
            $image_crop
              .croppie("result", {
                type: "canvas",
                size: "viewport",
              })
              .then(function (response) {
                $("#uploadimageModal").modal("hide");
                $("#uploaded_image").prop("src", response);
                $("#uploaded_image").css("display", "block");
              });
            //   }
          });
        });
```

Above create a Modal For Image crop id = uploadimageModal and add submit button class = crop_image.
```html
 <button class="btn btn-success crop_image">Crop Image</button>
```


## Width and Height
```js
 $image_crop = $("#image_demo").croppie({
              enableExif: true,
              viewport: {
                width: 200,
                height: 200,
                type: "square", //circle
              },
              boundary: {
                width: 300,
                height: 300,
              },
            });

```
give as you want width and height for you

viewport: If can change type for square and circle for a type of image
Boundary: that you outer box for the image is set into the box

You can upload image after receive the image throw this function
```js
 $image_crop
              .croppie("result", {
                type: "canvas",
                size: "viewport",
              })
              .then(function (response) {
                console.log(response); // response is the image you can pass this image for upload .
              });
```

If you want to use multiple crop image on one page make sure you using this code before the second function
```js
$image_crop.croppie("destroy");
```

For more information about croppie please croppie sire or use this demo to learn more.
