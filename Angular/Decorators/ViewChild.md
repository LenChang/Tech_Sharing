# Overview
- Property decorator that configures a view query. The change detector looks for the first element or the directive matching the selector in the view DOM. If the view DOM changes, and a new child matches the selector, the property is updated.
- [Angular Official Docs](https://angular.io/api/core/ViewChild)

## Purpose
- If you wish to gain access to a **DOM element**, **directive** or **component** from a parent component class then you rely on Angular ViewChild.
- it will return the **1st element** that matches. It will match against the template reference selector, directive or component.

## Reference
- https://www.positronx.io/angular-viewchild-access-child-component/
- https://www.digitalocean.com/community/tutorials/angular-viewchild-access-component
