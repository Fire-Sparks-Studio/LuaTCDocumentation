# Project Overview

Welcome to the TransitCore project documentation.

A TransitCore project contains everything required to create, organize, and distribute an addon.

Whether you are creating a single vehicle or a complete railway system, your addon starts with a project.

## Introduction

Projects provide a consistent structure for your TransitCore content.

They allow LuaTC files, models, textures, sounds, animations, and other resources to be organized together.

A project can be extremely simple when you are just getting started.

For example, a minimal project could contain only an entry point.

    MyAddon/
    └── main.luatc

As the addon becomes larger, additional directories and resources can be added.

    MyAddon/
    ├── main.luatc
    ├── vehicles/
    ├── railway/
    ├── signaling/
    └── assets/

The structure is designed to grow with your addon.

## What Is a Project?

A project is a collection of resources that belong to the same addon.

The project provides the environment in which your LuaTC code and assets are organized.

Every addon should have a clear entry point and a predictable structure.

This makes it easier to understand where resources are located and how they are connected.

## The Main File

Every TransitCore addon uses a `main.luatc` file as its entry point.

This file is responsible for registering the resources that should be loaded by TransitCore.

A simple entry point can look like this:

    self:register(require("vehicles/tram.luatc"))

Multiple resources can be registered from the same file.

    self:register(require("vehicles/tram.luatc"))
    self:register(require("vehicles/metro.luatc"))
    self:register(require("railway/railway.luatc"))

TransitCore does not simply execute every LuaTC file it finds.

Resources must be explicitly registered by the addon.

## Project Structure

A recommended project can be organized by resource type.

    MyAddon/
    ├── main.luatc
    ├── vehicles/
    ├── railway/
    ├── signaling/
    ├── electrification/
    ├── infrastructure/
    └── assets/

Each directory has a specific purpose.

This separation becomes increasingly useful as an addon grows.

## Vehicles

The `vehicles` directory contains vehicle definitions.

This can include trams, metros, trains, locomotives, and other supported rolling stock.

    vehicles/
    ├── tram.luatc
    ├── metro.luatc
    └── train.luatc

For larger projects, vehicles can be grouped into additional directories.

    vehicles/
    ├── trams/
    │   ├── citadis.luatc
    │   └── urbos.luatc
    └── metros/
        ├── mpl75.luatc
        └── mpl16.luatc

## Railway

The `railway` directory contains railway-related definitions.

These resources can describe tracks, railway elements, switches, and other components.

    railway/
    ├── railway.luatc
    ├── tracks/
    └── switches/

A railway system can contain many individual resources.

Keeping them separated makes the project easier to maintain.

## Signaling

The `signaling` directory contains signal definitions and related resources.

    signaling/
    ├── signals.luatc
    ├── routes.luatc
    └── controllers.luatc

Signals can interact with railway infrastructure and other TransitCore systems.

A large signaling system may contain many different signal types.

Organizing them into separate files or directories can make the project easier to navigate.

## Electrification

Electrification resources define systems used to provide power to supported vehicles.

    electrification/
    ├── catenary.luatc
    └── overhead.luatc

These resources can be organized further when an addon contains multiple electrification systems.

## Infrastructure

Infrastructure contains static elements used by the addon.

Examples include poles, supports, platforms, signs, and other non-interactive or minimally interactive elements.

    infrastructure/
    ├── poles.luatc
    ├── platforms.luatc
    └── supports.luatc

Infrastructure can also be divided into multiple directories.

    infrastructure/
    ├── poles/
    ├── platforms/
    └── signs/

This becomes useful when an addon contains a large amount of infrastructure.

## Assets

Projects can contain external assets used by LuaTC resources.

Common asset types include models, textures, sounds, and animations.

    assets/
    ├── models/
    ├── textures/
    ├── sounds/
    └── animations/

Keeping assets separate from LuaTC definitions can make larger projects easier to manage.

## Models

Models provide the visual geometry used by resources.

They can be stored inside the project's asset directories.

    assets/
    └── models/
        ├── tram.obj
        ├── metro.obj
        └── signal.obj

A project may contain many different models.

Using descriptive filenames makes it easier to identify them later.

## Textures

Textures provide the visual appearance of models.

    assets/
    └── textures/
        ├── tram.png
        ├── metro.png
        └── signal.png

Textures can be grouped by resource when necessary.

    assets/
    └── textures/
        ├── vehicles/
        │   ├── tram/
        │   └── metro/
        ├── railway/
        └── signaling/

## Sounds

Sounds can be used by vehicles, signals, infrastructure, and other resources.

A project might contain several types of sounds.

    assets/
    └── sounds/
        ├── vehicles/
        ├── signals/
        └── environment/

Keeping audio resources grouped by purpose makes them easier to locate.

## Animations

Animations can be used for moving components.

Examples include doors, pantographs, couplers, control elements, and other animated parts.

    assets/
    └── animations/
        ├── doors/
        ├── pantographs/
        └── controls/

The exact organization can be adapted to the needs of the addon.

## Naming Resources

Consistent naming conventions are important for large projects.

Prefer descriptive names such as `tram_tcl.luatc` or `metro_mpl75.luatc`.

Avoid unclear names such as `test.luatc`, `thing.luatc`, or `new_file.luatc`.

Good names make the project easier to understand.

## Registration

TransitCore does not automatically register every resource.

Resources should be explicitly registered from the project's `main.luatc`.

For example:

    self:register(require("vehicles/tram.luatc"))
    self:register(require("vehicles/metro.luatc"))
    self:register(require("railway/railway.luatc"))
    self:register(require("signaling/signals.luatc"))

This gives addon developers control over which resources are loaded.

## Development

During development, projects can contain experimental resources.

These resources do not necessarily need to be included in the final addon.

    development/
    ├── test_vehicle.luatc
    ├── test_signal.luatc
    └── experimental.luatc

Keeping development resources separate can be useful when working on complex projects.

## Large Projects

Large projects should use additional directories when necessary.

Do not be afraid to create additional levels of organization.

    vehicles/
    ├── trams/
    ├── metros/
    ├── trains/
    └── locomotives/

The exact structure is up to the addon developer.

There is no requirement for every addon to use the same internal organization.

## Example Project

Consider an addon containing a complete tram network.

The project could contain the following structure:

    TramNetwork/
    ├── main.luatc
    ├── vehicles/
    │   └── tram.luatc
    ├── railway/
    │   └── tram_tracks.luatc
    ├── signaling/
    │   └── tram_signals.luatc
    ├── electrification/
    │   └── overhead.luatc
    ├── infrastructure/
    │   ├── poles.luatc
    │   └── platforms.luatc
    └── assets/
        ├── models/
        ├── textures/
        ├── sounds/
        └── animations/

This structure clearly separates each major part of the addon.

## Organizing Code

LuaTC files should generally be kept close to the resources they define.

For example, vehicle definitions can be stored inside the `vehicles` directory.

    vehicles/
    ├── tram.luatc
    └── metro.luatc

This makes it easier to locate the source code for a specific resource.

## Organizing Assets

Assets can be grouped according to their purpose or according to the resource they belong to.

Both approaches can work.

A resource-based structure might look like this:

    assets/
    └── vehicles/
        ├── tram/
        │   ├── model/
        │   ├── textures/
        │   └── sounds/
        └── metro/
            ├── model/
            ├── textures/
            └── sounds/

A type-based structure might instead look like this:

    assets/
    ├── models/
    ├── textures/
    └── sounds/

Choose the structure that makes the project easiest to understand.

## Best Practices

Keep related files together.

Use descriptive names.

Avoid unnecessary duplication.

Keep experimental files separate from production resources.

Use `main.luatc` as the central registration point.

Keep assets organized.

Review your project structure regularly.

## Common Mistakes

One common mistake is putting every file directly inside the project root.

Another common mistake is using inconsistent names.

A third mistake is registering resources that are not required.

These issues may not matter in a small project, but they become problematic as the addon grows.

## Project Checklist

Before considering a project ready, verify the following:

- [ ] `main.luatc` exists.
- [ ] Resources are correctly organized.
- [ ] Files have descriptive names.
- [ ] Required assets are present.
- [ ] Unused resources are not registered.
- [ ] Development files are separated.
- [ ] The project is easy to understand.
- [ ] Resource paths are correct.
- [ ] Models and textures are correctly referenced.
- [ ] The addon can be loaded successfully.

## Maintaining a Project

A project should remain understandable throughout its entire development lifecycle.

As new features are added, take the time to place them in the appropriate directory.

Avoid creating temporary structures that become permanent simply because the project has grown around them.

Regular organization is much easier than reorganizing hundreds of files later.

## Final Example

A mature TransitCore project could eventually look like this:

    MyTransitAddon/
    ├── main.luatc
    │
    ├── vehicles/
    │   ├── trams/
    │   │   ├── citadis.luatc
    │   │   └── urbos.luatc
    │   └── metros/
    │       ├── mpl75.luatc
    │       └── mpl16.luatc
    │
    ├── railway/
    │   ├── tracks/
    │   ├── switches/
    │   └── railway.luatc
    │
    ├── signaling/
    │   ├── signals/
    │   ├── routes/
    │   └── signaling.luatc
    │
    ├── electrification/
    │   ├── catenary/
    │   └── electrification.luatc
    │
    ├── infrastructure/
    │   ├── poles/
    │   ├── platforms/
    │   └── infrastructure.luatc
    │
    └── assets/
        ├── models/
        ├── textures/
        ├── sounds/
        └── animations/

## Conclusion

A good project structure should make your addon easier to understand.

There is no single structure that works for every addon.

Start simple.

Add additional directories when they become useful.

Keep related resources together.

Use clear names.

Keep the entry point organized.

Most importantly, choose a structure that remains understandable as your project grows.

## Next Steps

Once you understand the basics of a TransitCore project, continue with the Structure documentation.

The next section explains how the different files and directories of a TransitCore project fit together.

From there, you can learn how `main.luatc` registers your resources and how LuaTC definitions are connected to the rest of your addon.