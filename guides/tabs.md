# Tabs and subtabs

Tabs and subtabs can be used to split your documentation into logical sections. Each section will have its own navigation and its content lives in its own subdirectory.

{% capture content %}
📖 You can read our official documentation about tabs [here](https://docs.doctave.com/contents/tabs-and-subtabs).
{% endcapture %}
{% include "_partials/callout.html" content: content, kind: "info" %}

This demo project has 3 tabs:

- A ["Home"](/) section that acts as your landing page
- A ["Guides"](/guides) section for... guides
- An ["API Reference"](/api) section for documentation generated from an OpenAPI specification

## How tabs work

![tabs and subtabs screenshot](/_assets/tabs-and-subtabs.png)

The basics of how tabs and subtabs work is as follows:

- Tabs show up at the top of your project
- Each tab **must** have one or more subtabs
- Each subtab is mapped to a specific subdirectory in your project s and has its own `navigation.yaml`
- If there is only one tab, or there is no `structure.yaml` file, no tabs are shown
- If a tab has only one subtab (like in this demo), the subtabs section is not shown for that tab

## Defining tabs

Tabs are defined in your `structure.yaml` file. Let's take a look at this project's example:

```yaml
tabs:
  - label: Home
    subtabs:
      - label: Placeholder
        path: /
  - label: Guides
    subtabs:
      - label: Placeholder
        path: /guides/
  - label: API Reference
    subtabs:
      - label: Placeholder
        path: /api/
```

Under the `tabs:` key, we define a list of 3 tabs, each with a label, and subtabs.

As mention above, each tab has to have at least one subtab. When there is only one subtab, the subtab selector in the navigation is hidden.

**Try adding a new subtab to the "Guides" tab to see what happens!**

```yaml
- label: Guides
  subtabs:
    - label: Placeholder
      path: /guides/
    - label: New Subtab # <== New subtab
      path: /guides/
```
