This is a code block with tabs for each languages:


{% codetabs name="URL", type="url" -%}
https://res.cloudinary.com/demo/image/upload/steve.jpg

{%- language name="Ruby", type="ruby" -%}
cl_image_tag("steve.jpg")

{%- language name="PHP", type="php" -%}
cl_image_tag("steve.jpg")

{%- language name="Python", type="python" -%}
CloudinaryImage("steve.jpg").image()

{%- language name="Node.js", type="node" -%}
cloudinary.image("steve.jpg")

{%- language name="Java", type="java" -%}
cloudinary.url().imageTag("steve.jpg")

{%- language name="JavaScript", type="javascript" -%}
cl.imageTag('steve.jpg').toHtml();

{%- language name="JQuery", type="jquery" -%}
$.cloudinary.image("steve.jpg")

{%- language name="React", type="react" -%}
<Image publicId="steve.jpg"></Image>

{%- language name="Angular", type="angular" -%}
<cl-image public-id="steve.jpg"></cl-image>

{%- language name=".Net", type="net" -%}
cloudinary.Api.UrlImgUp.BuildImageTag("steve.jpg")

{%- language name="Android", type="android" -%}
MediaManager.get().url().generate("steve.jpg")

{%- language name="iOS", type="ios" -%}
cloudinary.createUrl().generate("steve.jpg")
{%- endcodetabs %}