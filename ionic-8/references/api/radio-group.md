# Radio Group Component

Source: https://ionicframework.com/docs/api/radio-group

Sections: Interfaces · Properties · Events · Methods · CSS Shadow Parts · CSS Custom Properties · Slots

A radio group is a container for a group of [radios](https://ionicframework.com/docs/api/radio). It allows a user to select at most one radio button from a set. Checking one radio button that belongs to a radio group unchecks any previous checked radio button within the same group. For example usage of the radio group, see the [radio](https://ionicframework.com/docs/api/radio) documentation.

## Interfaces

### RadioGroupChangeEventDetail

```typescript
interface RadioGroupChangeEventDetail<T = any> {
  value: T;
}
```

### RadioGroupCustomEvent

While not required, this interface can be used in place of the `CustomEvent` interface for stronger typing with Ionic events emitted from this component.

```typescript
interface RadioGroupCustomEvent<T = any> extends CustomEvent {
  detail: RadioGroupChangeEventDetail<T>;
  target: HTMLIonRadioGroupElement;
}
```

## Properties

### allowEmptySelection

|     |     |
| --- | --- |
| **Description** | If `true`, the radios can be deselected. |
| **Attribute** | `allow-empty-selection` |
| **Type** | `boolean` |
| **Default** | `false` |

### compareWith

|     |     |
| --- | --- |
| **Description** | This property allows developers to specify a custom function or property name for comparing objects when determining the selected option in the ion-radio-group. When not specified, the default behavior will use strict equality (===) for comparison. |
| **Attribute** | `compare-with` |
| **Type** | `((currentValue: any, compareValue: any) => boolean) ｜ null ｜ string ｜ undefined` |
| **Default** | `undefined` |

### errorText

|     |     |
| --- | --- |
| **Description** | The error text to display at the top of the radio group. |
| **Attribute** | `error-text` |
| **Type** | `string ｜ undefined` |
| **Default** | `undefined` |

### helperText

|     |     |
| --- | --- |
| **Description** | The helper text to display at the top of the radio group. |
| **Attribute** | `helper-text` |
| **Type** | `string ｜ undefined` |
| **Default** | `undefined` |

### name

|     |     |
| --- | --- |
| **Description** | The name of the control, which is submitted with the form data. |
| **Attribute** | `name` |
| **Type** | `string` |
| **Default** | `this.inputId` |

### value

|     |     |
| --- | --- |
| **Description** | the value of the radio group. |
| **Attribute** | `value` |
| **Type** | `any` |
| **Default** | `undefined` |

## Events

| Name | Description | Bubbles |
| --- | --- | --- |
| `ionChange` | Emitted when the value has changed.<br>This event will not emit when programmatically setting the `value` property. | `true` |

## Methods

No public methods available for this component.

## CSS Shadow Parts

No CSS shadow parts available for this component.

## CSS Custom Properties

No CSS custom properties available for this component.

## Slots

No slots available for this component.
