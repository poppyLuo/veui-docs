# OptionGroup <small>选择组</small>

:::tip
`Option` is required to be used within [`Select`](./select), [`Dropdown`](./dropdown) or other `OptionGroup`, and can be used with [`Option`](./option).
:::

## Demos

See [the demos of `Select`](./select#demos) or [the demos of `Dropdown`](./dropdown#demos).

## API

### Props

| Name | Type | Default | Description |
| -- | -- | -- | -- |
| `label` | `string` | The descriptive label of the option group. |
| `options` | `Array<Object>` | `[]` | [^options] |
| `position` | `string` | `inline` | [^position] |
| `overlay-class` | `string|Array|Object=` | - | See the `overlay-class` prop of [`Overlay`](./overlay). |

^^^options
The list of options with the option type being `{label, value, disabled, ...}`.

+++Properties
| Name | Type | Description |
| -- | -- | -- |
| `label` | `string` | The descriptive label of the option. |
| `value` | `*` | The value of the option. |
| `disabled` | `boolean=` | Whether the option is disabled. |
+++
^^^

^^^position
The way to display child options.

+++Enum values
| Value | Description |
| -- | -- |
| `inline` | Displays child options inline. |
| `popup` | Displays child options in a separate popup menu. |
+++
^^^

### Slots

| Name | Description |
| -- | -- |
| `default` | The content of the options dropdown. Can be used to place `Option`s or `OptionGroups`s when the `options` prop is not specified. |
| `label` | [^scoped-slot-label] |
| `group-label` | [^scoped-slot-group-label] |
| `option-label` | [^scoped-slot-option-label] |
| `option` | [^scoped-slot-option] |

^^^scoped-slot-label
The label of the option group. Displays the `label` prop by default.

+++Scope properties
| Name | Type | Description |
| -- | -- | -- |
| `label` | `string` | The descriptive label of the option group. |
| `disabled` | `boolean=` | Whether the option group is disabled. |
+++
^^^

^^^scoped-slot-group-label
The label text of each option group (option with child `options`). Displays the `label` of the option by default.

+++Scope properties
| Name | Type | Description |
| -- | -- | -- |
| `label` | `string` | The descriptive label of the option group. |
| `disabled` | `boolean=` | Whether the option group is disabled. |
+++

Additionally, custom properties in current option, apart from the listed ones, will also be passes into the scope object via `v-bind`.
^^^

^^^scoped-slot-option-label
The label text of each option (option without child `options`). Displays the `label` of the option by default.

+++Scope properties
| Name | Type | Description |
| -- | -- | -- |
| `label` | `string` | The descriptive label of the option. |
| `value` | `*` | The value of the option. |
| `selected` | `boolean` | Whether the the option is selected. |
| `disabled` | `boolean=` | Whether the option is disabled. |
+++

Additionally, custom properties in current option, apart from the listed ones, will also be passes into the scope object via `v-bind`.
^^^

^^^scoped-slot-option
The entire content area of each option (option without child `options`). Displays the default content of `Options` component by default.

+++Scope properties
| Name | Type | Description |
| -- | -- | -- |
| `label` | `string` | The descriptive label of the option. |
| `value` | `*` | The value of the option. |
| `selected` | `boolean` | Whether the the option is selected. |
| `disabled` | `boolean=` | Whether the option is disabled. |
+++

Additionally, custom properties in current option, apart from the listed ones, will also be passes into the scope object via `v-bind`.
^^^

### Icons

| Name | Description |
| -- | -- |
| `expandable` | Expandable options. |
