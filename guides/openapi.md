# Adding OpenAPI specs

{% capture content %}
📖 You can read our official documentation about OpenAPI documentation [here](https://docs.doctave.com/contents/openapi-specs).
{% endcapture %}
{% include "_partials/callout.html" content: content, kind: "info" %}

Doctave can generate documentation from your OpenAPI specifications. In fact, this demo project includes an example OpenAPI specification!

## Include your OpenAPI spec file

To render your OpenAPI spec in Doctave, first you need to include your OpenAPI specification in your project directory.

This demo has an example project at `openapi-example.yaml`. You can replace it with your own specification to see how we render your API references.

After this, specify the file in the `doctave.yaml` settings file:

```yaml
open_api:
  - spec_file: openapi-example.yaml
    uri_prefix: /api/reference
```

## Include the reference in your navigation

Next, you'll want to add links to your API docs to a `navigation.yaml` file so your users can find them.

In this demo, we've added the API documentation under the _API Reference_ tab, which is in the `api` folder. The tab has its own navigation under `api/navigation.yaml` with the following section:

```yaml
- heading: Example API
  items:
    - open_api_spec: openapi-example.yaml
```

This will generate links for each tag and operation.

## Done 🚀

You should now see links to your OpenAPI tags in the left side navigation!
