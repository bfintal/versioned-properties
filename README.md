# versioned-properties
Enables versioned object property management. Add and retrieve sets of properties with associated version numbers

# Usage

```js
const obj = new VersionedProperties()

obj.addProperties( {
	properties: {
		foo: 'bar',
		baz: { type: 'string', default: '' },
	},
	versionAdded: '0.1.0',
	versionDeprecated: '0.8.0',
} )

obj.addProperties( {
	properties: {
		corge: { type: 'string', default: 'grault' },
	},
	versionAdded: '0.2.0',
} )

obj.updateProperties( {
	properties: {
		corge: { default: 'garply' },
	},
	versionAdded: '0.9.0',
} )

obj.getForVersion( '0.7.0' )
/* Returns:
{
	foo: 'bar',
	baz: { type: 'string', default: ' },
	corge: { type: 'string', default: 'grault' },
} */

obj.getForVersion( '0.8.0' )
/* Returns:
{
	corge: { type: 'string', default: 'grault' },
} */

obj.getForVersion( '0.9.0' )
/* Returns:
{
	corge: { type: 'string', default: 'garply' },
} */
```
