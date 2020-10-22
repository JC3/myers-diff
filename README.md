# myers-diff

A javascript test differentiation implementation based on [An O(ND) Difference Algorithm and Its Variations (1986)](www.xmailserver.org/diff2.pdf).  It is a lightweight, no-frills implementation.

## Installation
```bash
$ npm install myers-diff
```

## Basic usage

```js
const myers = require('myers-diff');

const lhs = 'the quick red fox jumped\nover the hairy dog';
const rhs = 'the quick brown fox jumped\nover the lazy dog';

const diff = myers.diff(lhs, rhs, {});

console.log(myers.formats.GnuNormalFormat(diff));
console.log(diff);
//
// 1,2c1,2
// < the quick red fox jumped
// < over the hairy dog
// ---
// > the quick brown fox jumped
// > over the lazy dog
```

## API
### Typedefs

<dl>
<dt><a href="#Change">Change</a> : <code>object</code></dt>
<dd><p>A change.</p>
</dd>
<dt><a href="#ChangePair">ChangePair</a> : <code>object</code></dt>
<dd><p>A change pair</p>
</dd>
<dt><a href="#EncoderContext">EncoderContext</a> : <code>object</code></dt>
<dd><p>Encoder context</p>
</dd>
<dt><a href="#myers">myers</a> : <code>object</code></dt>
<dd><p>Main module exports.</p>
</dd>
<dt><a href="#diff">diff</a> ⇒ <code><a href="#Change">Array.&lt;Change&gt;</a></code></dt>
<dd><p>Compare <code>lhs</code> to <code>rhs</code>.  Changes are compared from left
to right such that items are deleted from left, or added to right,
or just otherwise changed between them.</p>
</dd>
<dt><a href="#GnuNormalFormat">GnuNormalFormat</a> ⇒ <code>string</code></dt>
<dd><p>Formats a diff in GNU normal format.</p>
</dd>
<dt><a href="#formats">formats</a> : <code>object</code></dt>
<dd></dd>
</dl>

<a name="Change"></a>

### Change : <code>object</code>
A change.

**Kind**: global typedef  
**Properties**

| Name | Type | Description |
| --- | --- | --- |
| at | <code>number</code> | The index where the change occurs. |
| del | <code>number</code> | The number of parts changed. |
| ctx | [<code>EncoderContext</code>](#EncoderContext) | The encoder context. |

<a name="ChangePair"></a>

### ChangePair : <code>object</code>
A change pair

**Kind**: global typedef  
**Properties**

| Name | Type | Description |
| --- | --- | --- |
| lhs | [<code>Change</code>](#Change) | The left-hand document that was compared. |
| rhs | [<code>Change</code>](#Change) | The right-hand document that was compared. |

<a name="EncoderContext"></a>

### EncoderContext : <code>object</code>
Encoder context

**Kind**: global typedef  
**Properties**

| Name | Type | Description |
| --- | --- | --- |
| getPart | <code>function</code> | Gets a part. |

<a name="myers"></a>

### myers : <code>object</code>
Main module exports.

**Kind**: global typedef  
**Properties**

| Name | Type |
| --- | --- |
| diff | [<code>diff</code>](#diff) | 
| formats | [<code>formats</code>](#formats) | 

<a name="diff"></a>

### diff ⇒ [<code>Array.&lt;Change&gt;</code>](#Change)
Compare `lhs` to `rhs`.  Changes are compared from left
to right such that items are deleted from left, or added to right,
or just otherwise changed between them.

**Kind**: global typedef  
**Returns**: [<code>Array.&lt;Change&gt;</code>](#Change) - An array of change objects  

| Param | Type | Default | Description |
| --- | --- | --- | --- |
| lhs | <code>string</code> |  | The left-hand source text. |
| rhs | <code>string</code> |  | The right-hand source text. |
| [options] | <code>object</code> | <code>{}</code> | Optional settings. |
| [options.ignoreWhitespace] | <code>boolean</code> | <code>false</code> | Ignores whitespace. |
| [options.ignoreCase] | <code>boolean</code> | <code>false</code> | Ignores case. |
| [options.ignore] | <code>boolean</code> | <code>false</code> | Ignores accents. |
| [options.compare] | <code>string</code> | <code>&quot;&#x27;lines&#x27;&quot;</code> | The type of comparison; one of: 'chars', 'words', or 'lines' (default). |

**Example**  
```js
const myers = require('myers-diff');
const changes = myers.diff(lhs, rhs);
```
<a name="GnuNormalFormat"></a>

### GnuNormalFormat ⇒ <code>string</code>
Formats a diff in GNU normal format.

**Kind**: global typedef  
**Returns**: <code>string</code> - A diff in GNU normal format.  

| Param | Type | Description |
| --- | --- | --- |
| changes | [<code>Array.&lt;Change&gt;</code>](#Change) | The array of changes to format. |

**Example**  
```js
const myers = require('myers-diff');
console.log(myers.formats.GnuNormalFormat(changes));
```
<a name="formats"></a>

### formats : <code>object</code>
**Kind**: global typedef  
**Properties**

| Name | Type |
| --- | --- |
| GnuNormalFormat | [<code>GnuNormalFormat</code>](#GnuNormalFormat) | 

