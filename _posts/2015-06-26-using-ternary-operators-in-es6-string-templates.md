---
layout: post
title: Using Ternary Operators in ES6 String Templates
---
The new ES6 version of JavaScript introduced Template Strings which allow for improved readability of code when working with multiple line strings. This allows us to avoid the following syntax:

```javascript
//Common method
let foo = '<table>' +
	'<tr>' +
		'<td>Tables are a pain</td>' +
	'</tr>' +
'</table>';
//Alternate equally painful & ugly method
let foo = '<table> \
	<tr> \
		<td>Tables are a pain</td> \
	</tr> \
</table>';
```

Instead we can now use the backtick character to create a string template. We can also include variables by wrapping them in ${}.

```
let enjoyment = 'not so bad';
let foo = `<table>
	<tr>
		<td>Tables are ${enjoyment}</td>
	</tr>
</table>`;
```

We can even take this one step farther and use a ternary operator to do an if else statement within our multiple line string.

```
let displayAverages = false;
let totalSales = 500;
let averageSales = 338;
let tableTemplate = `<table id="sales">
	<tr>
		<th>Total</th>
		${displayAverages ? '<th>Averages</th>' : ''}
	</tr>
	<tr>
		<td>${totalSales}</td>
		${displayAverages ? `<td>${averageSales}</td>` : ''}
</tr>
</table>`;
```

Try it out for yourself on Plunker.

<iframe style="border: 1px solid #999;width: 100%; height: 300px"
src="http://embed.plnkr.co/lzXUulsbNAFdnu8m2xDx/" frameborder="0"
allowfullscreen="allowfullscreen">
Loading plunk...
</iframe>