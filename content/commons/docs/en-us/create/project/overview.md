# Project

A TransitCore project is the foundation of an addon. It defines the structure, files, and resources used by TransitCore to load and manage your content.

A project provides a consistent environment for organizing your LuaTC code, assets, and other resources.

## Overview

A typical TransitCore project contains:

- A `main.luatc` entry point
- Asset definitions
- Models and other resources
- LuaTC scripts and modules
- Additional project files

TransitCore uses the project structure to determine how your addon is organized and loaded.

## Project Structure

A basic project can look like this:

```text
MyAddon/
├── main.luatc
├── vehicles/
├── railway/
├── signaling/
├── electrification/
└── infrastructure/