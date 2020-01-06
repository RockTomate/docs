---
id: terminology
title: Terminology
---

Before we dive in, it's important to understand some terminology which is used throughout the documentation.

## Step

Step is a simplest form of action. Its purpose is to invoke a specific instruction with specified parameters. For example, it could something as simple as building a Unity project for a specific platform.

Steps cannot be executed by themselves, but they can execute child steps (some steps like `Group` does nothing but run child steps).

## Job

Job stores steps, their properties/formulas and executes those steps in a given order. Jobs is what users usually interact with directly.

## Macro

Macro is a simple function which is executed within a Formula. Macros are methods that take multiple arguments and return a single value. An example of macro would be `sum(10, 30)`.

You can read more about macros [here](formulas/macros.md).

## Design-Time

Refers to a stage when you're editing the Job properties, adding/removing Steps or changing their parameters.

## Runtime

Refers to the stage when the Job is running.

## Job Context

`JobContext` is a class that stores current data about the job such as variables at a current stage of execution. It's constantly modified and passed to Steps before execution.

It's not required to understand the inner workings of the `JobContext` especially if you're not looking into extending RockTomate core functionality.