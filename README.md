# Schotteriser: a no-code JavaScript algorithmic art generator

A single page JavaScript algorithmic art generator inspired by the work of Vera Molnár, Georg Nees et al. No signup/login, no build steps and no code required - open the HTML file and play with it.

* Why is it a single file?

It doesn't need to be anything more complex, it's portable and doesn't need hosting or building.

* Why doesn't it do _______?

If you've got a cool feature idea, fork the repo or send me a pull request.

* Schotteriser?

Named after Schotter, one of the early algorithmic art pieces and the one that inspired this workflow. 

* Did you vibe code it?

One ten line function for generating SVG markup and some CSS suggestions came from ChatGPT, I wrote the rest

# How to use it 

The Schotteriser has four pipelines which can be used to generate procedural patterns.

**Generators** draw the specified shape arranged in a parameterised pattern. Output from all the Generators in a pipeline is combined for the following steps, but each pipeline works independently of the others.

**Transforms** can then be used to modify the geometry. Transforms are applied in order from top to bottom on a per-shape basis to all the geometry in a pipeline. The magnitude of the effect is linearly interpolated between the minimum and maximum values (From and To) depending on the shape's position based on the measure chosen.

🎲 *Random effect*: the magnitude of the transform will be randomly chosen between 0 and the amount determined by the shape's position. 

↔️ *Random sign* effect: the effect of the transform will be randomly (p=0.5) made negative. 

📊 *Quantise*: if the number of steps is set to 2 or greater, the effect of the transform will be quantised to that number of steps including the minimum and maxium value. (e.g. A rotate transform between 0 and 90° with three steps will rotate by 0, 45° or 90°). Set steps to 0 for no quantisation

Finally, **colour Rules** can be used to assign colour to the geometry. Each colour ruleset contains groups of rules which work as a sum of products: if _all_ the rules in _any_ group of a set apply to a given shape, it will be assigned the set's colour. Colour rulesets are also applied in order from top to bottom