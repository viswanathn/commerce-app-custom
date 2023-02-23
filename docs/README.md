commerce-app-custom

# commerce-app-custom

## Table of contents

### Interfaces

- [Integration](interfaces/Integration.md)
- [Pagination](interfaces/Pagination.md)
- [ParameterDefinition](interfaces/ParameterDefinition.md)
- [Product](interfaces/Product.md)

### Type Aliases

- [Config](README.md#config)
- [DeleteFn](README.md#deletefn)
- [DisabledPredicateFn](README.md#disabledpredicatefn)
- [MakeCTAFn](README.md#makectafn)
- [MakeSaveBtnTextFn](README.md#makesavebtntextfn)
- [OpenDialogFn](README.md#opendialogfn)
- [ProductPreviewsFn](README.md#productpreviewsfn)
- [ProductsFn](README.md#productsfn)
- [RenderDialogFn](README.md#renderdialogfn)
- [ValidateParametersFn](README.md#validateparametersfn)

### Functions

- [renderSkuPicker](README.md#renderskupicker)
- [setup](README.md#setup)

## Type Aliases

### Config

Ƭ **Config**: `Record`<`string`, `any`\>

Object containing all information configured on the app configuration page.

___

### DeleteFn

Ƭ **DeleteFn**: (`index`: `number`) => `void`

#### Type declaration

▸ (`index`): `void`

##### Parameters

| Name | Type |
| :------ | :------ |
| `index` | `number` |

##### Returns

`void`

___

### DisabledPredicateFn

Ƭ **DisabledPredicateFn**: (`currentValue`: `string`[], `config`: [`Config`](README.md#config)) => `boolean`

#### Type declaration

▸ (`currentValue`, `config`): `boolean`

Function that should return true when the button should be disabled.

##### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `currentValue` | `string`[] | Currently selected skus |
| `config` | [`Config`](README.md#config) | App configuration |

##### Returns

`boolean`

true, if the button in the field location should be disabled. false, if the button should be enabled

___

### MakeCTAFn

Ƭ **MakeCTAFn**: (`fieldType`: `string`, `skuType?`: `string`) => `string`

#### Type declaration

▸ (`fieldType`, `skuType?`): `string`

Returns the text that is displayed on the button in the field location.

##### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `fieldType` | `string` | Type of the field the app is used for. |
| `skuType?` | `string` | SKU type of the current field. Undefined if only a single SKU type is supported by the app. |

##### Returns

`string`

Text that should be displayed on the button

___

### MakeSaveBtnTextFn

Ƭ **MakeSaveBtnTextFn**: (`selectedSKUs`: `string`[], `skuType?`: `string`) => `string`

#### Type declaration

▸ (`selectedSKUs`, `skuType?`): `string`

Returns the text that is used for confirming the dialog selection.

##### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `selectedSKUs` | `string`[] | An array of SKUs chosen. |
| `skuType?` | `string` | - |

##### Returns

`string`

Text that should be displayed on the button

___

### OpenDialogFn

Ƭ **OpenDialogFn**: (`sdk`: `FieldExtensionSDK`, `currentValue`: `string`[] \| `string`, `config`: [`Config`](README.md#config)) => `Promise`<`string`[]\>

#### Type declaration

▸ (`sdk`, `currentValue`, `config`): `Promise`<`string`[]\>

Function that gets called when app wants to open a dialog. Should return an updated list of skus as a Promise.

You probably want to call [`sdk.openCurrentApp`](https://www.contentful.com/developers/docs/extensibility/app-framework/sdk/#open-the-current-app-in-a-dialog).

**`Example`**

```javascript
async function openDialog(sdk, currentValue, config) {
  return await sdk.dialogs.openCurrentApp({
    parameters: { config, currentValue },
  });
}

```

##### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `sdk` | `FieldExtensionSDK` | [FieldExtensionSDK](https://www.contentful.com/developers/docs/extensibility/app-framework/sdk/) |
| `currentValue` | `string`[] \| `string` | List of currently selected akus |
| `config` | [`Config`](README.md#config) | App configuration |

##### Returns

`Promise`<`string`[]\>

Promise containing a list of selected skus

___

### ProductPreviewsFn

Ƭ **ProductPreviewsFn**: (`skus`: `string`[], `config`: [`Config`](README.md#config), `skuType?`: `string`) => `Promise`<[`Product`](interfaces/Product.md)[]\>

#### Type declaration

▸ (`skus`, `config`, `skuType?`): `Promise`<[`Product`](interfaces/Product.md)[]\>

Function that returns a list for a given list of skus. The returned value is used to render a product preview.

##### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `skus` | `string`[] | List of skus |
| `config` | [`Config`](README.md#config) | App configuration |
| `skuType?` | `string` | SKU type of the current field. Undefined if only a single SKU type is supported by the app. |

##### Returns

`Promise`<[`Product`](interfaces/Product.md)[]\>

List of Products which is used to render a preview.

___

### ProductsFn

Ƭ **ProductsFn**: (`search`: `string`, `pagination?`: `Partial`<[`Pagination`](interfaces/Pagination.md)\>) => `Promise`<`ProductsFnResponse`\>

#### Type declaration

▸ (`search`, `pagination?`): `Promise`<`ProductsFnResponse`\>

##### Parameters

| Name | Type |
| :------ | :------ |
| `search` | `string` |
| `pagination?` | `Partial`<[`Pagination`](interfaces/Pagination.md)\> |

##### Returns

`Promise`<`ProductsFnResponse`\>

___

### RenderDialogFn

Ƭ **RenderDialogFn**: (`sdk`: `DialogExtensionSDK`) => `void`

#### Type declaration

▸ (`sdk`): `void`

Function that gets called within the Iframe when the app is rendered in a dialog location.

**`Example`**

```javascript
function renderDialog(sdk) {
  const config = sdk.parameters.invocation;

  const container = document.createElement('div');
  container.innerHTML = `<iframe src="https://example.com/dam?folder=${config.folder}" width="400" height="650" style="border:none;"/>`;
  document.body.appendChild(container);
}
```

##### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `sdk` | `DialogExtensionSDK` | [DialogExtensionSDK](https://www.contentful.com/developers/docs/extensibility/app-framework/sdk/) |

##### Returns

`void`

___

### ValidateParametersFn

Ƭ **ValidateParametersFn**: (`parameters`: `Record`<`string`, `string`\>) => `string` \| ``null``

#### Type declaration

▸ (`parameters`): `string` \| ``null``

Custom code that validates installation parameters that is run before saving.

##### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `parameters` | `Record`<`string`, `string`\> | Object containg the entered parameters. |

##### Returns

`string` \| ``null``

`string` containing an error message. `null` if the parameters are valid.

## Functions

### renderSkuPicker

▸ **renderSkuPicker**(`elementId`, `«destructured»`): `void`

#### Parameters

| Name | Type |
| :------ | :------ |
| `elementId` | `string` |
| `«destructured»` | `Props` |

#### Returns

`void`

___

### setup

▸ **setup**(`integration`): `void`

#### Parameters

| Name | Type |
| :------ | :------ |
| `integration` | [`Integration`](interfaces/Integration.md) |

#### Returns

`void`
