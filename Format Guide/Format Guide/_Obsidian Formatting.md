# Format Notes Quick Guide
#### Contents:
- [[#Headers]]
- [[#Emphasis]]
- [[#Create code blocks]]
	- [[#Supported Code Specifiers]]
- [[#Internal Links and Pictures]]
- [[#Blockquotes]]
- [[#Math and Symbols]]
	- [[#Guide |Math Guide]]
		- [[#Special Characters or Symbols]]
		- [[#Summations and Integrals]]
		- [[#Parentheses Size Scaling]]
		- [[#Font Change for Special Functions]]
		- [[#Aligned Equations and Piecewise Functions]]
		- [[#Font Size for Equations]]
- [[#Tables]]

---
## Headers

```md 
# Header level 1
## Header level 2
### Header level 3
#### Header level 4
##### Header level 5

--- creates a line acroos the page
```

# Header level 1
## Header level 2
### Header level 3
#### Header level 4
##### Header level 5

---
- Above is the line created

## Emphasis
^d7679f
```md
*Italics*
_Also Italics_

**Bold**
__Also Bold__

**Easy to _combine_ the two**

_Using **the opposite** notation_

You can also ==highlight text==.
```
*Italics*
_Also Italics_
**Bold**
__Also Bold__
**Easy to _combine_ the two**
_Using **the opposite** notation_
You can also ==highlight text==.

- Using CMD+B (Mac) / Control + B (Windows) still makes text bold and will generate bold format
	- Same applies to Italics

## Create code blocks
```md 
Text inside a single set of `backticks` will create in line code
```

Text inside a single set of `backticks` will create in line code

<pre><code>
To create code blocks use the following syntax:

```(language specifier)
*code*
```
</code></pre>
```md
- Language specifier is the programming language used
- Includes color highlighting
- Make language specifier "md" for text file
- To escape the ``` characters like this block use:

<pre><code>```(specifier)
*text*
```</code></pre>

- Example below is a java code snippet
```

<pre><code>```java
public class JavaFile {
	public static void main(String[] args) {
		System.out.println("This is java code");
	}
}
```</code></pre>
```java
public class JavaFile {
	public static void main(String[] args) {
		System.out.println("This is java code");
	}
}
```
#### Supported Code Specifiers
- Java: java
- JavaDoc: javadoc
- C: c
- C++: cpp
- JavaScript - javascript / js
- Regex - regex
- Ruby - Ruby / rb
- Python - python / py
- [Link to full list](https://prismjs.com/#supported-languages)

## Internal/External Links and Pictures
```md
General: [[Where you want to link]]
Embed Link: ![[What to embed]]

Obsidian will show options when inserting an internal link which will make it easier than typing it out.

Syntax:
Link to Note: [[TestImage.jpeg]]
	- Links to the note with the test image in it

Link to Heading: [[#Headers]]
	- Links to the Headers heading

Link to Block: [[#^d7679f]](Link)
	- Links to the emphasis block

External Link to Website: [Display Text](URL)
	- [Link to full list](https://prismjs.com/#supported-languages)
	- Link in previous section that goes to supported code block languages

Display alternate text: [Link to Note](TestImage.jpeg)
	- Links to the same TestImage.jpeg

Embed a Picture:
	- Can use this to embed other notes and PDFs
![[TestImage.jpeg]]

Embed a Picture changing size: 
	- Changes picture size to 200 pixels wide, automatic scaling
![[TestImage.jpeg|200]]

```

Link to Note: [[TestImage.jpeg]]
	- Links to the note with the test image in it

Link to Heading: [[#Headers]]
	- Links to the Headers heading

Link to Block: [[#^d7679f]]
	- Links to the emphasis block

Display alternate text: [Link to Note](TestImage.jpeg)
	- Links to the same TestImage.jpeg

Embed a Picture:
	- Can use this to embed other notes and PDFs
	- Put pictures to embed into Attachments folder
![[TestImage.jpeg]]

Embed a Picture changing size: 
	- Changes picture size to 200 pixels wide, automatic scaling
![[TestImage.jpeg|200]]

## Blockquotes
```md
> This is a block quote. It is a very long quote that spans multiple lines. Similar to when you need to indent for MLA formatting when a quote gets to be more than 4 lines, but this just can also be used to place emphasis on a block of text.
```

> This is a block quote. It is a very long quote that spans multiple lines. Similar to when you need to indent for MLA formatting when a quote gets to be more than 4 lines, but this just can also be used to place emphasis on a block of text.

## Math and Symbols
- Obsidian uses [Mathjax](http://docs.mathjax.org/en/latest/basic/mathjax.html) to display math operations
- Use dollarsigns to surround the math operation
	- `$Likethis$`
	- Use Curly Braces to group items
	- Use ^ for superscript
	- Use _ for subscript
	- Can have a space between command and input
		- `$\frac 1x$` = `$\frac1x$` = $\frac 1x$  
	- { }, $, and % need escape characters
	- To make letters appear as text use `\text{text}`
		- $\text{This is text}\ This is not text$	

### Guide: 
---
###### **Exponenets:** 
$2^5$ `$2^5$`

###### **Logarithms:** 
$log_3(x)$  `$log_3(x)$`

###### **Fractions:** 
$\frac 12$ `$\frac 12$`
- Complex fractions: $\frac{x+1}{x-1}$ `$\frac{x+1}{x-1}$`
- More Complex fractions: ${(n+1)^2-\frac{n!}{2^{n+1}} \over 2^{n+1}+(n+3)!}$ 
	- `${(n+1)^2-\frac{n!}{2^{n+1}} \over 2^{n+1}+(n+3)!}$`

###### **Spaces:**
- Use `\ ` for an extra space (backslash before space)
		- Wrong: $x y$ = `$x y$`  
		- Right: $x\ y$ = `$x\ y`
- Use `\quad` for large space: 
		- $4\quad *\quad 5$  `$4\quad *\quad 5$`  
- Use `\qquad` for larger space: 
		- $4\qquad *\qquad 5$  `$4\qquad *\qquad 5$``

###### **Special Characters or Symbols:**
- Greek Letters:  $\alpha\ \Omega\ \delta\ \Delta\ \pi$ 
	- `$\alpha\ \Omega\ \delta\ \Delta\ \pi$`
	- Simply the name of the letter
	- Use a capital letter for the capital version of the letter
- *Infinity:* $\infty$ `\infty`
- Arrow: $\to$ `\to`
- is in: $\in$ `\in`
- Is not in: $\notin$ `\notin`
- Multiplication: $\times$ `\times`
	- Can also just use *
- Division: $\div$ `\div`
- Plus or minus: $\pm$ `\pm`
	- Minus or plus: $\mp$ `\mp`
- Centered dot: $x\cdot y$ `x\cdot y`
- To Make Symbols **Bold**
	-  $\boldsymbol\alpha$ vs $\alpha$ 
	- Use `\boldsymbol\symbolname`
		- $\boldsymbol\sigma$  vs $\sigma$ 
		- `\boldsymbol\sigma`

###### **Radicals:** 
$\sqrt x$ `$\sqrt x$`
- Roots other than 2: $\sqrt[3]{\frac xy}$   `$\sqrt[3]{\frac xy}$`

###### **Comparisons:** 
- $\lt$ `\lt`
- $\gt$ `\gt`
- $\leq$ `\leq`
- $\geq$ `\geq`
- $\neq$  `\neq`

###### Summations and Integrals: 
$\sum_{i=0}^\infty i^2$  `$\sum_{i=0}^\infty i^2$`

$\prod _{i=0}^{k-1}4^i$ `$\prod _{i=0}^{k-1}4^i$`

 $\int_0^\infty e^x\ dx$  `$\int_0^\infty e^x\ dx$`
 
###### **Limits:**
$\lim_{x\to 0} \frac 1x$ `$\lim_{x\to 0} \frac 1x$`

###### **Overhead Characters:** 
- Carrot / hat: $\hat x$ `$\hat x$`
- Wider carrot: $\widehat {xy}$ `$\widehat {xy}$`
- Bar (or NOT operator) $\bar x$ `$\bar x$`
- Wide bar: $\overline {xyz}$ `$\overline {xyz}$`
	- Boolean logic ex: $\overline {x\bar y z}$ `$\overline {x\bar y z}$`
- Vector: $\vec x$ `$\vec x$`
- Longer Vector: $\overrightarrow {2xyz}$ `$\overrightarrow {2xyz}$`
- Two way arrow: $\overleftrightarrow {xy}$ `$\overleftrightarrow {xy}$`

###### **Parentheses Size Scaling**
- Use to scale Parentheses, Brackets, and Curly Braces
	- Remember to use escape char on curly braces
- `\left` and `\right` automatically adjust to formula height
	- No adjustment: $3({(n+1)^2-\frac{n!}{2^{n+1}} \over 2^{n+1}+(n+3)!})$`
	- Adjustment  $3\left ({(n+1)^2-\frac{n!}{2^{n+1}} \over 2^{n+1}+(n+3)!} \right)$ 
		- `$3\left ({(n+1)^2-\frac{n!}{2^{n+1}} \over 2^{n+1}+(n+3)!} \right)$`
		- `\right` goes *inside* the parenthesis
- If not using a forumala can use the following (from smallest to largest)
	- `\bigl` and `\bigr` 
	- `\Bigl` and `\Bigr` 
	- `\biggl` and `\biggr` 
	- `\Biggl` and `\Biggr`
- The encolser being used `()` or `[]` or `{}` needs to follow the command
- **Size comparison**
	- $\Biggl(\biggl(\Bigl(\bigl((x)\bigr)\Bigr)\biggr)\Biggr)$  $\Biggl\{\biggl\{\Bigl\{\bigl\{\{x\}\bigr\}\Bigr\}\biggr\}\Biggr\}$ $\Biggl[\biggl[\Bigl[\bigl[[x]\bigr]\Bigr]\biggr]\Biggr]$
- Can be used on `\lceil` / `\rceil` and `\lfloor` / `\rfloor` as well
	- $\lceil {2x} \rceil$ `$\lceil {2x} \rceil$`
	- $\lfloor {2x} \rfloor$  `$\lfloor {2x} \rfloor$`

###### Center Equations
- Use two dollar signs instead of one to center the equation into an equation block
- Works like a code snippet
$$\sum_{i=0}^\infty i^2$$
Above code: `$$\sum_{i=0}^\infty i^2$$`

###### **Set Notation and Symbols from Discrete Math:**
- Union: `\cup` $\cup$ 
- Intersection: `\cap` $\cap$ 
- Subset: `\subset` $\subset$
- Subset equals: `\subseteq` $\subseteq$
- Subset not equals: `\subsetneq` $\subsetneq$ 
- Empty set: `\emptyset` $\emptyset$
- Null set: `\varnothing` $\varnothing$ 
- **Choose notation:** ${n+1 \choose 2k}$ 
	- `{n+1 \choose 2k}`
	- `binom{n+1}{2k}`
- **_Discrete Math Symbols_**
	- Implies: $\implies$ `\implies`
	- If and only if: $\iff$ `\iff`
	- AND: $\land$ `\land`
	- OR: $\lor$ `\lor`
	- NOT: $\lnot$ `\lnot`
	- For all: $\forall$ `\forall`
	- There exists: $\exists$ `\exists`

###### **Font Change for Special Functions**
- Some functions have a command so they stand out with a different font
- EX: $\sin(x)$ vs. $sin(x)$ 
	- Sine: `\sin`
	- Cosine: `\cos`  
	- Natural Log (ln): `\ln`
	- Logarithms: `\log_2(x)` 
		- $\log_2(x)$ 
	- Max and min: `\max` and `\min` 
		- $\max(5,6)$ and $\min(x,y)$ 
- Can also set with non-standard functions
	- $\operatorname{foo}(x)$ `$\operatorname{foo}(x)`
		- Not changed: $foo(x)$ 

###### Aligned Equations and Piecewise Functions
- To align equations to show solving steps
	- Use `\begin{align} ... \end{align}`
	- Each line should end with `\\` and should contain an ampersand `&` at the point to align the text.
	- Ex:
$\begin{align} \operatorname{F}(n) & = \frac{(n+5)!\ \cdot\ 2^{n+3}} {(n+4)!\ \cdot\ 2^{n+4}}\\ & = \frac{(n+5)(n+4)!\ \cdot\ 2^{n+3}} {(n+4)!\ \cdot\ 2^{n+4}}\\  & = \frac{(n+5)\ \cdot\ 2^{n+3}} {2^{n+4}}\\ & = \frac{(n+5)\ \cdot\ 2^{n+3}} { 2\ \cdot\ 2^{n+3}}\\ & = \frac{n+5}{2}\end{align}$

Code:
```
$\begin{align} 
\operatorname{F}(n) & = \frac{(n+5)!\ \cdot\ 2^{n+3}} {(n+4)!\ \cdot\ 2^{n+4}}\\ 
	& = \frac{(n+5)(n+4)!\ \cdot\ 2^{n+3}} {(n+4)!\ \cdot\ 2^{n+4}}\\  
	& = \frac{(n+5)\ \cdot\ 2^{n+3}} {2^{n+4}}\\ 
	& = \frac{(n+5)\ \cdot\ 2^{n+3}} { 2\ \cdot\ 2^{n+3}}\\ 
	& = \frac{n+5}{2}
\end{align}$
```

- ###### Definitions by Cases
- This can also be used for piecewise functions,  recursive functions, etc...
- Use for Piecewise functions, recursive functions, etc...
- Use `\begin{cases} ... \end{cases}`
- End each case with a `\\`
- Use `&` for parts that should be aligned
- Ex:

$\operatorname{T}(n)\ =\ \begin{cases} \qquad 1, & \text{if }n \lt 4 \\ 3\operatorname{T}(\frac n2)+1, & \text{if } n \geq 4 \end{cases}$

Code:
```
$\operatorname{T}(n)\ =\ 
\begin{cases} 
\qquad 1, & \text{if }n \lt 4 \\ 
3\operatorname{T}(\frac n2)+1, & \text{if } n \geq 4 
\end{cases}$
```

###### Font Size for Equations
In order from smallest to largest, can use `\command{equation}` to make equation larger
- `\large`
- `\Large`
- `\LARGE`
- `\huge`
- `\Huge`

Showcase order: Normal, large, Large, LARGE, huge, Huge

${\frac 1 2}$ $\large{{\frac 1 2}}$ $\Large{{\frac 1 2}}$ $\LARGE{{\frac 1 2}}$ $\huge{{\frac 1 2}}$ $\Huge{{\frac 1 2}}$ 

###### Matrices
Can make matrices by using `\begin{bmatrix}` and end with `\end{bmatrix}`
- Terminate row with `\\`
$\begin{bmatrix}a\ b\\c\ d\end{bmatrix}$
- `\begin{bmatrix}a\ b\\c\ d\end{bmatrix}`

## Tables
To create a Table
- Make the header row by separating columns with a pipe `|`
- Put hyphens `-` underneath the first row, with a pipe to separate columns still
- Insert data into the table, again separting columns with a pipe
- **LIVE PREVIEW WILL NOT SHOW COMPLETED TABLE**
	- To see completed table, switch to read-only mode
- EX:

First Header | Second Header
------------ | ------------
Content from cell 1 | Content from cell 2
Content in the first column | Content in the second column



