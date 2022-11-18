# Values.yaml Explained

## global

<details open>
<summary>Show more</summary>
Available keys:

```yaml
global:
  nameOverride: ""
  annotations: {}
  labels: {}
```

### nameOverride

<details>

Sets an override for the suffix of the full name.
(Applies to current chart and all sub-charts)

- Type: `string`
- Helm template: ❌

Example: Values.yaml

```yaml
global:
  nameOverride: something
```

Appends `something` to:

- Deployment
  - metadata.name
  - spec.template.spec.containers[].name

Sets `something` to:

- Deployment
  - metadata.app
  - metadata.app.kubernetes.io/name
  - spec.selector.matchLabels.app
  - spec.selector.matchLabels.app.kubernetes.io/name
  - spec.template.metadata.annotations.app
  - spec.template.metadata.annotations.app
  - spec.template.metadata.labels.app.kubernetes.io/name
  - spec.template.metadata.labels.app.kubernetes.io/name

</details>

### annotations

<details>

Sets additional global annotations.

- Type: `dict`
- Helm Template: ✅
  - On values only

Example:

Values.yaml

```yaml
global:
  annotations:
    key1: value
    key2: "{{ .Values.some.key }}"
```

Sets all `key: value` pairs to:

- Deployment
  - metadata.annotations

</details>

### labels

<details>

Set additional global labels. Helm templates can be used.

- Type: `dict`
- Helm Template: ✅
  - On values only

Example:

Values.yaml

```yaml
global:
  labels:
    key1: value
    key2: "{{ .Values.some.key }}"
```

Sets all `key: value` pairs to:

- Deployment
  - metadata.labels

</details>
</details>