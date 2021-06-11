# @vanpariyar/text-manipulation

this is the very simple.

## install
`npm install @vanpariyar/text-manipulation`

## use
```javascript

const stringTOSlug = require('@vanpariyar/text-manipulation');

console.log( stringTOSlug( "THis is the Demo Title" ) );

```
`Output > this-is-the-demo-title `

Code Behind:

```javascript

const stringTOSlug = function (str)
{
    str = str.replace(/^\s+|\s+$/g, ''); // trim
    str = str.toLowerCase();

    // remove accents, swap ñ for n, etc
    const from = "àáäâèéëêìíïîòóöôùúüûñçěščřžýúůďťň·/_,:;";
    const to   = "aaaaeeeeiiiioooouuuuncescrzyuudtn------";

    for (let i=0, l=from.length ; i<l ; i++)
    {
        str = str.replace(new RegExp(from.charAt(i), 'g'), to.charAt(i));
    }

    str = str.replace('.', '-') // replace a dot by a dash 
        .replace(/[^a-z0-9 -]/g, '') // remove invalid chars
        .replace(/\s+/g, '-') // collapse whitespace and replace by a dash
        .replace(/-+/g, '-') // collapse dashes
        .replace( /\//g, '' ); // collapse all forward-slashes

    return str;
}

module.exports = stringTOSlug;
```