# \<kwc-building-listing\>

## Purpose
To display a list of step-by-step build challenges. This component also accepts an array of challenge ids to mark as completed.

## Properties
* challenges (Object): List of challenges to be displayed.
* completedChallenges (Array): List of challenge ids to mark as completed

The element properties are have the shape (specified using [json schema](https://spacetelescope.github.io/understanding-json-schema/)):


```js
// challenges
{
    type: `array`,
    items:{
        type: 'object',
        properties: {
            title: {
                type: 'string'
            },
            slug: {
                type: 'string'
            },
            image: {
                type: 'string',
                format: 'url'
            }
        },
        required: [ 'title', 'slug', `image` ]
    }
}
// e.g
[{
    "title": "Chatterbox",
    "slug": "pixel_talking_mouth",
    "image": "https://www.tonymacx86.com/data/avatars/l/1342/1342909.jpg"
},{
    "title": "The Aurora Borealis",
    "slug": "pixel_aurora_borealis",
    "image": "https://rfclipart.com/image//arctic-glacier-landscape.jpg"
}]

// completedChallenges
{
    type: `array`,
    items:{
        type: 'string'
    }
}
// e.g
[
    "pixel_talking_mouth",
    "pixel_dice"
]
```
## Events
This component will fire a custom event `open-kano-code` intitated by a click or tap event on any of the challenge cards in the displayed list. The event is passed the following detail:
```js
{
    type: 'object',
    properties: {
        type: {
            type: 'string'
        },
        challengeId: {
            type: 'string'
        }
    }
}
```
The challengeId can then be accessed in any listener implementation on the event detail property.
```js
addEventListener('open-kano-code', function(e){
    console.log(e.detail);
}
// e.g. {"type": "challenge", "challengeId: "pixel_talking_mouth"}
```

## Installation
* Clone this repository.
* Run `bower i`
* Make sure you have the [Polymer CLI](https://www.npmjs.com/package/polymer-cli) installed. Then run `polymer serve` to serve your element locally.

## Running Tests

```
$ polymer test --skip-plugin junit-reporter
```
