# Responsive images and SVG images

Learn how to do the following:

- Use the `<picture>` element to create a responsive image with art direction.
- Use an `<img>` with `srcset` and `size` attributes to serve different image sizes for different screen widths.
- Load an SVG image with `<img>`.
- Use inline SVGs and create a `<symbol>` to easily reuse your inline SVG.

 ⚠️ This assignment builds on your _Semantic HTML and basic navigation_ assignment                                                                                                                                                                                                                                                                                                                                                                               |
| :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| After cloning this repo and opening it in VSCode, copy the following files and folder from your _Semantic HTML and basic navigation_ assignment into this repo.<br><br><ul><li>📄 index.html</li><li>📄 favicon.ico</li><li>📁images</li><li>📁about</li><li>📁contact</li></ul><br>**Make sure that you don't copy any other folders or files, including the `test` and `readme-assets` folders, the hidden `.git` and `.github` folders, and the `package.json` files** |

## :art: Add a hero image using `<picture>`

A hero image is a large banner image that is displayed at the top of a webpage and is the first image visitors see. The actual image in a hero images should not include text. We will learn how to add text on top of our hero image in a later assignment.

For this assignment, place your hero image either above or below the header on your main `index.html` page.

| 💡 Hero videos                                                                                      |
| :------------------------------------------------------------------------------------------------------ |
| _Hero videos are becoming popular, and we will learn how to create a hero video later in the semester_. |

A `<picture>` element allows for _art direction_, or different versions of images cropped to display best on different screen sizes and devices. Below is an example of images cropped to display on (from left to right) a laptop, a tablet, and a mobile phone.
![art-direction](readme-assets/art-direction.jpg)

For this assignment we will create three versions of images for laptops, tablets, and mobile devices. There are no "set" widths and heights to use, but for this assignment, assume

| Device | Max width | Suggested ratio |
| ------ | --------- | --------------- |
| laptop | `1920px`  | 16:9            |
| tablet | `768px`   | 4:3             |
| mobile | `380px`   | 1:1             |

As discussed in class, the widths and ratios are guides. You are welcome to use different ratios based on your own preferences. If you'd like a full screen hero image (100% of the width and height), don't try to force the sizing with HTML. After we learn CSS, you can use CSS to make the image fill the entire screen.

Finally, we will keep this assignment simple and assume the maximum screen width is `1920px`, and ignore pixel ratios (which on some devices are up to 4x). **Make sure none of your images are wider than `1920px`.** To see the pixel ratio of your computer or device, check out [mydevice.io](https://www.mydevice.io/).

### Steps to create your hero `<picture>` element

1. Find a free high-resolution image for your hero image. You can search [Unsplash](https://unsplash.com/) or [Pexels](https://www.pexels.com/). If you use your own image, make sure the image is at least `1920px` wide.
2. Use a photo editor, such as [befunky](https://www.befunky.com/create/), to crop and resize your image to display on all three screen sizes. Make sure the cropping is obvious; don't just resize the image.
3. Save your images in the `images` folder. In order for the auto-grader to detect that this is your hero image, begin the file name with `hero`. To make it easy for you to identify which image is which, append the width to the image file name. For example, in the images above, I used the file names
   - `hero-squirrel-1920w.jpg`
   - `hero-squirrel-768w.jpg`
   - `hero-squirrel-380w.jpg`
4. In your main `index.html` file, change the HTML to load your images (also delete the squirrel example images included in the repo). Here is the code included in the sample index.html:

   ```html
   <picture>
    <source media="(min-width: 769px)" srcset="images/hero-squirrel-1920w.jpg">
    <source media="(min-width: 381px)" srcset="images/hero-squirrel-768w.jpg">
    <source media="(max-width: 380px)" srcset="images/hero-squirrel-380w.jpg">
    <img src="images/hero-squirrel-768w.jpg" alt="brown squirrel on green grass lawn">
   </picture>
   ```

   Make sure to include a fallback `<img>` with descriptive alt text. Since the `<picture>` element is used for art direction, the source image dimensions will not be the same, so you should not use `<img>` `width` and `height` attributes as you would with single images.

   In the video below, "Dev Tools and `<picture>`," I explain what the `media` attribute communicates to the browser.

5. In order for the image to display properly, we need a little CSS. Load the `styles/main.css` in the document `<head>` on all three of your html files. Add this to your main `index.html` file:

   `<link rel="stylesheet" href="styles/main.css">`

   And add this to your subpages (notice the relative path to the styles folder):

   `<link rel="stylesheet" href="../styles/main.css">`

### Use Live Server and Dev Tools to make sure your images are loading properly

Before you open your webpage in Live Server, check the bottom left info bar on VS Code. You want to make sure you don't have any errors or warnings which should look like this:

![no errors or warnings](readme-assets/errors.png)

If you have errors or warnings, click on the icons to see what they are and fix them.

Once any problems are fixed, open Live Server and use the Dev Tools to make sure your images are loading properly.

| 🎥 WATCH: Dev Tools and `<picture>`                                                                                                                                                                                       |
| :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Watch this 7 minute [video on using Dev Tools with the `<picture>` element](https://youtu.be/2jkA83w1ibc) to learn how to use the Network tab in Dev Tools to check that your `<picture>` element images are downloading correctly |

## 🎨 On your About page, add an `<img>` with `srcset` and `size` attributes to serve different image sizes for different screen widths

While desktop computers can handle downloading large images, you don't want a user to waste bandwidth on a mobile device. You want to make sure that the image is downloaded at the right size for the device. This is where `<img>` with `srcset` and `size` attributes come in.

Now, unlike the `<picture>` element, `<img>` with `srcset` and `size` attributes are not art direction. They are used to serve different sizes of the same image. Also, unlike `<picture>`, `<img>` with `srcset` and `size` does not guarantee a certain image will display at a given screen width. If the browser has a larger image cached, it will choose that instead.

![srcset example](readme-assets/img-srcset.jpg)

Let's add an `<img>` with different image sizes to our `about/index.html` page.

1. Find a free high-resolution image for your About page image. You can search [Unsplash](https://unsplash.com/) or [Pexels](https://www.pexels.com/). Let's keep the max width of this image at 900px.
2. Use a photo editor, such as [befunky](https://www.befunky.com/create/), to crop your image if desired, and then resize your image to be 900px wide. Save this image in the `images` folder. For convenience, append "-900w" to the image file name.
3. Resize the same image to 600px wide and then 300px wide, appending the widths to the files names. Save these images in the `images` folder.
4. Open your `about/index.html` file in VS Code. If you were simply loading the 600px wide image, you'd use this markup:

   `<img src="../images/staring-squirrel-600w.jpg" alt="a brown squirrel on a black background" width="600" height="600">`

   but you would use your image file and a relevant `alt` attribute. Notice I've added the `width` and `height` attributes to the `<img>` element to match the intrinsic dimensions of the image.

5. Next, let's add the other images using the `srcset` attribute. List the path to all the images and then follow each path with a "width descriptor," which is the _intrinsic_ (actual) pixel width of the image (srcset can gets more complicated by accounting for screen pixel density, but we will keep this example as simple as possible). We added the width to the file name to help us keep the images separate, but the browser can't read that and needs you to let it know the width. Separate each path and width descriptor with a comma:

   ```html
   <img srcset="../images/staring-squirrel-300w.jpg 300w,
               ../images/staring-squirrel-600w.jpg 600w,
               ../images/staring-squirrel-900w.jpg 900w"
       src="../images/staring-squirrel-600w.jpg"
       alt="a brown squirrel on a black background" width="600" height="600">
   ```

6. Finally we need to add information to the `sizes` attribute. The sizes are relative to the browser viewport. The sizes will make more sense when you are able to use CSS to layout images.

   I added some CSS to force the image on the About page to always be 50% of the page width. We can let the browser know that instead of downloading an image that is the full width of the page, it should download an image that is half of the page width. Add the `sizes` attribute below to tell the browser the image will always be half the page width (or 50vw - vertical width). _We will learn more about this in the CSS lesson._

   ```html
   <img srcset="../images/staring-squirrel-300w.jpg 300w,
            ../images/staring-squirrel-600w.jpg 600w,
            ../images/staring-squirrel-900w.jpg 900w"
        sizes="50vw"
        src="../images/staring-squirrel-600w.jpg"
        alt="a brown squirrel on a black background" width="600" height="600">
   ```

   In this example, if your browser viewport is 1000px wide, the browser will look for an image that is at least 500px wide. It will download the 600px wide image.

   Open the Network tab in Firefox's Dev Tools and resize the window to see when the images download.

   Chrome handles image loading a little differently and is more likely to reuse a larger image in the cache. Try viewing the Network tab in Chrome to see the difference.

| 📖 Learn more about srcset and sizes                                                                                                                                                                                                                                                         |
| :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| This example was simply to introduce you to `srcset` and `sizes`. `sizes` can include media queries and account for high res displays like Apple's Retina display. Learn more at [MDN's The Image Embed element page](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/img#attr-srcset) |

<!-- TODO: more info here on waterfall -->
## ⏱️ Check image file sizes and load times

Images that take too long to download can impact SEO and user experience. Even if an image is resized to 2000px or less, the image file can still be too large and slow your page's load. There are no set rules for how large image files should be, but I recommend making sure they are less than 1MB, if possible.

You can check the size of your images and their loading time using the Network tab in Dev Tools. If any images seem to be loading too slowly, various utilities exist to further compress images. You can use a website like [TinyJPG](https://tinyjpg.com/) to compress your images.

## 💹 Add SVG images

### Add an SVG image to your contact page using `<img>`

SVG images can be loaded on a web page just like PNG and JPG files.

1. Find a free SVG image on a site such as [Icon Finder](https://www.iconfinder.com/search?q=form&price=free) to add to your Contact `index.html`.
2. Make sure that the image has an `.svg` extension and save the SVG image file in your `images` folder.
3. On your contact page, add an `<img>` element to load your SVG file. Use a relative path in the `src` attribute and don't forget to add an `alt` description.

### Add a simple inline SVG image to your main page using `<symbol>`

You can use the inline SVG you wrote for the [inline SVG learning task](https://codepen.io/lsburton/pen/yLXvxJq). It can be as simple as a circle, although many students create a "hamburger" menu icon to use for our mobile menu assignment at the end of the semester. The location of the SVG isn't important, as long as it is visible on the main `index.html`.

Refer to the assigned reading [SVG intro](https://codepen.io/lsburton/pen/ZEBYbXw?editors=1100) for more information on inline SVG and `<symbol>`.

### Use Live Server to make sure your images are displaying properly

Before you open your webpage in Live Server, check that you don't have any errors or warnings. If you have errors or warnings, fix them.

If everything looks good, then....

## :arrow_up: Use VS Code's Source Control (in the sidebar) to commit your changes and sync these changes to Github

### 🚀 Publish your web page on Github Pages

Open your repo on Github. Publish your site on GitHub pages.

### Enter your repo about information

In your main repo page edit the About section. Enter a description of your repo and add your Pages URL in the **Website** text field.

## Validate your HTML with validator.nu

Once your page is live, use the [validator.nu](https://validator.nu/) service to validate the HTML on all three of your web pages (main, contact, about). Select Show "outline" and "image report" then paste your page URL into the validator and click Check.

Check that each image has a valid alt attribute.

If you have any errors, fix them in VSCode, commit and sync, and then re-validate your page. Make sure to wait a few minutes for Github to generate the updated page.

## Pass automated tests

After you've ensured that your page has validated, open your repo in Github and check that you've passed the automated tests. Look at the top right of your repo header. If you have passed all the tests, you'll see a green check mark:

![passed tests](readme-assets/pass.png)

If you failed any tests, you will see a red X. Click on the X to see which test failed. Click on the failed test name for more details.

![failed tests](readme-assets/fail.png)

If you see a yellow dot, it means that the test is still running. Wait for the test to finish.

### Current automated tests

- HTML validation
- HTML proofer
- `<head>` should have a `<title>`
- `<head>` should have a `<meta>` description element
- all HTML files should contain an `<h1>`, and only one `<h1>`
- all HTML files should contain favicon information
- all index.html files must contain a `<header>`
- all `<header>` elements must contain a `<nav>` element
- menu items in header `<nav>` must be in an `<ul>`
- main index.html must contain a `<main>`
- `<main>` must contain two `<article>` elements
- each `<article>` must contain an `<h2>` and at least one `<p>`
- main index.html must contain an `<aside>`
- main index.html must contain a `<footer>`
- text in the `<aside>` must inside a `<p>`
- text in the `<footer>` must be inside a `<p>`
- image paths are all lowercase and contain no spaces
- images must be 1920px wide or less
- relative paths to images used, and images must be in the images directory
- images that aren't SVGs and images outside `<picture>` elements have the `<img>` `height` and `width` attributes set to the `src` image's intrinsic dimensions
- stylesheet `main.css` in `styles` folder is loaded on all pages using relative links
- main `index.html` contains a `<picture>` element
- `<picture>` element must contain three `<source>` elements with `media` and `srcset` attributes
- `<picture>` element must contain a fallback image
- about page includes an `<img>` element that uses `srcset` and `sizes` to load three versions of the same image with different widths
- contact page loads an SVG file with `<img>`
- main `index.html` includes a simple inline SVG image displayed using `<symbol>`

## Submit your repo URL to Learning Suite

When you are ready to have your assignment graded, submit your repo (not web page) URL to Learning Suite in the assignment comments.
