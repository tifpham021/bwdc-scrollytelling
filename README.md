# KWK Scrollytelling template

This template is a starting point / example of how to create a scrollytelling piece using Svelte and Highcharts! 

## Demo
See a live demo of the page [here]((https://tifpham021.github.io/bwdc-scrollytelling/))!

## Recommended IDE Setup

[VS Code](https://code.visualstudio.com/) + [Svelte](https://marketplace.visualstudio.com/items?itemName=svelte.svelte-vscode).

## How to clone the repo
On this repo's homepage in GitHub, click the `Use this template` button. Select the option to create a new repository. This will create a new repo under your GitHub account.

Navigate to your new copy of this template in your GitHub profile. 

Clone your new repo locally and `cd` into it. 

Run `npm install` and then `npm run dev` to spin up the project locally. Then, start making changes! You can use this repo as a starting point for your own final project or simply as an example. 

## Credit
Images came from [here](https://blush.design/) and [here](https://www.freepik.com/).
Help from AI:
1) Used to make the fade in fade out of content
  import { fade } from 'svelte/transition';

    let visible1 = false;
    let visible2 = false;
    let visible3 = false;

    function inView(node, callback) {
        const observer = new IntersectionObserver(
        ([entry]) => {
            callback(entry.isIntersecting);
        },
        { threshold: 0.5 }
        );

        observer.observe(node);

        return {
        destroy() {
            observer.unobserve(node);
        }
        };
    }

2) Used to make the "show more" buttons that reveal more info when user presses them
   use:inView={(val) => (visible2 = val)}
            transition:fade
            class:invisible={!visible2}
   
   let visibleCount = 1;

    function showMore() {
        if (visibleCount < featuresScene1.length) {
        visibleCount += 1;
        }
    }
Repo created using vite (`npm create vite@6`)
