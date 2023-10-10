## Admonitions

Admonitions are frequently used in documentation to call attention to warnings, notes, and tips. Markdown doesn’t provide special syntax for admonitions, and most Markdown applications don’t provide support for admonitions (one exception is [MkDocs](https://www.markdownguide.org/tools/mkdocs/)).

However, if you need to add admonitions, you might be able to use [blockquotes](https://www.markdownguide.org/basic-syntax/#blockquotes-1) with [emoji](https://www.markdownguide.org/extended-syntax/#emoji) and [emphasis](https://www.markdownguide.org/basic-syntax/#emphasis) to create something that looks similar to the admonitions you see on other websites.

```
> :warning: **Warning:** Do not push the big red button.

> :memo: **Note:** Sunrises are beautiful.

> :bulb: **Tip:** Remember to appreciate the little things in life.
```

The rendered output looks like this:

> ⚠️ **Warning:** Do not push the big red button.

> 📝 **Note:** Sunrises are beautiful.

> 💡 **Tip:** Remember to appreciate the little things in life.


```markdown
> [!NOTE]  
> Highlights information that users should take into account, even when skimming.

> [!IMPORTANT]  
> Crucial information necessary for users to succeed.

> [!WARNING]  
> Critical content demanding immediate user attention due to potential risks.
```


> [!NOTE]  
> Highlights information that users should take into account, even when skimming.

> [!IMPORTANT]  
> Crucial information necessary for users to succeed.

> [!WARNING]  
> Critical content demanding immediate user attention due to potential risks.


```
> **Note**
> This is a note

> **Warning**
> This is a warning
```

> **Note**
> This is a note

> **Warning**
> This is a warning


```
> **⚠ WARNING: Aliens are coming.**  
> A description of the colour, smell and dangerous behaviour of the aliens.
```

> **⚠ WARNING: Aliens are coming.**  
> A description of the colour, smell and dangerous behaviour of the aliens.

```
| ⚠️ Warning                               | 
|------------------------------------------|
| You shouldn't. This is irreversible!     |

| ❌ Error                                 | 
|------------------------------------------|
| Don't do that. This is irreversible!     |

| ℹ️ Information                           | 
|------------------------------------------|
| You can do that without problem.         |

| ✅ Success                               | 
|------------------------------------------|
| Don't hesitate to do that.               |

| 🦄 New line support                       | 
|-------------------------------------------|
| It supports new lines:<br/>.. simply use `<br/>` for new lines|
```

| ⚠️ Warning                               | 
|------------------------------------------|
| You shouldn't. This is irreversible!     |

| ❌ Error                                 | 
|------------------------------------------|
| Don't do that. This is irreversible!     |

| ℹ️ Information                           | 
|------------------------------------------|
| You can do that without problem.         |

| ✅ Success                               | 
|------------------------------------------|
| Don't hesitate to do that.               |

| 🦄 New line support                                            |
| -------------------------------------------------------------- |
| It supports new lines:<br/>.. simply use `<br/>` for new lines |

```
!!! note

  Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
  nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
  massa, nec semper lorem quam in massa.
```

```
>[!WARNING]
>This is a warning
```
>[!WARNING]
>This is a warning

```
> [!NOTE]  
> Highlights information that users should take into account, even when skimming.
> [!IMPORTANT]  
> Crucial information necessary for users to succeed.
> [!WARNING]  
> Critical content demanding immediate user attention due to potential risks.
```

> [!NOTE]  
> Highlights information that users should take into account, even when skimming.


> [!IMPORTANT]  
> Crucial information necessary for users to succeed.


> [!WARNING]  
> Critical content demanding immediate user attention due to potential risks.



 
 























```
<font color="red">This text is red!</font>
```

<font color="red">This text is red!</font>


```
<p style="color:blue">Make this text blue.</p>
```

<p style="color:blue">Make this text blue.</p>


## Blockquotes

To create a blockquote, add a `>` in front of a paragraph.

```
> Dorothy followed her through many of the beautiful rooms in her castle.
```

The rendered output looks like this:

> Dorothy followed her through many of the beautiful rooms in her castle.

### Blockquotes with Multiple Paragraphs

Blockquotes can contain multiple paragraphs. Add a `>` on the blank lines between the paragraphs.

```
> Dorothy followed her through many of the beautiful rooms in her castle.
>
> The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.
```

The rendered output looks like this:

> Dorothy followed her through many of the beautiful rooms in her castle.
> 
> The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.

### Nested Blockquotes

Blockquotes can be nested. Add a `>>` in front of the paragraph you want to nest.

```
> Dorothy followed her through many of the beautiful rooms in her castle.
>
>> The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.
```

The rendered output looks like this:

> Dorothy followed her through many of the beautiful rooms in her castle.
> 
> > The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.

### Blockquotes with Other Elements

Blockquotes can contain other Markdown formatted elements. Not all elements can be used — you’ll need to experiment to see which ones work.

```
> #### The quarterly results look great!
>
> - Revenue was off the chart.
> - Profits were higher than ever.
>
>  *Everything* is going according to **plan**.
```

The rendered output looks like this:

> #### The quarterly results look great!
> 
> - Revenue was off the chart.
> - Profits were higher than ever.
> 
> _Everything_ is going according to **plan**.


>  **Tip:** Need to display backticks inside a code block? See [this section](https://www.markdownguide.org/basic-syntax/#escaping-backticks) to learn how to escape them.




