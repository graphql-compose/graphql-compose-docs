---
id: version-8.x.x-ObjectTypeComposer
title: ObjectTypeComposer
custom_edit_url: https://github.com/graphql-compose/graphql-compose/blob/master/src/ObjectTypeComposer.d.ts
original_id: ObjectTypeComposer
---

<!-- 
🛑🛑🛑
DO NOT EDIT THIS FILE!
IT WAS AUTO-GENERATED FROM d.ts FILE
🛑🛑🛑
If you want to make changes in this file, please do it via
https://github.com/graphql-compose/graphql-compose/blob/master/src/ObjectTypeComposer.d.ts
-->

Main class that gets `GraphQLObjectType` and provide ability to change them.

## Static methods

### static create()

```js
static create<TSrc = any, TCtx = any>(
  typeDef: ObjectTypeComposerDefinition<TSrc, TCtx>,
  schemaComposer: SchemaComposer<TCtx>
): ObjectTypeComposer<TSrc, TCtx>
```

Create `ObjectTypeComposer` with adding it by name to the `SchemaComposer`.

### static createTemp()

```js
static createTemp<TSrc = any, TCtx = any>(
  typeDef: ObjectTypeComposerDefinition<TSrc, TCtx>,
  schemaComposer: SchemaComposer<TCtx>
): ObjectTypeComposer<TSrc, TCtx>
```

Create `ObjectTypeComposer` without adding it to the `SchemaComposer`.
This method may be useful in plugins, when you need to create type temporary.

## Getters

### List

```js
List: ListComposer<ObjectTypeComposer<TSource, TContext>>;
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
NonNull: NonNullComposer<ObjectTypeComposer<TSource, TContext>>;
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

### schemaComposer

```js
schemaComposer: SchemaComposer<TContext>;
```

## Field methods

### getFields()

```js
getFields(): ObjectTypeComposerFieldConfigMap<TSource, TContext>
```

### getFieldNames()

```js
getFieldNames(): string[]
```

### getField()

```js
getField<TArgs = any>(
  fieldName: string
): ObjectTypeComposerFieldConfig<TSource, TContext, TArgs>
```

### hasField()

```js
hasField(
  fieldName: string
): boolean
```

### setFields()

```js
setFields(
  fields: ObjectTypeComposerFieldConfigMapDefinition<TSource, TContext>
): this
```

### setField()

```js
setField<TArgs = any>(
  fieldName: string,
  fieldConfig: ObjectTypeComposerFieldConfigDefinition<TSource, TContext, TArgs>
): this
```

### addFields()

```js
addFields(
  newFields: ObjectTypeComposerFieldConfigMapDefinition<TSource, TContext>
): this
```

Add new fields or replace existed in a GraphQL type

### addNestedFields()

```js
addNestedFields(
  newFields: ObjectTypeComposerFieldConfigMapDefinition<TSource, TContext>
): this
```

Add new fields or replace existed (where field name may have dots)

### removeField()

```js
removeField(
  fieldNameOrArray: string | string[]
): this
```

Remove fields from type by name or array of names.
You also may pass name in dot-notation, in such case will be removed nested field.

```js
removeField('field1'); // remove 1 field
removeField(['field1', 'field2']); // remove 2 fields
removeField('field1.subField1'); // remove 1 nested field
```

### removeOtherFields()

```js
removeOtherFields(
  fieldNameOrArray: string | string[]
): this
```

### reorderFields()

```js
reorderFields(
  names: string[]
): this
```

### extendField()

```js
extendField<TArgs = any>(
  fieldName: string,
  partialFieldConfig: Partial<ObjectTypeComposerFieldConfigAsObjectDefinition<TSource, TContext, TArgs>>
): this
```

### getFieldConfig()

```js
getFieldConfig(
  fieldName: string
): GraphQLFieldConfig<TSource, TContext>
```

### getFieldType()

```js
getFieldType(
  fieldName: string
): GraphQLOutputType
```

### getFieldTypeName()

```js
getFieldTypeName(
  fieldName: string
): string
```

### getFieldTC()

```js
getFieldTC(
  fieldName: string
): ComposeNamedOutputType<TContext>
```

Automatically unwrap from List, NonNull, ThunkComposer
It's important! Cause greatly helps to modify fields types in a real code
without manual unwrap writing.

If you need to work with wrappers, you may use the following code:
   - `TC.getField().type` // returns real wrapped TypeComposer
   - `TC.isFieldNonNull()` // checks is field NonNull or not
   - `TC.makeFieldNonNull()` // for wrapping in NonNullComposer
   - `TC.makeFieldNullable()` // for unwrapping from NonNullComposer
   - `TC.isFieldPlural()` // checks is field wrapped in ListComposer or not
   - `TC.makeFieldPlural()` // for wrapping in ListComposer
   - `TC.makeFieldNonPlural()` // for unwrapping from ListComposer

### getFieldOTC()

```js
getFieldOTC(
  fieldName: string
): ObjectTypeComposer<TSource, TContext>
```

Alias for `getFieldTC()` but returns statically checked ObjectTypeComposer.
If field have other type then error will be thrown.

### isFieldNonNull()

```js
isFieldNonNull(
  fieldName: string
): boolean
```

### makeFieldNonNull()

```js
makeFieldNonNull(
  fieldNameOrArray: string | string[]
): this
```

### makeFieldNullable()

```js
makeFieldNullable(
  fieldNameOrArray: string | string[]
): this
```

### isFieldPlural()

```js
isFieldPlural(
  fieldName: string
): boolean
```

### makeFieldPlural()

```js
makeFieldPlural(
  fieldNameOrArray: string | string[]
): this
```

### makeFieldNonPlural()

```js
makeFieldNonPlural(
  fieldNameOrArray: string | string[]
): this
```

### deprecateFields()

```js
deprecateFields(
  fields: {
      [fieldName: string]: string;
  } | string[] | string
): this
```

## Field Args methods

### getFieldArgs()

```js
getFieldArgs<TArgs = any>(
  fieldName: string
): ObjectTypeComposerArgumentConfigMap<TArgs>
```

### getFieldArgNames()

```js
getFieldArgNames(
  fieldName: string
): string[]
```

### hasFieldArg()

```js
hasFieldArg(
  fieldName: string,
  argName: string
): boolean
```

### getFieldArg()

```js
getFieldArg(
  fieldName: string,
  argName: string
): ObjectTypeComposerArgumentConfig
```

### getFieldArgType()

```js
getFieldArgType(
  fieldName: string,
  argName: string
): GraphQLInputType
```

### getFieldArgTypeName()

```js
getFieldArgTypeName(
  fieldName: string,
  argName: string
): string
```

### getFieldArgTC()

```js
getFieldArgTC(
  fieldName: string,
  argName: string
): ComposeNamedInputType<TContext>
```

Automatically unwrap from List, NonNull, ThunkComposer
It's important! Cause greatly helps to modify args types in a real code
without manual unwrap writing.

If you need to work with wrappers, you may use the following code:
    `isFieldArgPlural()` – checks is arg wrapped in ListComposer or not
    `makeFieldArgPlural()` – for arg wrapping in ListComposer
    `makeFieldArgNonPlural()` – for arg unwrapping from ListComposer
    `isFieldArgNonNull()` – checks is arg wrapped in NonNullComposer or not
    `makeFieldArgNonNull()` – for arg wrapping in NonNullComposer
    `makeFieldArgNullable()` – for arg unwrapping from NonNullComposer

### getFieldArgITC()

```js
getFieldArgITC(
  fieldName: string,
  argName: string
): InputTypeComposer<TContext>
```

Alias for `getFieldArgTC()` but returns statically checked InputTypeComposer.
If field have other type then error will be thrown.

### setFieldArgs()

```js
setFieldArgs(
  fieldName: string,
  args: ObjectTypeComposerArgumentConfigMapDefinition<any>
): this
```

### addFieldArgs()

```js
addFieldArgs(
  fieldName: string,
  newArgs: ObjectTypeComposerArgumentConfigMapDefinition<any>
): this
```

### setFieldArg()

```js
setFieldArg(
  fieldName: string,
  argName: string,
  argConfig: ObjectTypeComposerArgumentConfigDefinition
): this
```

### removeFieldArg()

```js
removeFieldArg(
  fieldName: string,
  argNameOrArray: string | string[]
): this
```

### removeFieldOtherArgs()

```js
removeFieldOtherArgs(
  fieldName: string,
  argNameOrArray: string | string[]
): this
```

### isFieldArgPlural()

```js
isFieldArgPlural(
  fieldName: string,
  argName: string
): boolean
```

### makeFieldArgPlural()

```js
makeFieldArgPlural(
  fieldName: string,
  argNameOrArray: string | string[]
): this
```

### makeFieldArgNonPlural()

```js
makeFieldArgNonPlural(
  fieldName: string,
  argNameOrArray: string | string[]
): this
```

### isFieldArgNonNull()

```js
isFieldArgNonNull(
  fieldName: string,
  argName: string
): boolean
```

### makeFieldArgNonNull()

```js
makeFieldArgNonNull(
  fieldName: string,
  argNameOrArray: string | string[]
): this
```

### makeFieldArgNullable()

```js
makeFieldArgNullable(
  fieldName: string,
  argNameOrArray: string | string[]
): this
```

## Type methods

### getType()

```js
getType(): GraphQLObjectType
```

### getTypePlural()

```js
getTypePlural(): ListComposer<ObjectTypeComposer<TSource, TContext>>
```

### getTypeNonNull()

```js
getTypeNonNull(): NonNullComposer<ObjectTypeComposer<TSource, TContext>>
```

### getTypeName()

```js
getTypeName(): string
```

### setTypeName()

```js
setTypeName(
  name: string
): this
```

### getDescription()

```js
getDescription(): string
```

### setDescription()

```js
setDescription(
  description: string
): this
```

### clone()

```js
clone(
  newTypeNameOrTC: string | ObjectTypeComposer<any, any>
): ObjectTypeComposer<TSource, TContext>
```

You may clone this type with a new provided name as string.
Or you may provide a new TypeComposer which will get all cloned
settings from this type.

### cloneTo()

```js
cloneTo(
  anotherSchemaComposer: SchemaComposer<any>,
  cloneMap: Map<any, any>
): ObjectTypeComposer<any, any>
```

Clone this type to another SchemaComposer.
Also will be cloned all sub-types.

### getIsTypeOf()

```js
getIsTypeOf(): GraphQLIsTypeOfFn<TSource, TContext> | undefined | null
```

### setIsTypeOf()

```js
setIsTypeOf(
  fn: GraphQLIsTypeOfFn<any, any> | null | undefined
): this
```

### merge()

```js
merge(
  type: GraphQLObjectType | GraphQLInterfaceType | ObjectTypeComposer<any, any> | InterfaceTypeComposer<any, any>
): this
```

Merge fields and interfaces from provided `GraphQLObjectType`, or `ObjectTypeComposer`.
Also you may provide `GraphQLInterfaceType` or `InterfaceTypeComposer` for adding fields.

## InputType methods

### getInputType()

```js
getInputType(): GraphQLInputObjectType
```

### hasInputTypeComposer()

```js
hasInputTypeComposer(): boolean
```

### setInputTypeComposer()

```js
setInputTypeComposer(
  itc: InputTypeComposer<TContext>
): this
```

### getInputTypeComposer()

```js
getInputTypeComposer(
  opts: ToInputTypeOpts
): InputTypeComposer<TContext>
```

### getITC()

```js
getITC(
  opts: ToInputTypeOpts
): InputTypeComposer<TContext>
```

### removeInputTypeComposer()

```js
removeInputTypeComposer(): this
```

## Resolver methods

### getResolvers()

```js
getResolvers(): Map<string, Resolver<any, TContext, any>>
```

### hasResolver()

```js
hasResolver(
  name: string
): boolean
```

Returns existed Resolver by name.

Resolver may be additionally wrapped by middlewares. Eg:

```js
async function authMiddleware(resolve, source, args, context, info) {
  if (somehowCheckAuthInContext(context)) {
    return resolve(source, args, context, info);
  }
  throw new Error('You must be authorized');
}

schemaComposer.Query.addFields({
  userById: UserTC.getResolver('findById', [authMiddleware]),
  userByIds: UserTC.getResolver('findByIds', [authMiddleware])
});
```

### getResolver()

```js
getResolver<TArgs = any>(
  name: string,
  middlewares: Array<ResolverMiddleware<TSource, TContext, TArgs>>
): Resolver<any, TContext, TArgs>
```

### setResolver()

```js
setResolver(
  name: string,
  resolver: Resolver<any, TContext>
): this
```

### addResolver()

```js
addResolver(
  opts: Resolver<any, TContext> | ResolverDefinition<any, TContext>
): this
```

### removeResolver()

```js
removeResolver(
  resolverName: string
): this
```

### wrapResolver()

```js
wrapResolver(
  resolverName: string,
  cbResolver: ResolverWrapCb<any, TSource, TContext>
): this
```

### wrapResolverAs()

```js
wrapResolverAs(
  resolverName: string,
  fromResolverName: string,
  cbResolver: ResolverWrapCb<any, TSource, TContext>
): this
```

### wrapResolverResolve()

```js
wrapResolverResolve(
  resolverName: string,
  cbNextRp: ResolverNextRpCb<any, TContext>
): this
```

## Interface methods

### getInterfaces()

```js
getInterfaces(): Array<InterfaceTypeComposerThunked<TSource, TContext>>
```

### getInterfacesTypes()

```js
getInterfacesTypes(): Array<GraphQLInterfaceType>
```

### setInterfaces()

```js
setInterfaces(
  interfaces: ReadonlyArray<InterfaceTypeComposerDefinition<any, TContext>>
): this
```

### hasInterface()

```js
hasInterface(
  iface: InterfaceTypeComposerDefinition<any, TContext>
): boolean
```

### addInterface()

```js
addInterface(
  iface: InterfaceTypeComposerDefinition<any, TContext> | InterfaceTypeComposerThunked<any, TContext>
): this
```

### addInterfaces()

```js
addInterfaces(
  ifaces: ReadonlyArray<InterfaceTypeComposerDefinition<any, TContext> | InterfaceTypeComposerThunked<any, TContext>>
): this
```

### removeInterface()

```js
removeInterface(
  iface: InterfaceTypeComposerDefinition<any, TContext>
): this
```

## Extensions methods

### getExtensions()

```js
getExtensions(): Extensions
```

### setExtensions()

```js
setExtensions(
  extensions: Extensions
): this
```

### extendExtensions()

```js
extendExtensions(
  extensions: Extensions
): this
```

### clearExtensions()

```js
clearExtensions(): this
```

### getExtension()

```js
getExtension(
  extensionName: string
): unknown
```

### hasExtension()

```js
hasExtension(
  extensionName: string
): boolean
```

### setExtension()

```js
setExtension(
  extensionName: string,
  value: unknown
): this
```

### removeExtension()

```js
removeExtension(
  extensionName: string
): this
```

### getFieldExtensions()

```js
getFieldExtensions(
  fieldName: string
): Extensions
```

### setFieldExtensions()

```js
setFieldExtensions(
  fieldName: string,
  extensions: Extensions
): this
```

### extendFieldExtensions()

```js
extendFieldExtensions(
  fieldName: string,
  extensions: Extensions
): this
```

### clearFieldExtensions()

```js
clearFieldExtensions(
  fieldName: string
): this
```

### getFieldExtension()

```js
getFieldExtension(
  fieldName: string,
  extensionName: string
): unknown
```

### hasFieldExtension()

```js
hasFieldExtension(
  fieldName: string,
  extensionName: string
): boolean
```

### setFieldExtension()

```js
setFieldExtension(
  fieldName: string,
  extensionName: string,
  value: unknown
): this
```

### removeFieldExtension()

```js
removeFieldExtension(
  fieldName: string,
  extensionName: string
): this
```

### getFieldArgExtensions()

```js
getFieldArgExtensions(
  fieldName: string,
  argName: string
): Extensions
```

### setFieldArgExtensions()

```js
setFieldArgExtensions(
  fieldName: string,
  argName: string,
  extensions: Extensions
): this
```

### extendFieldArgExtensions()

```js
extendFieldArgExtensions(
  fieldName: string,
  argName: string,
  extensions: Extensions
): this
```

### clearFieldArgExtensions()

```js
clearFieldArgExtensions(
  fieldName: string,
  argName: string
): this
```

### getFieldArgExtension()

```js
getFieldArgExtension(
  fieldName: string,
  argName: string,
  extensionName: string
): unknown
```

### hasFieldArgExtension()

```js
hasFieldArgExtension(
  fieldName: string,
  argName: string,
  extensionName: string
): boolean
```

### setFieldArgExtension()

```js
setFieldArgExtension(
  fieldName: string,
  argName: string,
  extensionName: string,
  value: unknown
): this
```

### removeFieldArgExtension()

```js
removeFieldArgExtension(
  fieldName: string,
  argName: string,
  extensionName: string
): this
```

## Directive methods

Directive methods are useful if you declare your schemas via SDL.
Users who actively use `graphql-tools` can open new abilities for writing
your own directive handlers.

If you create your schemas via config objects, then probably you
no need in `directives`. Instead directives better to use `extensions`.

### getDirectives()

```js
getDirectives(): Array<ExtensionsDirective>
```

### setDirectives()

```js
setDirectives(
  directives: Array<ExtensionsDirective>
): this
```

### getDirectiveNames()

```js
getDirectiveNames(): string[]
```

### getDirectiveByName()

```js
getDirectiveByName(
  directiveName: string
): DirectiveArgs | undefined
```

### getDirectiveById()

```js
getDirectiveById(
  idx: number
): DirectiveArgs | undefined
```

### getFieldDirectives()

```js
getFieldDirectives(
  fieldName: string
): Array<ExtensionsDirective>
```

### setFieldDirectives()

```js
setFieldDirectives(
  fieldName: string,
  directives: Array<ExtensionsDirective>
): this
```

### getFieldDirectiveNames()

```js
getFieldDirectiveNames(
  fieldName: string
): string[]
```

### getFieldDirectiveByName()

```js
getFieldDirectiveByName(
  fieldName: string,
  directiveName: string
): DirectiveArgs | undefined
```

### getFieldDirectiveById()

```js
getFieldDirectiveById(
  fieldName: string,
  idx: number
): DirectiveArgs | undefined
```

### getFieldArgDirectives()

```js
getFieldArgDirectives(
  fieldName: string,
  argName: string
): Array<ExtensionsDirective>
```

### setFieldArgDirectives()

```js
setFieldArgDirectives(
  fieldName: string,
  argName: string,
  directives: Array<ExtensionsDirective>
): this
```

### getFieldArgDirectiveNames()

```js
getFieldArgDirectiveNames(
  fieldName: string,
  argName: string
): string[]
```

### getFieldArgDirectiveByName()

```js
getFieldArgDirectiveByName(
  fieldName: string,
  argName: string,
  directiveName: string
): DirectiveArgs | undefined
```

### getFieldArgDirectiveById()

```js
getFieldArgDirectiveById(
  fieldName: string,
  argName: string,
  idx: number
): DirectiveArgs | undefined
```

## Misc methods

### addRelation()

```js
addRelation<TArgs = any>(
  fieldName: string,
  opts: Readonly<ObjectTypeComposerRelationOpts<any, TSource, TContext, TArgs>>
): this
```

### getRelations()

```js
getRelations(): ObjectTypeComposerRelationMap<any, TContext>
```

### setRecordIdFn()

```js
setRecordIdFn(
  fn: ObjectTypeComposerGetRecordIdFn<TSource, TContext>
): this
```

### hasRecordIdFn()

```js
hasRecordIdFn(): boolean
```

### getRecordIdFn()

```js
getRecordIdFn(): ObjectTypeComposerGetRecordIdFn<TSource, TContext>
```

### getRecordId()

```js
getRecordId(
  source: TSource,
  args: Record<string, any>,
  context: TContext
): string | number
```

Get function that returns record id, from provided object.

### get()

```js
get(
  path: string | string[]
): TypeInPath<TContext> | void
```

### getNestedTCs()

```js
getNestedTCs(
  opts: {
      exclude?: string[];
  },
  passedTypes: Set<NamedTypeComposer<any>>
): Set<NamedTypeComposer<any>>
```

Returns all types which are used inside the current type

### toSDL()

```js
toSDL(
  opts: SchemaPrinterOptions & {
      deep?: boolean;
      sortTypes?: boolean;
      exclude?: string[];
  }
): string
```

Prints SDL for current type. Or print with all used types if `deep: true` option was provided.

## Internal type definitions

### ObjectTypeComposerDefinition

```js
export type ObjectTypeComposerDefinition<TSource, TContext> =
  | TypeAsString
  | TypeDefinitionString
  | ObjectTypeComposerAsObjectDefinition<TSource, TContext>
  | Readonly<ObjectTypeComposer<TSource, TContext>>
  | Readonly<GraphQLObjectType>;
```

### ObjectTypeComposerAsObjectDefinition

```js
export type ObjectTypeComposerAsObjectDefinition<TSource, TContext> = {
  name: string;
  interfaces?: null | ThunkWithSchemaComposer<
    ReadonlyArray<InterfaceTypeComposerDefinition<any, TContext>>,
    SchemaComposer<TContext>
  >;
  fields?: ObjectTypeComposerFieldConfigMapDefinition<TSource, TContext>;
  isTypeOf?: null | GraphQLIsTypeOfFn<TSource, TContext>;
  description?: string | null;
  isIntrospection?: boolean;
  extensions?: Extensions;
};
```

### ObjectTypeComposerFieldConfigMap

```js
export type ObjectTypeComposerFieldConfigMap<TSource, TContext> = ObjMap<
  ObjectTypeComposerFieldConfig<TSource, TContext>
>;
```

### ObjectTypeComposerFieldConfigMapDefinition

```js
export type ObjectTypeComposerFieldConfigMapDefinition<TSource, TContext> = ObjMap<
  ObjectTypeComposerFieldConfigDefinition<TSource, TContext>
>;
```

### ObjectTypeComposerFieldConfigDefinition

```js
export type ObjectTypeComposerFieldConfigDefinition<TSource, TContext, TArgs = any> =
  | ThunkWithSchemaComposer<
      ObjectTypeComposerFieldConfigAsObjectDefinition<TSource, TContext, TArgs>,
      SchemaComposer<TContext>
    >
  | ThunkWithSchemaComposer<ComposeOutputTypeDefinition<TContext>, SchemaComposer<TContext>>
  | Readonly<Resolver<any, TContext, any>>;
```

### ObjectTypeComposerFieldConfigAsObjectDefinition

```js
export type ObjectTypeComposerFieldConfigAsObjectDefinition<TSource, TContext, TArgs = any> = {
  type: ThunkWithSchemaComposer<
    ComposeOutputTypeDefinition<TContext> | Readonly<Resolver<any, TContext, any>>,
    SchemaComposer<TContext>
  >;
  args?: ObjectTypeComposerArgumentConfigMapDefinition<TArgs>;
  resolve?: GraphQLFieldResolver<TSource, TContext, TArgs>;
  subscribe?: GraphQLFieldResolver<TSource, TContext>;
  deprecationReason?: string | null;
  description?: string | null;
  extensions?: Extensions | undefined;
  [key: string]: any;
};
```

### ObjectTypeComposerFieldConfig

```js
export type ObjectTypeComposerFieldConfig<TSource, TContext, TArgs = any> = {
  type: ComposeOutputType<TContext>;
  args?: ObjectTypeComposerArgumentConfigMap<TArgs>;
  resolve?: GraphQLFieldResolver<TSource, TContext, TArgs>;
  subscribe?: GraphQLFieldResolver<TSource, TContext>;
  deprecationReason?: string | null;
  description?: string | null;
  astNode?: FieldDefinitionNode | null;
  extensions?: Extensions;
  [key: string]: any;
};
```

### ObjectTypeComposerArgumentConfigMap

```js
// Compose Args -----------------------------

export type ObjectTypeComposerArgumentConfigMap<TArgs = Record<string, any>> = Record<
  keyof TArgs,
  ObjectTypeComposerArgumentConfig
>;
```

### ObjectTypeComposerArgumentConfigMapDefinition

```js
export type ObjectTypeComposerArgumentConfigMapDefinition<TArgs = Record<string, any>> = Record<
  keyof TArgs,
  ObjectTypeComposerArgumentConfigDefinition
>;
```

### ObjectTypeComposerArgumentConfigAsObjectDefinition

```js
export type ObjectTypeComposerArgumentConfigAsObjectDefinition = {
  type: ThunkWithSchemaComposer<ComposeInputTypeDefinition, SchemaComposer<any>>;
  defaultValue?: any;
  description?: string | null;
  extensions?: Extensions;
  [key: string]: any;
};
```

### ObjectTypeComposerArgumentConfig

```js
export type ObjectTypeComposerArgumentConfig = {
  type: ComposeInputType;
  defaultValue?: any;
  description?: string | null;
  astNode?: InputValueDefinitionNode | null;
  extensions?: Extensions;
  [key: string]: any;
};
```

### ObjectTypeComposerArgumentConfigDefinition

```js
export type ObjectTypeComposerArgumentConfigDefinition =
  | ObjectTypeComposerArgumentConfigAsObjectDefinition
  | ThunkWithSchemaComposer<ComposeInputTypeDefinition, SchemaComposer<any>>;
```

### ObjectTypeComposerRelationMap

```js
// RELATION -----------------------------

export type ObjectTypeComposerRelationMap<TSource, TContext> = {
  [fieldName: string]: ObjectTypeComposerRelationOpts<any, TSource, TContext>;
};
```

### ObjectTypeComposerRelationOpts

```js
export type ObjectTypeComposerRelationOpts<TRelationSource, TSource, TContext, TArgs = any> =
  | ObjectTypeComposerRelationOptsWithResolver<TRelationSource, TSource, TContext, TArgs>
  | ObjectTypeComposerFieldConfigAsObjectDefinition<TSource, TContext, TArgs>;
```

### ObjectTypeComposerRelationOptsWithResolver

```js
export type ObjectTypeComposerRelationOptsWithResolver<
  TRelationSource,
  TSource,
  TContext,
  TArgs = any
> = {
  resolver: ThunkWithSchemaComposer<
    Resolver<TRelationSource, TContext, TArgs>,
    SchemaComposer<TContext>
  >;
  prepareArgs?: ObjectTypeComposerRelationArgsMapper<TSource, TContext, TArgs>;
  projection?: ProjectionType;
  description?: string | null;
  deprecationReason?: string | null;
  catchErrors?: boolean;
  extensions?: Extensions;
};
```

### ObjectTypeComposerRelationArgsMapperFn

```js
export type ObjectTypeComposerRelationArgsMapperFn<
  TSource,
  TContext,
  TArgs = Record<string, any>
> = (source: TSource, args: TArgs, context: TContext, info: GraphQLResolveInfo) => any;
```

### ObjectTypeComposerRelationArgsMapper

```js
export type ObjectTypeComposerRelationArgsMapper<
  TSource,
  TContext,
  TArgs extends Record<string, any> = Record<string, any>
> = {
  [argName in keyof TArgs]:
    | { [key: string]: any }
    | ObjectTypeComposerRelationArgsMapperFn<TSource, TContext, TArgs>
    | null
    | void
    | string
    | number
    | any[];
};
```

### ObjectTypeComposerGetRecordIdFn

```js
export type ObjectTypeComposerGetRecordIdFn<TSource, TContext, TArgs = any> = (
  source: TSource,
  args?: TArgs,
  context?: TContext
) => string;
```

### ObjectTypeComposerThunked

```js
export type ObjectTypeComposerThunked<TReturn, TContext> =
  | ObjectTypeComposer<TReturn, TContext>
  | ThunkComposer<ObjectTypeComposer<TReturn, TContext>, GraphQLObjectType>;
```
