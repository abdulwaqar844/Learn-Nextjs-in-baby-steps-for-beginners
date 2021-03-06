### Steps to Follow are 
*   **Download** your profile picture in `.jpg` format
*   Create an `images` directory inside of the `public` directory.
*   Save the picture as `profile.jpg` in the `public/images` directory.
*   The image size can be around 400px by 400px.

Create a components directory at root and create profile.js component and paste this code:
```javascript
import Image from "next/image";
const ProfileComponent = () => (
  <Image
    src="/images/profile.jpg" // Route of the image file
    height={144} // Desired size with correct aspect ratio
    width={144} // Desired size with correct aspect ratio
    alt="Your Name"
  />
);
export default ProfileComponent;
```
Import Profile in index.js and render at top of elements or simply copy this code and update index.js file.
```javascript
import Link from "next/link";
import Profile from "./../components/profile";
export default function Home() {
  return (
    <div>
      <Profile />
      Hello World.
      <Link href="/about">
        <a>About</a>
      </Link>
    </div>
  );
}
```
Assets
------

Next.js can serve **static assets**, like images,fonts  , `robots.txt` and Google Site Verification from  **the top-level `public` directory**. Files inside `public` can be referenced from the root of the application similar to `/pages`.

### Download Your Profile Picture

First, let's retrieve your profile picture.

*   **Download** your profile picture in `.jpg` format (or [use this file](https://github.com/vercel/next-learn/blob/master/basics/basics-final/public/images/profile.jpg)).
*   Create an `images` directory inside of the `public` directory.
*   Save the picture as `profile.jpg` in the `public/images` directory.
*   The image size can be around 400px by 400px.
*   You may remove the unused SVG logo file directly under the [`public` directory](/docs/basic-features/static-file-serving).

### Unoptimized Image

With regular HTML, you would add your profile picture as follows:

    <img src="/images/profile.jpg" alt="Your Name" />
    

However, this means you have to manually handle:

*   Ensuring your image is responsive on different screen sizes
*   Optimizing your images with a third-party tool or library
*   Only loading images when they enter the viewport

And more. Instead, Next.js provides an `Image` component out of the box to handle this for you.

### Image Component and Image Optimization

[`next/image`](/docs/api-reference/next/image) is an extension of the HTML `<img>` element, evolved for the modern web.

Next.js also has support for Image Optimization by default. This allows for resizing, optimizing, and serving images in modern formats like [WebP](https://developer.mozilla.org/en-US/docs/Web/Media/Formats/Image_types#webp) when the browser supports it. This avoids shipping large images to devices with a smaller viewport. It also allows Next.js to automatically adopt future image formats and serve them to browsers that support those formats.

Automatic Image Optimization works with any image source. Even if the image is hosted by an external data source, like a CMS, it can still be optimized.

### Using the Image Component

Instead of optimizing images at build time, Next.js optimizes images on-demand, as users request them. Unlike static site generators and static-only solutions, your build times aren't increased, whether shipping 10 images or 10 million images.

Images are lazy loaded by default. That means your page speed isn't penalized for images outside the viewport. Images load as they are scrolled into viewport.

Images are always rendered in such a way as to avoid [Cumulative Layout Shift](https://web.dev/cls/), a [Core Web Vital](https://web.dev/vitals/#core-web-vitals) that Google is going to [use in search ranking](https://webmasters.googleblog.com/2020/05/evaluating-page-experience.html).

Here's an example using [`next/image`](/docs/api-reference/next/image.md) to display our profile picture. The `height` and `width` props should be the desired rendering size, with an aspect ratio identical to the source image.


```javacript
import Image from "next/image";

const ProfileComponent = () => (
  <Image
    src="/images/profile.jpg" // Route of the image file
    height={144} // Desired size with correct aspect ratio
    width={144} // Desired size with correct aspect ratio
    alt="Your Name"
  />
);
export default ProfileComponent;

```
    

> To learn more about Automatic Image Optimization, check out the [documentation](/docs/basic-features/image-optimization).
> 
> To learn more about the `Image` component, check out the [API reference for `next/image`](/docs/api-reference/next/image).

**Quick Review**: What does `next/image` simplify for you?

Uploading & storing images Resizing & optimizing images Cropping & color correcting images

**Correct.** Good job!