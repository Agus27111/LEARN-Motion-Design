https://www.youtube.com/watch?v=vqXLGX0szIQ&t=18319s

# Exercise Videos (exercise 1 & 2)

    1. we can add video from youtube with embed
    2. we can add video from internal device
        to make video lower brightness we can add trick with :before style in the Hero section (exercise 2)
        MP4 haved big data so we can change to WebM (but not support at some old browwser)
        we can use HandBrake aplication. (download it!)
        to make it still load we store both of them MP4 and WebM ( take a look at exercise 2) => browser will load the thiny file first.

# exercises CSS Transition

    1. Exercise 3
        > we can add transition when hover the button
        > we add CSS transition in button parents elemet
        *CSS*
            transition-property: backround-color;
            transition-duration: 0.4s;
            transition-timing-function: ease-in-out;
            transition-delay: 2s;

        *or we can simplify with*
            transition: all 0.4s ease-in-out 2s;
            but its not good for the application, because maybe we want something different in other property if changed.

        *Good application is like ... *
            transition: backround-color 0.4s ease-in-out, color 0.4s ease-out;

    2. Exercise 4
        We leaern to transition a Navbar with drop menu
            1. Firstly we need to add transition to All children element at navbar with
                 nav ul a,
                .has-submenu::after,
                .has-submenu ul,
                .has-submenu ul a,
                .has-submenu ul a::after {
                    transition-duration: var(--def-transition-duration);
                    transition-timing-function: ease-in-out;
                    }
            2. we add specify from the drop menu like this.
                nav ul a {
                    transition-property: color;
                }
                .has-submenu::after {
                    transition-property: opacity;
                }

                /* START effect to moving from left to right */
                .has-submenu ul {
                    display: block;
                    opacity: 0;
                    visibility: hidden;
                    transform: translateX(-1rem);
                    transition-property: opacity, visibility, transform;
                }
                .has-submenu:hover ul {
                    opacity: 1;
                    visibility: visible;
                    transform: translateX(0);
                }
                /* END effect to moving from left to right */

                /* START to add Transition to chil element from drop down menu */
                .has-submenu ul a {
                    transition-property: backround-color, padding;
                }
                .has-submenu ul a::after {
                    transition-property: opacity;
                }
                /* End of children element from drop down menu */
    3. exercises 5 and 6
        > not all CSS properties support transition like for ex background.
        > not all transition need the same duration
        > Transition are not limited to hover states, for examplle they can be triggered when an element receive a certain class. (like exercise 6)

# exercises CSS animation

    * first we need to define the keyframes (describing step by step)
    Normal syntax
        @keyframe animationName {
            from {
                ....
            }
            to {
                ....
            }
        }

    Short Syntax
    .box {
        animation: duration | easing-function |
            delay | iteration-count | direction |
            fill-mode | play-state | name;
    }

    example
    . box {
        animation: 2s ease-in-out 1s 2 moveRight;
    }

    * second we can apply the animation what we want
    alternate as the direction causes animation between forward and reverse.


    // LOADING ANIMATION
     ^^ Loading Animation  (CSS spinner)
     --> Spinkit by Tobias Ahlin
     --> Lottie FIles animation

    1. exercise 8
    learn loading animation

    2. Exercise 9
    learn loading animation with SVG text

    3. exercise 10
    learn loading animation in button

    4. exercises 11
    add lotti files animation to project with just copyy the embed.

    5. exercises 12-14
    i cant follow because i dont have a SVG file.

    in this steps the lecture animation the SVG and thats awesome!

    6. Exercises 15
    play with GSAP
    still dont have a SVG huhu...

    7.exercise 16
    typewriter with GSAP
        add CDN GSAP
        $create script for the typewriter
        //main timeline with GSAP
            let mainTimeline = gsap.timeline({
                repeat: -1,
                 });

        //for each word, create a new timeline, use the Text plugin then append that timeline to the main one to make typewriter

            words.forEach((word) => {
                let textTimeline = gsap.timeline({
                repeat: 1,
                yoyo: true,
                repeatDelay: 4,
                });
                textTimeline.to("#typewriter", {
                text: word,
                duration: 1,
                onUpdate: () => {
                    cursorTimeline.restart();
                    cursorTimeline.pause();
                },
                onComplete: () => {
                    cursorTimeline.play();
                },
                });
                mainTimeline.add(textTimeline);
            });

        $Create blinking cursor
        //make blinking cursor
            let cursorTimeline = gsap.timeline({
                repeat: -1,
                repeatDelay: 0.8,
                });

            cursorTimeline.to("#cursor", {
                opacity: 1,
                duration: 0,
            }).to("#cursor", {
                opacity: 0,
                duration: 0,
                delay: 0.8,
            });

        $ Create drop icon bouncing with CSS
            #our-work svg {
                animation: 5s ease-in-out infinite point-down;
            }

            @keyframes point-down {
                0%,
                10%,
                40%,
                100% {
                transform: translate3d(0, 0, 0);
                }
                25% {
                transform: translate3d(0, 1rem, 0);
                }
            }
            to make perfect we can take a look at cubic-bezier.com to replace ease-in with cubic-bezier(1,.06,.24,1.32)


    8.exercise 17
    Magneto button when hover

    9. exercise 18
    scrollong animation
        1. CSS scroll-timeline
        2. Intersection Observer
    we create with GSAP and lenis

    10. exercises 19
    i dont have the SVG
    paralax have some SVG pieces to make it works
