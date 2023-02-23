[commerce-app-custom](../README.md) / Integration

# Interface: Integration

## Table of contents

### Properties

- [color](Integration.md#color)
- [description](Integration.md#description)
- [fetchProductPreviews](Integration.md#fetchproductpreviews)
- [isDisabled](Integration.md#isdisabled)
- [logo](Integration.md#logo)
- [makeCTA](Integration.md#makecta)
- [name](Integration.md#name)
- [openDialog](Integration.md#opendialog)
- [parameterDefinitions](Integration.md#parameterdefinitions)
- [renderDialog](Integration.md#renderdialog)
- [skuTypes](Integration.md#skutypes)
- [validateParameters](Integration.md#validateparameters)

## Properties

### color

• **color**: `string`

The app's primary color

___

### description

• **description**: `string`

Short description of the app

___

### fetchProductPreviews

• **fetchProductPreviews**: [`ProductPreviewsFn`](../README.md#productpreviewsfn)

Function that returns a list for a given list of skus. The returned value is used to render a product preview.

**`Param`**

List of skus

**`Param`**

App configuration

___

### isDisabled

• **isDisabled**: [`DisabledPredicateFn`](../README.md#disabledpredicatefn)

Function that should return true when the button should be disabled.

**`Param`**

Currently selected assets

**`Param`**

App configuration

___

### logo

• **logo**: `string`

Path to the app's logo

___

### makeCTA

• **makeCTA**: [`MakeCTAFn`](../README.md#makectafn)

Returns the text that is displayed on the button in the field location.

**`Param`**

Type of the field the app is used for.

___

### name

• **name**: `string`

Name of the app

___

### openDialog

• **openDialog**: [`OpenDialogFn`](../README.md#opendialogfn)

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

**`Param`**

[FieldExtensionSDK](https://www.contentful.com/developers/docs/extensibility/app-framework/sdk/)

**`Param`**

Array of currently selected skus

**`Param`**

App configuration

___

### parameterDefinitions

• **parameterDefinitions**: [`ParameterDefinition`](ParameterDefinition.md)[]

Parameter definition which can be customized on the app configuration page and used in the callback functions.

___

### renderDialog

• **renderDialog**: [`RenderDialogFn`](../README.md#renderdialogfn)

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

**`Param`**

[DialogExtensionSDK](https://www.contentful.com/developers/docs/extensibility/app-framework/sdk/)

___

### skuTypes

• `Optional` **skuTypes**: { `default?`: `boolean` ; `id`: `string` ; `name`: `string`  }[]

If your app supports multiple sku types (for example - product, product variant, category...) you can provide a list here.
This configuration will be stored under the skuTypes key in your installation parameters.

___

### validateParameters

• **validateParameters**: [`ValidateParametersFn`](../README.md#validateparametersfn)

Custom code that validates installation parameters that is run before saving.

**`Param`**

Object containg the entered parameters.
