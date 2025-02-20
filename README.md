# Wonderstudios

/!\ The code won’t be displayed because it’s a private project.

## The idea

We’ve all seen those splendid Apple website when new products come out. Yeah the ones with all the amazing scroll animations. Well, that’s the goal of this project. The founders of Wonderstudios asked me to find a way to create a lookalike animation for the agency website.

/!\ The site is not live anymore

## The method

To recreate this animation, I have a few ideas.

### Video control on scroll

The easiest one to test is to control a video time stamp on scroll. I’ll just put a video in absolute without the video controls. Then I just need to add a Javascript onScroll listener to change the timestamp of the video. The idea is great but it doesn’t work. The scrollY value that we get doesn’t necessarily match the video time. What I mean by that is each video has a different frame rate, because of that the value that we get with the scrollY won’t correspond to any frame of the video. That explains the laggy experience when we do this method.

### Frame by frame

To prevent the sync issue that we get with the video we can export it frame by frame. It will increase the weight of the video so let’s keep it in mind when we do the export. I exported the frames with the same name and the number of the frame in the name (img_0001.jpg for example). How can I play a frame by frame video in HTML? Well, it’s impossible. Let’s create an img tag and add the first frame in the src. I’ll change the number in the src with the scrollY and, it just works!

## Some issues

### Performances

It is amazing to recreate the Apple scroll animation but something feels wrong. The Apple websites are way better. Let’s find a way to improve performances. The first thing to change is the method I used. Yeah, It works but sometimes we need to destroy to rebuild a better one. We will keep the frame by frame idea thought. Instead of settings the src of the img tag that forces the reload of the DOM everytime it changes. I’ll just create a canvas and set the image in there.

It’s already way better but I can do more. Instead of changing the src onScroll, I’ll add a requestAnimationFrame in between. requestAnimationFrame will start on the next frame, so I don’t create any latency in-between page rebuilding. By doing so, the framerate is constant and more pleasant for the eyes.

Lastly, the image weight. There is a lot of images, so I need to be careful on the quality. I limited the total weight to 7Mb. I need to load different images on mobile too.

### Libraries

The animation works fine in native Javascript but to add more than just a video on the website I had to use ScrollMagic and gsap. They are easy to use and well optimized, so it wasn’t a real issue, I just like to create the whole thing in native. 
