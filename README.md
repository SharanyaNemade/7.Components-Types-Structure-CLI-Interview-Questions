# Angular21Tutorial

This project was generated using [Angular CLI](https://github.com/angular/angular-cli) version 22.1.7.

This code is part of an Angular Component. It defines some of the configuration properties of a component.

Let's understand each property in detail, including why we use it and how it works.

typescript

```typescript
imports: [],
selector: 'app-profile',
standalone: true,
templateUrl: './profile.html',
styleUrl: './profile.css'
```

## 1. `imports: []`

Meaning: Specifies which other Angular components, directives, or pipes this component needs to use in its HTML template.

In Angular, when you create a standalone component, you must explicitly import the Angular features that you want to use.

For example:

typescript

```typescript
import { Component } from '@angular/core';
import { CommonModule } from '@angular/common';

@Component({
  selector: 'app-profile',
  standalone: true,
  imports: [CommonModule],
  templateUrl: './profile.html',
  styleUrl: './profile.css'
})
export class ProfileComponent {

}
```

Here, `CommonModule` provides commonly used Angular features such as:

- `*ngIf` – conditionally displays HTML elements.
- `*ngFor` – repeats HTML elements.
- Other common Angular directives and pipes.

If you use `imports: []`, it means you haven't imported any additional Angular features into this component.

Example:

If your HTML contains:

HTMLWrap linesCopy codePreview

```html
<h1>Welcome to my profile</h1>
```

You don't need any additional imports because this is normal HTML.

But if you use Angular directives such as `*ngIf`, you need the appropriate imports.

## 2. `selector: 'app-profile'`

Meaning: Defines the custom HTML tag used to display your Angular component.

Think of a selector as the component's name in HTML.

For example:

typescript

```typescript
selector: 'app-profile'
```

You can use this component in another component's HTML like this:

HTMLWrap linesCopy codePreview

```html
<app-profile></app-profile>
```

Angular recognizes this tag and displays the content of the ProfileComponent.

Example:

Suppose your `profile.html` contains:

HTMLWrap linesCopy codePreview

```html
<h1>My Profile</h1>
<p>Welcome to my profile page!</p>
```

And another component has:

HTMLWrap linesCopy codePreview

```html
<app-profile></app-profile>
```

The output will be:

## My Profile

Welcome to my profile page\!

In simple words: `selector` tells Angular which HTML tag represents your component.

## 3. `standalone: true`

Meaning: Tells Angular that this component is a standalone component.

Before standalone components were introduced, Angular components generally needed to be registered inside an `NgModule`.

For example, older Angular applications used:

typescript

```typescript
@NgModule({
  declarations: [ProfileComponent],
  imports: [CommonModule]
})
export class AppModule {

}
```

But with:

typescript

```typescript
standalone: true
```

You don't need to declare the component inside an Angular module.

You can directly import the component wherever you need it.

For example:

typescript

```typescript
import { ProfileComponent } from './profile/profile';

@Component({
  selector: 'app-root',
  standalone: true,
  imports: [ProfileComponent],
  template: `<app-profile></app-profile>`
})
export class AppComponent {

}
```

Advantages of standalone components:

- Less module configuration.
- Easier component reuse.
- Simpler application structure.
- Easier lazy loading.
- Better organization of Angular applications.

In simple words: `standalone: true` means the component can work independently without being declared in an NgModule.

## 4. `templateUrl: './profile.html'`

Meaning: Specifies the external HTML file that contains the component's user interface.

For example:

typescript

```typescript
templateUrl: './profile.html'
```

This tells Angular to find the HTML file named `profile.html` in the same folder as the component TypeScript file.

Your folder structure might look like this:

profile/

profile.ts Component logic

profile.html UI design

profile.css Styling

Example of `profile.html`:

HTMLWrap linesCopy codePreview

```html
<h1>My Profile</h1>
<p>This is my profile component.</p>
<button>View Profile</button>
```

Angular loads this HTML and displays it whenever the component is used.

In simple words: `templateUrl` tells Angular where your component's HTML code is located.

## 5. `styleUrl: './profile.css'`

Meaning: Specifies the external CSS file used to style the component.

For example:

typescript

```typescript
styleUrl: './profile.css'
```

This tells Angular to load the CSS styles from `profile.css`.

Example of `profile.css`:

css

```css
h1 {
  color: blue;
  font-size: 30px;
}

p {
  color: gray;
}

button {
  background-color: green;
  color: white;
  padding: 10px;
}
```

These styles apply to the HTML elements in your component.

In simple words: `styleUrl` tells Angular where the component's CSS styling is located.

Note: Angular also supports `styleUrls` (plural), which accepts an array of CSS file paths.

## 6. How everything works together

Let's understand the complete flow.

profile.ts

Component configuration and logic

Loads

profile.html

User interface

profile.css

Design and styling

Angular combines them

Rendered Profile Component

The final UI displayed in the browser

## 7. Complete Angular example

Here is how all these properties look together:

profile.ts

typescript

```typescript
import { Component } from '@angular/core';

@Component({
  selector: 'app-profile',
  standalone: true,
  imports: [],
  templateUrl: './profile.html',
  styleUrl: './profile.css'
})
export class ProfileComponent {

  username = 'John';

}
```

profile.html

HTMLWrap linesCopy codePreview

```html
<h1>Welcome {{ username }}</h1>
<p>This is my profile page.</p>
```

profile.css

css

```css
h1 {
  color: blue;
}

p {
  font-size: 18px;
}
```

### Quick revision

| Property | Purpose |
| --- | --- |
| `imports` | Imports components, directives and pipes |
| `selector` | Defines the custom HTML tag |
| `standalone` | Allows the component to work without NgModule declaration |
| `templateUrl` | Specifies the HTML file |
| `styleUrl` | Specifies the CSS file |

One important thing to remember:

- `.ts` → What the component does (logic).
- `.html` → What the component displays (structure).
- `.css` → How the component looks (design).

Together, these three files form an Angular component.
