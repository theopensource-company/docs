# Partials

Partials are Doctave's way of reusing content and creating custom components. All partials in a Doctave project live under the `_partials` directory.

Doctave supports a variant of the [Liquid Template Language](https://shopify.github.io/liquid/). Use can use Liquid's `include` function to invoke any partial you put in the `_partials` directory.

## Reusing content

Let's say we have a product description that we want to reuse in multiple places. These are the steps you'd take to create a reusable partial for it:

1. Create a file `_partials/product-description.md`
2. Write your Markdown formatter description in this filedescri
3. Include it in your documentation with the following snippet:<br /> `{% raw %}{% include "_partials/product-description.md" %}{% endraw %}`

Your description should appear wherever you invoked the `include` function!

## Custom HTML components

You can also create custom HTML components and style them with [custom CSS](https://docs.doctave.com/customization/custom-css-fonts#custom-css).

This project has one custom HTML component, which you have also encountered: `_partials/callout.html`. Here is is in action:

{% capture content %}
**Greetings!** Hello!
{% endcapture %}
{% include "_partials/callout.html" content: content, kind: "info" %}

It's a div with some custom styling, tha can accept some Markdown content. There are a few variants for it:

{% capture content %}
Success
{% endcapture %}
{% include "_partials/callout.html" content: content, kind: "success" %}

{% capture content %}
Warning
{% endcapture %}
{% include "_partials/callout.html" content: content, kind: "warning" %}

{% capture content %}
Error
{% endcapture %}
{% include "_partials/callout.html" content: content, kind: "error" %}

This callout can be invoked with the following syntax:

{% raw %}

```
{% capture content %}
**Greetings!** Hello!
{% endcapture %}
{% include "_partials/callout.html" content: content, kind: "info" %}
```

{% endraw %}

Here we are calling the `include` function again, but we also use a `capture` block to capture the Markdown content we want to pass into the partial. Finally, we pass the `kind` attribute which defines the color of the callout.

If you look at `_partials/callout.html`, it's a very small template:

{% raw %}
```html
<div class="callout callout-{{ kind }}">
  {{ content }}
</div>
```
{% endraw %}

Note the 2 Liquid variables: `kind` and `content`. The former sets a specific CSS class for the callout, the latter injects the actual content into the partial.

