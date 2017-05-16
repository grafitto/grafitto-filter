# grafitto-filter

`grafitto-filter` is a Polymer compatible reusable web element providing a solution for filtering a list of items before displaying them. This component also supports use of custom filter functions using the `f` property. 

```bash
bower install --save grafitto/grafitto-filter
```
Data:
```javascript
[
  {
    name:"John",
    home: "Thika"
  },
  {
    name: "Doe",
    home: "Nairobi"
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
```javascript
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
You can also use your custom function to filter the items provided.
The function receives a single `item` of the items provided and should return a `boolean` 

```html
<dom-module id="your-element">
  <template>
    <grafitto-filter items=[[data]] f="filterFunc" as="vitu">
      <template>
        <iron-list items=[[vitu]] as="item">
          <template>
            <div>{{item.name}}, {{item.home}}</div>
          </template>
        </iron-list>
      </template>
    </grafitto-filter>
    <script>
      Polymer({
        is: "your-element",
        properties: {
          data: {
            type: Array,
            value: [
                    {
                      "name":"John",
                      "home": "Thika"
                    },
                    {
                      "name": "Doe",
                      "home": "Nairobi"
                    }
                  ]
          }
        },
        filterFunc: function(item){
          return item.name == "Doe";
        }
      })
    </script>
  </template>
</dom-module>
```
## Dependencies

Element dependencies are managed via [Bower](http://bower.io/). You can
install that via:

    npm install -g bower

Then, go ahead and download the element's dependencies:

    bower install