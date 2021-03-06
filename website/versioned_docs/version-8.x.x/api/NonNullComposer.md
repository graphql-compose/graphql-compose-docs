---
id: version-8.x.x-NonNullComposer
title: NonNullComposer
custom_edit_url: https://github.com/graphql-compose/graphql-compose/blob/master/src/NonNullComposer.d.ts
original_id: NonNullComposer
---

<!-- 
🛑🛑🛑
DO NOT EDIT THIS FILE!
IT WAS AUTO-GENERATED FROM d.ts FILE
🛑🛑🛑
If you want to make changes in this file, please do it via
https://github.com/graphql-compose/graphql-compose/blob/master/src/NonNullComposer.d.ts
-->

## Getters

### List

```js
List: ListComposer<NonNullComposer<T>>;
```

Get Type wrapped in List modifier

```js
const UserTC = schemaComposer.createObjectTC(`type User { name: String }`);
schemaComposer.Query.addFields({
  users1: { type: UserTC.List }, // in SDL: users1: [User]
  users2: { type: UserTC.NonNull.List }, // in SDL: users2: [User!]
  users3: { type: UserTC.NonNull.List.NonNull } // in SDL: users2: [User!]!
});
```

### NonNull

```js
NonNull: NonNullComposer<T>;
```

Get Type wrapped in NonNull modifier

```js
const UserTC = schemaComposer.createObjectTC(`type User { name: String }`);
schemaComposer.Query.addFields({
  users1: { type: UserTC.List }, // in SDL: users1: [User]
  users2: { type: UserTC.NonNull.List }, // in SDL: users2: [User!]!
  users3: { type: UserTC.NonNull.List.NonNull } // in SDL: users2: [User!]!
});
```

## Properties

### ofType

```js
ofType: T;
```

## Methods

### getType()

```js
getType(): GraphQLNonNull<any>
```

### getTypeName()

```js
getTypeName(): string
```

### getUnwrappedTC()

```js
getUnwrappedTC(): NamedTypeComposer<any>
```

### getTypePlural()

```js
getTypePlural(): ListComposer<NonNullComposer<T>>
```

### getTypeNonNull()

```js
getTypeNonNull(): NonNullComposer<T>
```

### cloneTo()

```js
cloneTo(
  anotherSchemaComposer: SchemaComposer<any>,
  cloneMap: Map<any, any>
): NonNullComposer<AnyTypeComposer<any>>
```

Clone this type to another SchemaComposer.
Also will be cloned all wrapped types.
