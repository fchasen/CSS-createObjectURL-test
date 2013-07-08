CSS-createObjectURL-test
========================

CSS stylesheets loaded from objectURLs contain blank url() rules if original url is relative

1. Create a stylesheet link with a objectUrl created from a blob as the href  
2. Once sheet has loaded, inspect document.styleSheets
3. Rules containing relative url() links will display as empty

Rules with urls should display as url('path/to/file") but it has been changed to blank url()
Without a reference to the original url path there is no way to update it to work with the objectUrl
