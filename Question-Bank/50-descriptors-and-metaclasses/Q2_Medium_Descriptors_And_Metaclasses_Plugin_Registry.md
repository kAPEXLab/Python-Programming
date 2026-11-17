---
layout: default
---

# 50_DescriptorsAndMetaclasses_PluginRegistry

**Difficulty:** Medium  
**Primary Python Concept:** Metaclass registration  
**Supporting Concepts:** Class creation, registries, abstract behavior  
**Automotive Domain:** Offline diagnostic plugin registry  
**Estimated Completion Time:** 45 minutes

## Learning Objective
Register plugin subclasses automatically when their classes are created.

## Prerequisites
Classes, inheritance, metaclasses, dictionaries, and class attributes.

## Scenario Introduction
A local diagnostic toolkit discovers named plugins without loading external code.

## Problem Statement
**Goal:** Register plugin subclasses automatically when their classes are created.

**Specifically:** Implement `PluginMeta(type)` and `PluginBase(metaclass=PluginMeta)` with `plugins() -> dict[str, type]`.

## Task to Implement
Register concrete subclasses by their non-empty `plugin_name` class attribute; exclude `PluginBase`. Reject duplicate names during class creation.

## Input Specification
Plugins define `plugin_name: str` and a `run() -> str` method.

## Output Specification
`plugins()` returns a copy of the registry mapping names to classes.

## Rules and Constraints
- Registration belongs in the metaclass.
- Do not import plugins dynamically or connect to vehicles.
- Duplicate names raise `ValueError`.

## Hints
Inspect the namespace during `__new__` and register only subclasses with a valid name.

## Common Mistakes
- Registering the base class.
- Returning the mutable internal dictionary.
- Detecting duplicates only when running a plugin.

## Extension Challenge
Add a `category` field and a lookup by category.
