CSS createObjectURL Test
========================

CSS stylesheets loaded from objectURLs contain blank url() values in rules if paths are relative

1. Create a stylesheet with a rule that contains a relative url such as: 
    background-image: url('image.jpg');
2. Use XMLHttpRequest to load stylesheet as blob
3. Add stylesheet link with a objectUrl created from a blob as the href  
4. Once sheet has loaded, inspect document.styleSheets
5. cssText of rules containing relative url() links will display as empty

Rules with urls should display as url('path/to/file") but it has been changed to blank url()
Without a reference to the original url path there is no way to update it to work with the objectUrl

Resource is loaded as though url is page url, causing console messages such as below:

```javascript
Resource interpreted as Font but transferred with MIME type text/html: "http://fchasen.github.io/CSS-createObjectURL-test/"
```

Without a reference to the original url path there is no way to update it to the correct path.

Test case can be viewed at:
http://fchasen.github.io/CSS-createObjectURL-test/

Browsers Tested:

- Chrome 27.0.1453.116 - url blank, tries to load as page url
- Firefox 22.0 - displays url values, but does not allow resources to load
- Safari 6.0.5 - displays url values, loads resources relative to page url