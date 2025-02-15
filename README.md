# TypeScript Type Guard Missing Undefined Handling

This repository demonstrates a subtle issue in TypeScript's type guards. When a function accepts a union type including `null`, the type guard may not correctly handle `undefined` values, even though `undefined` is a subtype of `null`. This leads to unexpected compilation errors.

## The Problem

The `greet` function demonstrates the issue. It accepts either a string or `null`. While it correctly handles `null`, it throws an error if an `undefined` value is passed.  This occurs because TypeScript's type narrowing doesn't automatically consider `undefined` as a valid case within the `string | null` union, even though `undefined` can be assigned to a variable of type `null`.

## Solution

The solution involves explicitly handling `undefined` within the type guard. This can be done using an additional check or by widening the parameter's type to include `undefined`.