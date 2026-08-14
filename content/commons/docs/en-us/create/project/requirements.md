# Project Requirements

Before creating a TransitCore addon, make sure your project follows the basic requirements expected by TransitCore.

A valid project needs a recognizable structure and an entry point from which its resources can be registered.

## Addon Directory

TransitCore addons are stored inside the `TC_Addons` directory.

A basic installation can look like this:

```text
    .minecraft/
    └── TC_Addons/
        └── MyAddon/
```

Each directory inside `TC_Addons` represents an independent addon project.

### Project Directory

Each addon should have its own directory.

For example:

```text
    TC_Addons/
    ├── MyAddon/
    ├── RailwayAddon/
    └── MyVehicles/
```

Keeping addons separated prevents resources from different projects from being mixed together.

<Alert severity="info">

The name of the addon directory is up to you. Choose a clear and descriptive name that identifies your project.

</Alert>

## `main.luatc`

Every TransitCore addon requires a `main.luatc` file.

This file acts as the entry point of the project.

A minimal project should therefore contain at least:

```text
    MyAddon/
    └── main.luatc
```

TransitCore uses this file to determine which resources belong to the addon.

### Entry Point Location

The `main.luatc` file must be located at the root of the addon.

The following structure is valid:

```text
    MyAddon/
    ├── main.luatc
    └── vehicles/
        └── tram.luatc
```

The following structure is not valid:

```text
    MyAddon/
    └── scripts/
        └── main.luatc
```

The entry point must remain directly inside the addon directory.

<Alert severity="warning">

Do not move `main.luatc` into another directory. TransitCore expects the addon entry point at the root of the project.

</Alert>

## LuaTC Files

Project resources are defined using LuaTC.

LuaTC files should use the `.luatc` extension.

For example:

```text
    vehicles/
    ├── tram.luatc
    └── metro.luatc
```

LuaTC is used to define and configure the resources provided by your addon.

### File Organization

LuaTC files should be organized according to the resources they define.

For example:

```text
    MyAddon/
    ├── main.luatc
    ├── vehicles/
    │   ├── tram.luatc
    │   └── metro.luatc
    └── railway/
        └── railway.luatc
```

This is not only useful for readability, but also makes larger projects easier to maintain.

## Resource Registration

TransitCore does not automatically load every LuaTC file present in your project.

Resources must be explicitly registered from `main.luatc`.

For example:

    self:register(require("vehicles/tram.luatc"))

Multiple resources can be registered from the same entry point:

```luatc
    self:register(require("vehicles/tram.luatc"))
    self:register(require("vehicles/metro.luatc"))
    self:register(require("railway/railway.luatc"))
```

### Registration Paths

The path passed to `require()` must point to the LuaTC resource you want to load.

For example, if your project contains:
```text
    MyAddon/
    ├── main.luatc
    └── vehicles/
        └── tram.luatc
```

The resource can be registered with:

    self:register(require("vehicles/tram.luatc"))

<Alert severity="warning">

A LuaTC file existing inside your project does not automatically make it part of the addon. If the resource needs to be loaded by TransitCore, it must be registered.

</Alert>

## Project Structure

There is no requirement for every addon to use the exact same directory structure.

However, organizing resources by type is recommended for larger projects.

A typical project can look like this:
```text
    MyAddon/
    ├── main.luatc
    ├── vehicles/
    ├── railway/
    ├── signaling/
    ├── electrification/
    ├── infrastructure/
    └── assets/
```


### Vehicles

Vehicle definitions can be stored inside the `vehicles` directory.
```text
    vehicles/
    ├── tram.luatc
    └── metro.luatc
```

### Railway

Railway-related definitions can be stored inside the `railway` directory.

```text
    railway/
    └── railway.luatc
```

### Signaling

Signal definitions and related resources can be organized inside the `signaling` directory.

```text
    signaling/
    └── signals.luatc
```

### Electrification

Electrification resources can be organized inside the `electrification` directory.

```text
    electrification/
    └── catenary.luatc
```

### Infrastructure

Static infrastructure resources can be organized inside the `infrastructure` directory.

```text
    infrastructure/
    ├── poles.luatc
    └── platforms.luatc
```

## Assets

Projects can contain assets required by their resources.

These can include models, textures, sounds, animations, and other supported resources.

A project can organize them under an `assets` directory.

```text
    assets/
    ├── models/
    ├── textures/
    ├── sounds/
    └── animations/
```

### Asset Organization

For larger addons, assets can be grouped according to the resources they belong to.

For example:

```text
    assets/
    └── vehicles/
        └── tram/
            ├── model/
            ├── textures/
            └── sounds/
```

Keeping assets organized becomes increasingly important as the project grows.

## Recommended Requirements

A TransitCore project should satisfy the following basic requirements:

- The addon is located inside `TC_Addons`.
- The addon has its own project directory.
- A `main.luatc` file exists at the root of the project.
- LuaTC resources use the `.luatc` extension.
- Resources that need to be loaded are registered from `main.luatc`.
- Resource paths used by `require()` correctly point to the intended files.
- Project resources are organized in a clear and maintainable structure.

<Alert severity="success">

A project does not need to contain every possible TransitCore resource. Start with only what your addon needs and expand the structure as your project grows.

</Alert>