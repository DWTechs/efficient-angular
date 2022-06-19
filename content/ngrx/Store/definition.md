---
title: Definition
---

Store is RxJS powered global state management for Angular applications, inspired by Redux. Store is a controlled state container designed to help write performant, consistent applications on top of Angular.


## Key concepts

**Actions** describe unique events that are dispatched from components and services.
**State changes** are handled by pure functions called reducers that take the current state and the latest action to compute a new state.
**Selectors** are pure functions used to select, derive and compose pieces of state.
State is accessed with the Store, an observable of state and an observer of actions.


## Local state management

NgRx Store is mainly for managing global state across an entire application. In cases where you need to manage temporary or local component state, consider using NgRx ComponentStore.


## Why use NgRx Store for State Management?

NgRx Store provides state management for creating maintainable, explicit applications through the use of single state and actions in order to express state changes. In cases where you don't need a global, application-wide solution to manage state, consider using NgRx ComponentStore which provides a solution for local state management.


## When Should I Use NgRx Store for State Management?

In particular, you might use NgRx when you build an application with a lot of user interactions and multiple data sources, or when managing state in services are no longer sufficient.

A good guideline that might help answer the question, "Do I need NgRx Store?" is the SHARI principle:

Shared: state that is accessed by many components and services.

Hydrated: state that is persisted and rehydrated from external storage.

Available: state that needs to be available when re-entering routes.

Retrieved: state that must be retrieved with a side-effect.

Impacted: state that is impacted by actions from other sources.


## Inconveniences/disadvantages

However, realizing that using NgRx Store comes with some tradeoffs is also crucial. It is not meant to be the shortest or quickest way to write code. It also encourages the usage of many files.

It's also important to consider the patterns implemented with NgRx Store. A solid understanding of RxJS and Redux will be very beneficial before learning to use NgRx Store and the other state management libraries.