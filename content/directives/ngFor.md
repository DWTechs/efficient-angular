---
title: "*ngFor"
---


The structural directive ngFor allows you to loop over an array and inject the elements into the DOM.

It is possible to retrieve other information such as the index of the element:
* index : position of the element.
* odd : indicates if the element is at an odd position.
* even : indicates if the element is at an even position.
* first : indicates if the element is at the first position.
* last : indicates if the element is at the last position.

## Examples

JavaScript
```javascript
export interface Picture {
  address : string,
  src : string,
  width : number,
  height : number,
  text : string
}

let pictures : Picture[] = [];
```
### Example 1

HTML
```html
<div *ngFor="let img of pictures" class="img-container">
    <span>{{ img.text }}</span>
</div>
```
In this example, we have an array of pictures.<br/>
With the ngFor directive, we will iterate on pictures.<br/>
We display the text of each image.<br/>


### Example 2

HTML
```html
<div *ngFor="let img of pictures ; let index = index" class="img-container"> <!-- div 1 -->
    <div  [style.background-image]="'url(' + img.src + ')'" class="picture" key="index"> <!-- div 2 -->
        <div class="image-click" (click)="imageClick(index)"></div> <!-- div 3 -->
        <div><p>{{ img.text }}</p></div><!-- div 4-->       
    </div>
</div>
```

In this example, we have an array of pictures.<br/>
With the ngFor directive, we will iterate on pictures.<br/>
For each image contained in picture, div 1, 2, 3 and 4 will be duplicated.<br/>
We also get the index of the current element in order to process the click on a picture (div 3).

### Example 3

HTML
```html
<div *ngFor="let img of pictures; let index = index; let isFirst = first; let isOdd = odd;"> <!-- div 1 -->
    <span>{{ index }}</span>
    <span>:</span>
    <span>{{ img.text }}</span>
    <span>( isFirst: {{ isFirst }}, isOdd: {{ isOdd }} )</span>
</div>
<!-- output
0 : image text ( isFirst: true, isOdd: false )<br/>
1 : image text ( isFirst: false, isOdd: true ) -->  
```

## Special note for performance: trackBy

Working with list of data and *ngFor directive can quickly slow down your application.

A solution to prevent performance issues is to use `trackBy`.

By default, Angular tracks items by object identity.<br>
So, if the items are initiliazed with a request, and updated with a second request, items lose their identities and Angular must redraw them.<br>
This produces big DOM manipulations, which can be very expensive.

We can help Angular to track items by providing a trackBy function.<br>
`trackBy` takes a trackByFunction that will tell Angular how to track items.<br>
The trackBy function takes the index and the current item as arguments and needs to return the unique identifier for this item.<br>

### Example

Here is a simple component that displays a list of books, and get new data by clicking on 'Refresh list' button.

```typescript
import { Component, OnInit } from "@angular/core";

@Component({
  selector: "app-root",
  styleUrls: ["./app.component.scss"],
  template: `
  <button (click)="getBooks()">Refresh list</button>
  <ul>
    <li *ngFor="let book of books;">{{ book.name }}</li>
  </ul>
  `
})
export class AppComponent implements OnInit {

  public books = [];

  ngOnInit() {
    this.getBooks();
  }

  public getBooks() {
    this.books = this.books.length > 4 ? [
      { id: 0, name: 'Don Quixote - Miguel De Cervantes' },
      { id: 1, name: 'Robinson Crusoe - Daniel Defoe' },
      { id: 2, name: 'Frankenstein - Mary Shelley' },
      { id: 3, name: 'Anna Karenina - Leo Tolstoy' },
    ] : [
      { id: 0, name: 'Don Quixote - Miguel De Cervantes' },
      { id: 1, name: 'Robinson Crusoe - Daniel Defoe' },
      { id: 2, name: 'Frankenstein - Mary Shelley' },
      { id: 3, name: 'Anna Karenina - Leo Tolstoy' },
      { id: 4, name: 'The Trial - Franz Kafka' },
    ];
  }
}

```

We can see Angular rebuilds the DOM at each refresh.

![Without-Track-By](/assets/images/angular/before-track-by.gif "Without trackBy")

Now let's add `trackBy`:

```typescript
import { Component, OnInit } from "@angular/core";

@Component({
  selector: "app-root",
  styleUrls: ["./app.component.scss"],
  template: `
  <button (click)="getBooks()">Refresh list</button>
  <ul>
    <li *ngFor="let book of books; trackBy: trackByFn">{{ book.name }}</li>
  </ul>
  `
})
export class AppComponent implements OnInit {

  public books = [];

  ngOnInit() {
    this.getBooks();
  }

  public getBooks() {
    this.books = this.books.length > 4 ? [
      { id: 0, name: 'Don Quixote - Miguel De Cervantes' },
      { id: 1, name: 'Robinson Crusoe - Daniel Defoe' },
      { id: 2, name: 'Frankenstein - Mary Shelley' },
      { id: 3, name: 'Anna Karenina - Leo Tolstoy' },
    ] : [
      { id: 0, name: 'Don Quixote - Miguel De Cervantes' },
      { id: 1, name: 'Robinson Crusoe - Daniel Defoe' },
      { id: 2, name: 'Frankenstein - Mary Shelley' },
      { id: 3, name: 'Anna Karenina - Leo Tolstoy' },
      { id: 4, name: 'The Trial - Franz Kafka' },
    ];
  }

  public trackByFn(index: number, item) {
    return index;
  }
}

```

Now, even when the collection changes, Angular can track which item has been inserted or deleted according to their unique identifier provided by the trackBy, and destroy only the items that changed.

![With-Track-By](/assets/images/angular/after-track-by.gif "With trackBy")
