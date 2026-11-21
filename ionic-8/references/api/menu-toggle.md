# Menu Toggle Component

Source: https://ionicframework.com/docs/api/menu-toggle

Sections: Properties · Events · Methods · CSS Shadow Parts · CSS Custom Properties · Slots

[shadow](https://ionicframework.com/docs/reference/glossary#shadow)

The Menu Toggle component can be used to toggle a menu open or closed.

Menu toggles are only visible when the selected menu is enabled. If the menu is disabled or it's being presented as a split pane, the menu toggle will be hidden. To always display the menu toggle, the `autoHide` property can be set to `false`.

See the [menu](https://ionicframework.com/docs/api/menu#menu-toggle) documentation for more information.

## Properties

### autoHide

|     |     |
| --- | --- |
| **Description** | Automatically hides the content when the corresponding menu is not active.<br>By default, it's `true`. Change it to `false` in order to keep `ion-menu-toggle` always visible regardless the state of the menu. |
| **Attribute** | `auto-hide` |
| **Type** | `boolean` |
| **Default** | `true` |

### menu

|     |     |
| --- | --- |
| **Description** | Optional property that maps to a Menu's `menuId` prop. Can also be `start` or `end` for the menu side. This is used to find the correct menu to toggle.<br>If this property is not used, `ion-menu-toggle` will toggle the first menu that is active. |
| **Attribute** | `menu` |
| **Type** | `string ｜ undefined` |
| **Default** | `undefined` |

## Events

No events available for this component.

## Methods

No public methods available for this component.

## CSS Shadow Parts

No CSS shadow parts available for this component.

## CSS Custom Properties

No CSS custom properties available for this component.

## Slots

| Name | Description |
| --- | --- |
| \`\` | Content is placed inside the toggle to act as the click target. |
