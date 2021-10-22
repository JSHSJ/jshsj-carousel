# Carousel

Ever needed a carousel?

You probably don't. But you client wants one.

Anyways. This is supposed to make it less painful and it aids you with a bit of accessibility, while still giving you quite a bit of control.

It's build with @github/catalyst, which I think is fantastic.

## Setup

Install it. There should be an UMD and an ES version, plus a style sheet for very basic styles.

You then need to build the markup yourself. This is how it works and it's the way I prefer as it gives you quite a bit of control and understanding.

Props are passed through data-attributes. The following exist on the element itself:

- `data-items-to-display`: How many items should be displayed per "slide"
- `data-items-to-slide`: How many items should be slided per click.

That's it. You then need to provide the following elements:

- A container with `data-target="jshsj-carousel.container`, which is the container element around everything.
- Another slide container with `data-target="jshsj-carousel.slideContainer"`. This hold your slides.
- Another item container with `data-target="jshsj-carousel.itemContainer"`. This is the last container. I swear.
- However many items you want. Give them `data-targets="jshsj-carousel.items` and they will become your slides. Can be images / text or whatever you desire. Should work. If it breaks, it's probably a style issue.

Thats the carousel markup done.

Now you might want: **Buttons to control**.

Use whatever element you want, but give it `data-action="click:jshsj-carousel#previousSlide"` for "previous" and `data-action="click:jshsj-carousel#nextSlide"` for "next". I really recommend buttons, because that's what they were made for.

The last thing is truely optional, but might be nice: **Indicators**.

You'll need:

- Another container element. Huh. Give it `data-targets="jshsj-carousel.dots`.
- This is new: A template with `data-target="jshsj-carousel.dotTemplate"` that hold your "dot"-markup. There should be buttons (they're clickable), each having `data-targets="jshsj-carousel.dots"`. They will get an `-active` class, when they match the shown slides. Clicking them will go to the corresponding slide.

> The Template is the only "magic" I'll provide. It will create matching dots for each slide in correspondence to `data-items-to-display` and `data-items-to-slide`.

That's it. I hope it works.

## Example

This is a fully working example. You need to add a few more styles for the dots and buttons (or leave them out).

```html
<jshsj-carousel data-items-to-display="1" data-items-to-slide="1">
  <div class="" data-target="jshsj-carousel.container">
    <div class="" data-target="jshsj-carousel.slideContainer">
      <div class="" data-target="jshsj-carousel.itemContainer">
        <div class="jshsj-Carousel-item" data-targets="jshsj-carousel.items">
          <img src="https://picsum.photos/400/400?1" />
        </div>
        <div class="jshsj-Carousel-item" data-targets="jshsj-carousel.items">
          <img src="https://picsum.photos/400/400?1" />
        </div>
        <div class="jshsj-Carousel-item" data-targets="jshsj-carousel.items">
          <img src="https://picsum.photos/400/400?1" />
        </div>
        <div class="jshsj-Carousel-item" data-targets="jshsj-carousel.items">
          <img src="https://picsum.photos/400/400?1" />
        </div>
        <div class="jshsj-Carousel-item" data-targets="jshsj-carousel.items">
          <img src="https://picsum.photos/400/400?1" />
        </div>
      </div>
    </div>
    <div class="jshsj-Carousel-arrowContainer">
      <button
        class="CTA-button -icon -secondary"
        data-action="click:jshsj-carousel#previousSlide"
      >
        <svg
          class="icon -left"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
          viewBox="0 0 43 51"
        >
          <path
            d="m3 4 37 30M3 47.5l37-30"
            stroke="currentColor"
            stroke-width="8"
          />
        </svg>
      </button>
      <button
        class="CTA-button -icon -secondary"
        data-action="click:jshsj-carousel#nextSlide"
      >
        <svg
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
          viewBox="0 0 43 51"
          class="icon"
        >
          <path
            d="m3 4 37 30M3 47.5l37-30"
            stroke="currentColor"
            stroke-width="8"
          />
        </svg>
      </button>
    </div>
    <div
      class="jshsj-Carousel-dotsContainer -centered-bottom"
      data-target="jshsj-carousel.dotContainer"
    ></div>
    <template data-target="jshsj-carousel.dotTemplate">
      <button
        class="jshsj-Carousel-dot"
        data-targets="jshsj-carousel.dots"
      ></button>
    </template>
  </div>
</jshsj-carousel>
```
