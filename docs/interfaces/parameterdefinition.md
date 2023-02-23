[commerce-app-custom](../README.md) / ParameterDefinition

# Interface: ParameterDefinition

Definition of app configuration parameters

## Table of contents

### Properties

- [default](ParameterDefinition.md#default)
- [description](ParameterDefinition.md#description)
- [id](ParameterDefinition.md#id)
- [name](ParameterDefinition.md#name)
- [required](ParameterDefinition.md#required)
- [type](ParameterDefinition.md#type)

## Properties

### default

• `Optional` **default**: `any`

Default value

___

### description

• **description**: `string`

Short description/explanation

___

### id

• **id**: `string`

Unique id. Used as key in Config object.

___

### name

• **name**: `string`

Name / Label

___

### required

• **required**: `boolean`

Whether it is possible without providing a value.

___

### type

• **type**: ``"Symbol"`` \| ``"Number"`` \| ``"List"``

Parameter type
- Symbol: Text
- List: List of texts
- Number: Integer
