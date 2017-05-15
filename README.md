# grafitto-filter

`grafitto-filter` is a Polymer compatible reusable web element providing a solution for filtering a list of items before displaying them. This component also supports use of custom filter functions using the `f` property. 

```bash
bower install --save grafitto/grafitto-filter
```
Data:
```json
[
  {
    "name":"John",
    "home": "Thika"
  },
  {
    "name": "Doe",
    "home": "Nairobi"
  }
]
```
Example using `dom-repeat`:

```html
<grafitto-filter items='[[data]]' where="name" like="Doe" as="vitu">
  <template>
    <template is="dom-repeat" items=[[vitu]] as="item">
      <div>{{item.name}}</div>
    </template>
  </template>
</grafitto-filter>
```

Example using `iron-list`:

```html
<grafitto-filter items='[[data]]' where="name" like="Doe" as="vitu">
  <template>
    <iron-list items=[[vitu]] as="item">
      <template>
        <div>{{item.name}}</div>
      </template>
    </iron-list>
  </template>
</grafitto-filter>
```
Just incase you are wondering, `vitu` means `items` in Swahili :-)

`grafitto-filter` also supports complex objects. consider:

var `complexObj`
```json
[
    {
      name: {
        first: "Thomas",
        second: "Kimtu"
      },
      home: "Thika"
    },
    {
      name: {
        first: "John",
        second: "Doe"
      },
      home: "Othaya"
    },
    {
      name: {
        first: "Clement",
        second: "Wainaina"
      },
      home: "Nakuru"
    }
]
``` 

Here is an example using the `complexObj` object above

```html
<grafitto-filter items=[[complexObj]] where="name.first" like="tho" as="vitu">
  <template>
    <iron-list items=[[vitu]] as="item">
      <template>
        <div>{{item.name.first}} {{item.name.second}}, {{item.home}}</div>
      </template>
    </iron-list>
  </template>
</grafitto-filter>
```

## Dependencies

Element dependencies are managed via [Bower](http://bower.io/). You can
install that via:

    npm install -g bower

Then, go ahead and download the element's dependencies:

    bower install