# json to sass loader for webpack

Inspired (and forked) from github.com/EdwardIrby/jsontosass-loader

## Changes
No path to give, just a json exported from the webpack config. Now we can have an exportable configuration we can use everywhere.

In config.js :
```javascript
export const vars = {
    colors : {
        'red'   : '#FF0000',
        'green' : '#00FF00',
    }
    grid : {
        'nb-columns'      : 12,
        // Mobile
        'bk-xs'        : '0px',
        'gutter-xs'    : '10px',
        // Tablet
        'bk-sm'        : '760px',
        'gutter-sm'    : '10px',
        // Desktop
        'bk-md'        : '980px',
        'gutter-md'    : '10px',
        // TV
        'bk-lg'        : '1380px',
        'gutter-lg'    : '10px',
    }
}

export default vars
```

In the webpack conf :

```javascript
import variables from './config';
```

And :

```javascript
loader: ExtractTextPlugin.extract('style', 'css!sass!jsontosass?vars=' + encodeURIComponent(JSON.stringify(variables)))
```