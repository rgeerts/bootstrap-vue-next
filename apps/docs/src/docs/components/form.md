# Form

<PageHeader>

BootstrapVueNext form component and helper components that optionally support inline form styles and
validation states. Pair them up with other BootstrapVueNext form control components for an easy
customized, and responsive, layout with a consistent look and feel.

</PageHeader>

## Introduction to forms and controls

Be sure to use an appropriate `type` on all inputs (e.g., `email` for email address or `number` for
numerical information) to take advantage of newer input controls like email verification, number
selection, and more.

Here is a quick example to demonstrate BootstrapVueNext's form styles. Keep reading for documentation on
supported components, form layout, and more.

<<< DEMO ./demo/FormOverview.vue

## Inline form

Bootstrap 5 has dropped form-specific layout classes for the grid system. See the
[Bootstrap 5 Changelog](https://getbootstrap.com/docs/5.3/migration/#forms).

To create horizontal forms with the grid add the `.row` class to form groups and use the `.col-_-_` classes
to specify the width of your labels and controls. Be sure to add `.col-form-label` to your `<label>`s as well,
so they’re vertically centered with their associated form controls.

You may need to manually address the width and alignment of individual form controls with
[spacing utilities](/docs/reference/spacing-classes) (as shown below). Lastly, be sure to always
include a `<label>` with each form control, even if you need to hide it from non-screenreader
visitors with class `.visually-hidden`.

<<< DEMO ./demo/FormInline.vue#template{vue-html}

Custom form controls and selects are also supported.

<<< DEMO ./demo/FormInlineSelect.vue

## Floating Labels

Wrap a `BFormInput`, `BFormTextarea`, or `BFormSelect` in a `BFormFloatingLable` to enable floating labesl. A `placeholder`
is required on each input in order to make the Bootstrap 5 `css` work correctly.

<<< DEMO ./demo/FormFloatingLabels.vue#template{vue-html}

Floating labels work correclty for disable state and readonly states. In addition to styled textual inputs, floating labels
also work for plaintext inputs, textareas, input groups and selects.
See the [Bootstrap 5 documentation](https://getbootstrap.com/docs/5.3/forms/floating-labels) for more details.

The `floating` attribute on the `BForm` component only applies to single form controls like this:

<<< DEMO ./demo/FormSingleFloat.vue#template{vue-html}

## Accessibility

Ensure that all form controls have an appropriate accessible name so that their purpose can be conveyed to users of
assistive technologies. The simplest way to achieve this is to use a `<label>` element, or—in the case of buttons—to
include sufficiently descriptive text as part of the `<button>...</button>` content.

For situations where it’s not possible to include a visible `<label>` or appropriate text content, there are
alternative ways of still providing an accessible name, such as:

- `<label>` elements hidden using the `.visually-hidden` class
- Pointing to an existing element that can act as a label using `aria-labelledby`
- Providing a title attribute
- Explicitly setting the accessible name on an element using aria-label

If none of these are present, assistive technologies may resort to using the placeholder attribute as a fallback for
the accessible name on `<input>` and `<textarea>` elements. The examples in this section provide a few suggested, case-specific approaches.

While using visually hidden content (`.visually-hidden`, `aria-label`, and even placeholder content, which
disappears once a form field has content) will benefit assistive technology users, a lack of visible label text may
still be problematic for certain users. Some form of visible label is generally the best approach,
both for accessibility and usability.

## Related form control and layout components

See also:

- [`BFormInput`](/docs/components/form-input) Textual and text-like inputs
- [`BFormTextarea`](/docs/components/form-textarea) Text area inputs
- [`BFormSelect`](/docs/components/form-select) Select input
- [`BFormRadio`](/docs/components/form-radio) Radio Inputs
- [`BFormCheckbox`](/docs/components/form-checkbox) Checkbox Inputs
- [`BFormFile`](/docs/components/form-file) File Input
- [`BFormSpinbutton`](/docs/components/form-spinbutton) Numerical range spinbutton input
- [`BFormTags`](/docs/components/form-tags) Customizable tag input
- `BFormRating` Star rating custom form input and display (<NotYetImplemented/>)
- [`BButton`](/docs/components/button) Buttons
- [`BFormGroup`](/docs/components/form-group) Form Input wrapper to generate form-groups that
  support labels, help text and feedback
- [`BInputGroup`](/docs/components/input-group) Form Inputs with add-ons
- [`BFormRow`](/docs/components/grid-system) Create grid rows and columns with tighter margins
  (available via the [Layout and grid components](/docs/components/grid-system))

## Form helper components

The following helper components are available with the `Form` plugin:

- `BFormText` Help text blocks for inputs
- `BFormInvalidFeedback` Invalid feedback text blocks for input `invalid` states
- `BFormValidFeedback` Valid feedback text blocks for input `valid` states
- `BFormDatalist` Easily create a `<datalist>` for use with `BFormInput` or plain `<input>`

### Form text helper

Display a block of help text below an input with the `BFormText` helper component. text is
displayed with a muted color and slightly smaller font-size.

::: info Tip
Help text should be explicitly associated with the form control it relates to using the
`aria-describedby` attribute. This will ensure that assistive technologies, such as screen readers,
will announce this help text when the user focuses or enters the control.
:::

<<< DEMO ./demo/FormTextHelper.vue#template{vue-html}

### Feedback helpers

The `BFormValidFeedback` and `BFormInvalidFeedback` helper components will display
feedback (based on input state) as a block of colored text. They rely on being placed after an input
(sibling) and will show based on the browser native validation state of the input. To force them to
show, set the prop `force-show` to `true`, or bind the controls `state` to the `state` prop of the
feedback helper, or set the `was-validated` class on a parent element (such as a form). See the
[**Validation**](#validation) section below for additional details.

Use the optional Boolean prop `tooltip` to change the display from a block to a static tooltip
style. The feedback will typically appear below the form control. When this mode is enabled, it is
important that the parent container have a `position: relative:` css style (or `position-relative`
class). Note that tooltip style feedback may, since its positioning is static, obscure other inputs,
labels, etc.

:::info NOTE
Some form controls, such as [`BFormRadio`](/docs/components/form-radio#contextual-states) and
[`BFormCheckbox`](/docs/components/form-checkbox#contextual-states) have wrapper elements which will prevent
the feedback text from automatically showing (as the feedback component is not a direct sibling of the form
control's input). Use the feedback component's `state` prop (bound to the state of the form control)
or the `force-show` prop to display the feedback.
:::

<<< DEMO ./demo/FormFeedbackHelper.vue

### Datalist helper

For browsers that support
[`<datalist>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/datalist) elements, the
`<BFormDatalist>` helper component will allow you to quickly create a `<datalist>` and child
`<option>` elements via an array passed to the `options` prop.

You may also manually provide `<option>` elements inside `<BFormDatalist>`. They will appear below
any `<option>` elements generated from the `options` prop. Or use the `first` slot to place options
above the generated options.

<<< DEMO ./demo/FormDataHelper.vue

See also:

- [`<BFormInput> datalist`](/docs/components/form-input#datalist-support) for datalist usage.
- [`<BFormSelect>` `options` prop](/docs/components/form-select#options-property) docs for details
  on the formats and helper props associated with `options`. Note that `<BFormDatalist>` only support
  a flat list of `BFormSelectOptions`, unlike `<BFormSelect>` which support a heirarchy of
  `BFormSelectOption` and `BFormSelectOptionGroup`.

## Validation

Disable browser native HTML5 validation by setting the `novalidate` prop to true on `BForm`.

Set the `validated` prop, on `BForm`, to `true` to add the Bootstrap v5 `.was-validated` class to
the form to trigger validation states.

All form controls support a `state` prop, which can be used to set the form control into one
of three contextual states:

- `false` (denotes invalid state) is great for when there is a blocking or required field. A user
  must fill in this field properly to submit the form
- `true` (denotes valid state) is ideal for situations when you have per-field validation throughout
  a form and want to encourage a user through the rest of the fields
- `null` Displays no validation state (neither valid nor invalid)

Refer to the
[Bootstrap v5 Form Validation Documentation](https://getbootstrap.com/docs/5.3/forms/validation/)
for details on the Bootstrap v5 validation states.

<ComponentReference :data="data" />

<script setup lang="ts">
import {data} from '../../data/components/form.data'
</script>
