# Coastal walks

This is an interactive application built in 18 hours. Showcasing 5 coastal walks in the South of England, this responsive application takes the user through a 'long-read' interactive journey.

You can also see it hosted (note: only from being built locally) here: https://guileless-concha-9325f6.netlify.app/

From ideation, to UX/UI wireframes, creating assets, to hi-fi designs, to MVP this application presents this content to a mobile-first audience, aiming to make it engaging and captivating through animation.

## Code & Styling

Here are some of the way this application utilizes code and styling
- This application uses SASS for styling. Ideally most classes would be abstracted away in different styling folders and applied directly to HTML elements for clean code.
- At 4k break points the html root size changes to bump up the visual size.
- Global variables are used for colours, incorporating the guardian's core colour
- A component was made that utilizes the Intersection Observer and can be wrapped around any element and pass in a name that becomes an animation class that is applied and removed when the element os scrolled past.
- An example of how to animate svg line paths on stickied elements is used on the first map line, this process could be abstracted to a function and applied to all map line paths in the article
- All additional assets are SVGs that have been created for the purpose of this coding task
- Each map is styled off of a real route and is a link to the South West coastal walk path from the link provided at the end of the article

## v 2.0

With more time, these would be great to expand on
- Merging time space and data together all on one screen: the article contents are split up according to the time of the day you would encounter the establishments along the path. Each walk then becomes a story, e.g. at 2pm stop at this pub for a sunday roast, at 4pm stop at this cafe for an ice-cream, at 7pm catch the sunset in this hidden cove, etc.
- Hero animation turns into a sunset as you scroll down
- GIFs or short videos are utilised as the hero image for each walk to give more movement
- Audio is utilised that can be played, as the walks are the star of the show the audio should match the walk audioscape
- At the end of the route path the total walk in km is displayed
- There is a custom marker/walker/feet that follows the route path down the page
- Elements of the story pop out on the route path
- You can navigate through the story of the walk through clicking on the route path, e.g. beginning is start at 7am 0km day 1 and the end is 5pm 22km day 2
- User can select what kind of route they prefer at the beginning which changes the order the walks are displayed in
- User can save the walks for later
- Users can add their own pins along the route and see themselves in the story
- Animations would have custom cubic beziers for transitions
- Joyful and playful user interactions added, e.g. for more information link a button with micro interaction or walks love hearted to be saved and at the end of the article you can download a PDF itinerary with links to affiliated establishments
- Hover animations added for desktop use, subtle increases in size, changes in colour and interactivity 
- Styling would be split out into seperate files with reusable classes to apply to HTML
- Functions would be split out into utils
- This method of viewing scrolling images would be extracted into a resusable component
- The route path following the screen would be made into a component using the library GSAP
- A reduced motion global variable that stops all animations
- Increasing the sticky title smallest font to 16px/1rem

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Compile and Minify for Production

```sh
npm run build
```

### Lint with [ESLint](https://eslint.org/)

```sh
npm run lint
```
