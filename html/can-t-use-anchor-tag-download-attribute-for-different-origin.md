# Problem with Using the Anchor Tag's Download Attribute Across Different Origins

When the goal is to enable users to download resources, the anchor tag is typically used.

```html
<a href="/download/resources.pdf" download>DOWNLOAD</a>
```

However, this approach fails when attempting to download resources from another origin. In such cases, the browser behaves similarly to any other anchor tag, resulting in redirection to the linked page.

```html
<a href="https://somedomain.com/download/resources.pdf" download>DOWNLOAD</a>
```

For downloads originating from other origins, JavaScript becomes necessary. Presented below is one approach to achieve this functionality.

```html
<button onclick="download()">DOWNLOAD</button>
<script>
  function download() {
    fetch('https://somedomain.com/download/resources.pdf')
      .then((response) => response.blob())
      .then((blob) => {
        const blobURL = window.URL.createObjectURL(blob);
        const link = document.createElement("a");
        link.href = blobURL;
        link.style = "display: none";
        link.download = 'resources.pdf';
        link.click();
      })
      .catch((error) =>
        // handle errors
      );
  }
</script>
```

It's important to be cautious when employing this approach, as disabling JavaScript in the browser would prevent users from accessing the content for download.
