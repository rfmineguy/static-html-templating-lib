# static-html-templating-lib
A simple html templating library that makes writing repetitive html a little less repetitive.

# template.js
This library adds a system for populating html template tags with "dynamic content" for static websites
It works by leveraging the `<template>` html tag, and special `{{fields}}` in the template.

# Usage
```html
<template id="url-button-template">
  <a href={{url}}>
    <button type="button" class="btn btn-sm btn-outline-secondary" style="margin-right: 1rem">{{title}}</button>
  </a>
</template>

<template id="card-template">
<div class="col">
  <div class="card shadow-sm">
    <img src={{imgsrc}} width="100%" height="300px" background="#55595c" color="#eceeef" class="card-img-top" text="Thumbnail" style="padding:1rem; object-fit: contain">
    <div class="card-body">
      <h5 class="card-title">{{title}}</h5>
      <p class="card-text">{{description}}</p>
      <div class="d-flex justify-content-between align-items-center">
        <div id="urls" class="btn-group">
          <!-- Dynamically populated -->
        </div>
      </div>
    </div>
  </div>
</div>
</template>

<div id="project-container">
    <!-- Dynamically populated -->
</div>
```

```html
<script>
    emit((() => template('card-template', {
            title: "some title",
            imgsrc: "some/image/path.png",
            description: `
                Some description
            `,
            urls: [
                () => template('url-button-template', {
                    url: "https://github.com/rfmineguy/2024_barebones_os",
                    title: "Github",
                }),
            ],
        }))(), 'project-container');
</script>
```
