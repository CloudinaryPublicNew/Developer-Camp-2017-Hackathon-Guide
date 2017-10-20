# How to automatically tag images with Amazon Rekognition 

![Meir Feinberg](https://cloudinary-res.cloudinary.com/image/upload/bo_1px_solid_rgb:eee,c_thumb,dpr_2.0,g_face,h_42,r_max,w_42,z_0.8/profile_meir_feinberg.jpg "Meir Feinberg")

By
[Meir Feinberg](https://cloudinary.com/blog/author/meir_feinberg)
<time datetime="2017-10-19">Oct 19, 2017</time>

* [Image Manipulation](https://cloudinary.com/blog/tag/Image-Manipulation)
* [Features and Add-ons](https://cloudinary.com/blog/tag/Features-and-Add-ons)
* [Ruby-on-Rails](https://cloudinary.com/blog/tag/Ruby-on-Rails)
* [PHP](https://cloudinary.com/blog/tag/PHP)
* [Node](https://cloudinary.com/blog/tag/Node)
* [Django](https://cloudinary.com/blog/tag/Django)
* [Java](https://cloudinary.com/blog/tag/Java)
* [Image-management](https://cloudinary.com/blog/tag/Image-management)
* [Image Optimization](https://cloudinary.com/blog/tag/Image-optimization)


![Analyze and auto tag images with Amazon Rekognition](https://res.cloudinary.com/demo/image/upload/c_fill,w_770/dpr_2.0/Rekognition_tagging_blog.jpg)


Knowledge is power. And if you allow your users to upload images, you also probably want to better understand what their images contain. Whether a photo is of a building, people, animals, celebrities, or a product, image processing and analysis can assist in further comprehension. The benefits of this knowledge can go beyond "merely" categorizing your content and making your image library searchable: drawing insights from user generated content can be very useful! What better way to learn more about your users than to analyze the images they upload and find out what they care about and then have the ability to display relevant content to them according to their interests or even match them with other users that share similar interests.

Analyzing the contents of a photograph would be a huge time sink if performed manually on a lot of images. Enter [Amazon Rekognition](https://aws.amazon.com/rekognition/), a service that uses deep neural network models to detect and tag thousands of people, objects and scenes in your images, and lets you easily build powerful visual search and discovery into your applications. 

Cloudinary has integrated two Amazon Rekognition add-ons into its image management and manipulation pipeline: the [Amazon Rekognition Auto Tagging](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#aws_rekognition_categorization) add-on and the [Amazon Rekognition Celebrity Detection](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#aws_rekognition_celebrity_detection) add-on.

Customers are increasingly looking for innovative ways to generate more data around their media assets to derive actionable business insights. By using Amazon Rekognition, Cloudinary is bringing this technology closer to its clients so they can build their own unique experience.

_- Ranju Das, Director of Amazon Rekognition, Amazon Web Services, Inc._ 

## [Amazon Rekognition: Categorization](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#amazon_rekognition_categorization)

The Amazon Rekognition Auto Tagging add-on can automatically identify what's in a photograph and returns a list of detected categories and the confidence score of each category. The add-on is very simple to use: just set the `categorization` parameter of Cloudinary's image upload API to `aws_rek_tagging` while uploading a new image or updating an existing image and the response will include a list of identified tags for the image.

For example, uploading the following picture of a puppy to Cloudinary and requesting categorization:


{% codetabs -%}

{%- language name="Ruby", type="ruby" -%}

Cloudinary::Uploader.upload("cute_puppy.jpg", 
  :categorization => "aws_rek_tagging")
  
{%- language name="PHP", type="php" -%}

\Cloudinary\Uploader::upload("cute_puppy.jpg", 
  array("categorization" => "aws_rek_tagging"));



{%- language name="Python", type="python" -%}

cloudinary.uploader.upload("cute_puppy.jpg",
  categorization = "aws_rek_tagging")



{%- language name="Node.js", type="node" -%}

cloudinary.v2.uploader.upload("cute_puppy.jpg", 
  {categorization: "aws_rek_tagging"},
  function(error, result){console.log(result);});



{%- language name="Java", type="java" -%}

cloudinary.uploader().upload("cute_puppy.jpg", ObjectUtils.asMap(
  "categorization", "aws_rek_tagging"));





{%- language name="All", type="all" -%}

Ruby:

Cloudinary::Uploader.upload("cute_puppy.jpg", 
  :categorization => "aws_rek_tagging")



PHP:


\Cloudinary\Uploader::upload("cute_puppy.jpg", 
  array("categorization" => "aws_rek_tagging"));


Python:


cloudinary.uploader.upload("cute_puppy.jpg",
  categorization = "aws_rek_tagging")


Node.js:


cloudinary.v2.uploader.upload("cute_puppy.jpg", 
  {categorization: "aws_rek_tagging"},
  function(error, result){console.log(result);});


Java:

cloudinary.uploader().upload("cute_puppy.jpg", ObjectUtils.asMap(
  "categorization", "aws_rek_tagging"));

{% endcodetabs -%}


[URL](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#image_of_a_cute_puppy)[Ruby](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#image_of_a_cute_puppy)[PHP](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#image_of_a_cute_puppy)[Python](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#image_of_a_cute_puppy)[Node.js](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#image_of_a_cute_puppy)[Java](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#image_of_a_cute_puppy)[JS](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#image_of_a_cute_puppy)[jQuery](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#image_of_a_cute_puppy)[React](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#image_of_a_cute_puppy)[Angular](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#image_of_a_cute_puppy)[.Net](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#image_of_a_cute_puppy)[Android](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#image_of_a_cute_puppy)[All](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#image_of_a_cute_puppy)

URL:

`https://res.cloudinary.com/demo/image/upload/cute_puppy.jpg`

Ruby:

<pre>
cl_image_tag("cute_puppy.jpg")
</pre>

PHP:

<pre>
cl_image_tag("cute_puppy.jpg")
</pre>

Python:

<pre>
CloudinaryImage("cute_puppy.jpg").image()
</pre>

Node.js:

<pre>
cloudinary.image("cute_puppy.jpg")
</pre>

Java:

<pre>
cloudinary.url().imageTag("cute_puppy.jpg")
</pre>

JS:

<pre>
cl.imageTag('cute_puppy.jpg').toHtml();
</pre>

jQuery:

<pre>
$.cloudinary.image("cute_puppy.jpg")
</pre>

React:

<pre>
<Image publicId="cute_puppy.jpg" >

</Image>
</pre>

Angular:

<pre>
<cl-image public-id="cute_puppy.jpg" >

</cl-image>
</pre>

.Net:

<pre>
cloudinary.Api.UrlImgUp.BuildImageTag("cute_puppy.jpg")
</pre>

Android:

<pre>
MediaManager.get().url().generate("cute_puppy.jpg")
</pre>[![image of a cute puppy](https://res.cloudinary.com/demo/image/upload/cute_puppy.jpg "image of a cute puppy")](https://res.cloudinary.com/demo/image/upload/cute_puppy.jpg)

The upload response includes the various categories that were automatically detected in the uploaded photo together with the confidence level of the detected category. So Amazon Rekognition is 91% sure that the picture contains a puppy and is 82% sure that the breed is Newfoundland.

<pre>
..."info": {
  "categorization": {
    "aws_rek_tagging": {
      "status": "complete", 
      "data": [
        {"tag": "Animal", "confidence": 0.9117},
        {"tag": "Canine", "confidence": 0.9117}, 
        {"tag": "Dog", "confidence": 0.9117}, 
        {"tag": "Mammal", "confidence": 0.9117}, 
        {"tag": "Pet", "confidence": 0.9117}, 
        {"tag": "Puppy", "confidence": 0.9117}, 
        {"tag": "Newfoundland", "confidence": 0.8253}, 
        {"tag": "Husky", "confidence": 0.596}, 
        {"tag": "Adorable", "confidence": 0.5791} 
...
</pre>

For more information on the Amazon Rekognition Auto Tagging add-on, see the [documentation](https://cloudinary.com/documentation/aws_rekognition_auto_tagging_addon).

## [Amazon Rekognition: Celebrity Detection](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#amazon_rekognition_celebrity_detection)

The Amazon Rekognition Celebrity Detection add-on can automatically recognize thousands of celebrities in a wide range of categories, such as entertainment and media, sports, business, and politics. 
This add-on is also very simple to use: just set the `detection` parameter of Cloudinary's image upload API to `aws_rek_face` while uploading a new image or updating an existing image, and the response will include a list of identified celebrities for the image. 

For example, uploading the following picture to Cloudinary and requesting detection:

[Ruby](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#api_example_3)[PHP](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#api_example_3)[Python](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#api_example_3)[Node.js](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#api_example_3)[Java](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#api_example_3)[All](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#api_example_3)

Ruby:

<pre>
Cloudinary::Uploader.upload("brangelina.jpg", 
  :detection => "aws_rek_face")
</pre>

PHP:

<pre>
\Cloudinary\Uploader::upload("brangelina.jpg", 
  array("detection" => "aws_rek_face"));
</pre>

Python:

<pre>
cloudinary.uploader.upload("brangelina.jpg",
  detection = "aws_rek_face")
</pre>

Node.js:

<pre>
cloudinary.v2.uploader.upload("brangelina.jpg", 
  {detection: "aws_rek_face"},
  function(error, result){console.log(result);});
</pre>

Java:

<pre>
cloudinary.uploader().upload("brangelina.jpg", ObjectUtils.asMap(
  "detection", "aws_rek_face"));
</pre>

[URL](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#brangelina)[Ruby](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#brangelina)[PHP](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#brangelina)[Python](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#brangelina)[Node.js](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#brangelina)[Java](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#brangelina)[JS](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#brangelina)[jQuery](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#brangelina)[React](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#brangelina)[Angular](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#brangelina)[.Net](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#brangelina)[Android](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#brangelina)[All](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#brangelina)

URL:

`https://res.cloudinary.com/demo/image/upload/brangelina.jpg`

Ruby:

<pre>
cl_image_tag("brangelina.jpg")
</pre>

PHP:

<pre>
cl_image_tag("brangelina.jpg")
</pre>

Python:

<pre>
CloudinaryImage("brangelina.jpg").image()
</pre>

Node.js:

<pre>
cloudinary.image("brangelina.jpg")
</pre>

Java:

<pre>
cloudinary.url().imageTag("brangelina.jpg")
</pre>

JS:

<pre>
cl.imageTag('brangelina.jpg').toHtml();
</pre>

jQuery:

<pre>
$.cloudinary.image("brangelina.jpg")
</pre>

React:

<pre>
<Image publicId="brangelina.jpg" >

</Image>
</pre>

Angular:

<pre>
<cl-image public-id="brangelina.jpg" >

</cl-image>
</pre>

.Net:

<pre>
cloudinary.Api.UrlImgUp.BuildImageTag("brangelina.jpg")
</pre>

Android:

<pre>
MediaManager.get().url().generate("brangelina.jpg")
</pre>[![brangelina](https://res.cloudinary.com/demo/image/upload/brangelina.jpg "brangelina")](https://res.cloudinary.com/demo/image/upload/brangelina.jpg)

The upload response includes the various celebrities that were automatically detected in the uploaded photo together with the confidence level of the detected celebrity. So Amazon Rekognition is 100% sure that this is a picture of Brad Pitt and Angelina Jolie. The response also includes information about unrecognized faces detected in the image if relevant, and the results provide detailed data on each face's location, pose, orientation within the image, and facial landmarks. 

<pre>
{
...
"info": 
  {"detection": 
    {"aws_rek_face": 
      {"status": "complete",
       "data": 
        {"celebrity_faces": 
          [{ 
            "name": "Angelina Jolie",
            "match_confidence": 100.0
            "face":
             {"bounding_box":
               {"width"...
              },
              "landmarks":
               [{"type": "eyeLeft",
                 "x": ...
               }],
            ...
           },
                 ...
            "name": "Brad Pitt",
            "match_confidence": 100.0},
                 ...
        "unrecognized_faces": [ ],
         ...
}}}}}
</pre>

For more information on the Amazon Rekognition Celebrity Detection add-on, see the [documentation](https://cloudinary.com/documentation/aws_rekognition_celebrity_and_face_detection_addon).

## [Automatically tagging images](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#automatically_tagging_images)

Cloudinary allows you to [tag uploaded images](https://cloudinary.com/documentation/upload_images#tagging_images), where each image can be assigned one or more tags. You can also leverage the Amazon Rekognition add-ons to automatically assign tags to your images based on a minimum confidence score of identified categories/celebrities.

Simply add the `auto_tagging` parameter to the upload call and the image is automatically assigned resource tags based on the Amazon Rekognition detected categories/celebrities. The value of the `auto_tagging` parameter is the minimum confidence score of a detected celebrity that should be used for the automatically assigned resource tag. The value of the `auto_tagging` parameter is given as a decimal value between 0 and 1, where 1 represents 100%. Assigning these resource tags allows you to list and search images in your media library using Cloudinary's API and Web interface.

Note that the automatic tagging feature can be used with either of the Amazon Rekognition add-ons or with **both** together. The following example automatically tags an uploaded image with all detected categories _and_ celebrities that have a confidence score of at least 70% (auto_tagging = 0.7).

[Ruby](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#api_example_5)[PHP](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#api_example_5)[Python](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#api_example_5)[Node.js](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#api_example_5)[Java](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#api_example_5)[All](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#api_example_5)

Ruby:

<pre>
Cloudinary::Uploader.upload("steve.jpg", 
  :detection => "aws_rek_face", 
  :categorization => "aws_rek_tagging",
  :auto_tagging => 0.7)
</pre>

PHP:

<pre>
\Cloudinary\Uploader::upload("steve.jpg", 
  array(
    "detection" => "aws_rek_face", 
    "categorization" => "aws_rek_tagging", 
    "auto_tagging" => 0.7));
</pre>

Python:

<pre>
cloudinary.uploader.upload("steve.jpg",
  detection = "aws_rek_face",
  categorization = "aws_rek_tagging",
  auto_tagging = 0.7)
</pre>

Node.js:

<pre>
cloudinary.v2.uploader.upload("steve.jpg", {
  detection: "aws_rek_face", 
  categorization: "aws_rek_tagging", 
  auto_tagging: 0.7},
  function(error, result){console.log(result);});
</pre>

Java:

<pre>
cloudinary.uploader().upload("steve.jpg", ObjectUtils.asMap(
  "detection", "aws_rek_face", 
  "categorization", "aws_rek_tagging",
  "auto_tagging", "0.7"));
</pre>

[URL](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#steve_jobs)[Ruby](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#steve_jobs)[PHP](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#steve_jobs)[Python](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#steve_jobs)[Node.js](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#steve_jobs)[Java](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#steve_jobs)[JS](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#steve_jobs)[jQuery](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#steve_jobs)[React](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#steve_jobs)[Angular](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#steve_jobs)[.Net](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#steve_jobs)[Android](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#steve_jobs)[All](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#steve_jobs)

URL:

`https://res.cloudinary.com/demo/image/upload/steve.jpg`

Ruby:

<pre>
cl_image_tag("steve.jpg")
</pre>

PHP:

<pre>
cl_image_tag("steve.jpg")
</pre>

Python:

<pre>
CloudinaryImage("steve.jpg").image()
</pre>

Node.js:

<pre>
cloudinary.image("steve.jpg")
</pre>

Java:

<pre>
cloudinary.url().imageTag("steve.jpg")
</pre>

JS:

<pre>
cl.imageTag('steve.jpg').toHtml();
</pre>

jQuery:

<pre>
$.cloudinary.image("steve.jpg")
</pre>

React:

<pre>
<Image publicId="steve.jpg" >

</Image>
</pre>

Angular:

<pre>
<cl-image public-id="steve.jpg" >

</cl-image>
</pre>

.Net:

<pre>
cloudinary.Api.UrlImgUp.BuildImageTag("steve.jpg")
</pre>

Android:

<pre>
MediaManager.get().url().generate("steve.jpg")
</pre>[![Steve Jobs](https://res.cloudinary.com/demo/image/upload/steve.jpg "Steve Jobs")](https://res.cloudinary.com/demo/image/upload/steve.jpg)

The response of the upload API call above returns the **detected categories**, the **detected celebrities**, and the **automatically assigned tags**.

<pre>
{
   ...
  "tags": ["people","person","human","electronics","iphone","mobile phone","phone","Steve Jobs"]
  "info": {
    "detection": {
      "aws_rek_face": {
        "status": "complete",
        "data": [{
           "name": "Steve Jobs", 
           "match_confidence": 99.99,
            "face": {
              "bounding_box": {
                "width"...
             },
             "landmarks": [{
               "type": "eyeLeft",
                 "x": ...
               }],
            ...
           },
        "unrecognized_faces": [ ],
         ...
     }
     "categorization": {
       "aws_rek_tagging": {
         "status": "complete", 
         "data": [{
           "tag": "People", "confidence": 0.9925},
           "tag": "Person", "confidence": 0.9925},
           "tag": "Human", "confidence": 0.9924},
           "tag": "Electronics", "confidence": 0.7918},
           "tag": "Iphone", "confidence": 0.7918},
           "tag": "Mobile Phone", "confidence": 0.7918},
           "tag": "Phone", "confidence": 0.7918},
           "tag": "Computer", "confidence": 0.6756},
           "tag": "Tablet Computer", "confidence": 0.6756},
           "tag": "Face", "confidence": 0.5396},
           "tag": "Selfie", "confidence": 0.5396},
           "tag": "Cell Phone", "confidence": 0.5067}]}
      ...  
}
</pre>

## [Summary](https://cloudinary.com/blog/how_to_automatically_tag_images_with_amazon_rekognition#summary)

Understanding the images that your users upload can provide you with great insights, allow you to take actions such as creating dynamic content pages, and match content to user preferences. Cloudinary’s service together with the fully integrated [Amazon Rekognition Auto Tagging](https://cloudinary.com/documentation/aws_rekognition_auto_detection_addon) and [Amazon Rekognition Celebrity Detection](https://cloudinary.com/documentation/aws_rekognition_celebrity_and_face_detection_addon) add-ons provides developers with the powerful ability to enhance their image content management as well as increase their online users’ engagement and conversion.

[![](https://res.cloudinary.com/demo/image/upload/f_auto,q_auto/aws_rek_celebrity_detection.jpg)](https://cloudinary.com/console/addons?#aws_rek_face)

[![](https://res.cloudinary.com/demo/image/upload/f_auto,q_auto/aws_rek_auto_tagging.jpg)](https://cloudinary.com/console/addons?#aws_rek_tagging)

The add-ons are available with all Cloudinary plans, and both add-ons have a free tier for you to try out. If you don't have a Cloudinary account yet, sign up for a free account [here](https://cloudinary.com/users/register/free).

<small>(Hugh Laurie photo credit to <a href="https://www.flickr.com/photos/elfidomx/" data-popup="true">Fido</a>)</small>