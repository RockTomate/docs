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