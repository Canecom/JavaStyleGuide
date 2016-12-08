<img alt="Canecom" src="Images/Canecom_logo.png" width=100% />

# Java Style Guide

   - [Formatting](#formatting)
       - [Java source structure](#java-source-structure)
       - [Class structure](#class-structure)
       - [Modifier order](#modifier-order)
       - [Braces](#braces)
       - [WhiteSpaces](#whitespaces)
       - [Wrapping Lines](#wrapping-lines)
       - [Wrapping Class Declarations](#wrapping-class-declarations)
       - [Wrapping Method Declarations and Expressions](#wrapping-method-declarations-and-expressions)
       - [Variable Declarations and Annotations](#variable-declarations-and-annotations)
       - [Parentheses](#parentheses)
       - [Literals](#literals)
       - [Javadoc](#javadoc)
       
   - [Naming](#naming)
       - [Package names](#package-names)
       - [Class, Interface and Enum](#class-interface-and-enum)
       - [Method name](#method-name)
       - [Variables ](#variables)
       - [Constants ](#constants)
       

# Formatting

### Java source structure
-   copyright notice
-   package declaration
-   imports (no wildcard)
-   class declaration

### Class structure
-   fields
-   constructors
-   initializations
-   overriden methods with new functionality
-   new, not private methods
-   private methods
-   overriden methods with only super calls
-   static methods
-   abstract methods, other methods

### Modifier order
-   Access modifier (public / private / protected)
-   abstract
-   static
-   final
-   transient
-   volatile
-   default
-   synchronized
-   native
-   strictfp

### Braces
-   opening braces should be put on the end of the line and should followed by one empty line

-   There should be a new line in front of a closing brace unless the block is empty

-   Braces are recommended even where the language makes them optional, such as single-line if and loop bodies:

    -   If a block spans more than one line (including comments) it must have braces.
    
    -   If one of the blocks in a if / else statement has braces, the other block must too.
    
    -   If the block comes last in an enclosing block, it must have braces.
    
-   the else, catch and the while keyword in do…while loops go on the same line as the closing brace of the preceding block.

-   In some cases “short forms” that deviate from the above guidelines are just as readable and may be used instead. These cases include for instance simple enum declarations and trivial methods and lambda expressions.

<table>
<tr><th>SFW</th><th>NSFW</th></tr>
<tr>
<td><pre lang=java>
void method() {
    …
}

try {
    …
} catch (AnException e) {
    …
}

for (int[] row : matrix) {
    for (int val : row) {
        sum += val;
    }
}

enum Response { YES, NO, MAYBE }

public boolean isReference() { return true; }

}
</pre></td>
<td><pre lang=java>
// Wrong placement of opening brace
void method()
{
    …
}

// Newline in front of catch should be avoided
try {
    …
}
catch (AnException e) {
    …
}

// Braces should be used
if (flag)
    // Restore x
    x = 1;

// Use braces if block comes last in enclosing block
// to avoid accidentally indenting the closing brace.
for (int[] row : matrix) {
    for (int val : row)
        sum += val;
}

// Not a trivial method, more blocks
public boolean getResult() { int value = getValue(); return value &lt; 0 ? 0 : value; }

for (int i = 0; i &lt; size; i++) { sum += data[i]; }
</pre></td>
</tr>
</table>

### WhiteSpaces
-	Use 4 spaces for tabs.
-	Prefer indent using: Tabs
-	Tab width: 4
-	Indent width: 4
-	Tab key: Indents in leading whitespace

<table>
<tr><th>SFW</th><th>NSFW</th></tr>
<tr>
<td><pre lang=java>
switch (var) {
    case TWO:
        setChoice("two");
        break;
    case THREE:
        setChoice("three");
        break;
    default:
        throw new IllegalArgumentException();
}
</pre></td>
<td><pre lang=java>
switch (var) {
case TWO:
    setChoice("two");
    break;
case THREE:
    setChoice("three");
    break;
default:
    throw new IllegalArgumentException();
}
</pre></td>
</tr>
</table>

-	A single space should be used:

	-	To separate keywords from neighboring opening or closing brackets and braces
	
	-	Before and after all binary operators and operator like symbols such as arrows in lambda expressions and the colon in enhanced for loops (but not before the colon of a label)

 -	After // that starts a comment.

 -	After commas separating arguments and semicolons separating the parts of a for loop.

 -	After the closing parenthesis of a cast.

-	In variable declarations it is not recommended to align types and variables.

<table>
<tr><th>SFW</th><th>NSFW</th></tr>
<tr>
<td><pre lang=java>
int someInt;
String myString;
char aChar;
long sixtyfourFlags

if (isFlagSet(GO)) {
    …
}

IntUnaryOperator inc = x -&gt; x + 1;
</pre></td>
<td><pre lang=java>
int    someInt;
String myString;
char   aChar;
long   sixtyfourFlags;

if( isFlagSet( GO ) ) {
    …
}

IntUnaryOperator inc = x-&gt;x + 1;
</pre></td>
</tr>
</table>

### Wrapping Lines
-	Source code and comments should generally not exceed 100 characters per line, including indentation.

-	URLs or example commands should not be wrapped.

<table>
<tr><th>SFW</th></tr>
<tr>
<td><pre lang=java>
// Ok even though it might exceed max line width when indented.
Error e = isTypeParam
        ? Errors.InvalidRepeatableAnnotationNotApplicable(targetContainerType, on)
        : Errors.InvalidRepeatableAnnotationNotApplicableInContext(targetContainerType));
String pretty = Stream.of(args)
                      .map(Argument::prettyPrint)
                      .collectors(joining(", "));
</pre></td>
<tr><th>NSFW</th></tr>
<td><pre lang=java>
// Too strict interpretation of max line width. Readability suffers.
Error e = isTypeParam
        ? Errors.InvalidRepeatableAnnotationNotApplicable(
                targetContainerType, on)
        : Errors.InvalidRepeatableAnnotationNotApplicableInContext(
                targetContainerType);
// Should be wrapped even though it fits within the character limit
String pretty = Stream.of(args).map(Argument::prettyPrint).collectors(joining(", "));

</pre></td>
</tr>
</table>

-	There should be at most 1 statement per line.

<table>
<tr><th>SFW</th><th>NSFW</th></tr>
<tr>
<td><pre lang=java>
i += j;
j += k;
if (condition) {
    return expression;
}

</pre></td>
<td><pre lang=java>
i += j; j += k;
if (condition) { return expression; }

</pre></td>
</tr>
</table>

### Wrapping Class Declarations
-	A class header should not be wrapped unless it approaches the maximum column limit.

-	If it does, it may be wrapped before extends and/or implements keywords.

-	Declarations of type parameters may, if necessary, be wrapped the same way as method arguments

<table>
<tr><th>SFW</th><th>NSFW</th></tr>
<tr>
<td><pre lang=java>
public class MyGenericClass&lt;T, S&gt;
        extends HashMap&lt;T, S&gt;
        implements Comparable&lt;T&gt; {
    …
}
public class AnotherClass&lt;K, R&gt; implements Collector&lt;T extends K,
                                                     Set&lt;? extends R&gt;,
                                                     List&lt;R&gt;&gt; {
    …
}
</pre></td>
<td><pre lang=java>
public class MyGenericClass&lt;T&gt; implements Comparable&lt;T&gt;,
        Predicate&lt;T&gt; {
    …
}
</pre></td>
</tr>
</table>

### Wrapping Method Declarations and Expressions
- Method declarations can be formatted by listing the arguments vertically

<table>
<tr><th>SFW</th><th>NSFW</th></tr>
<tr>
<td><pre lang=java>
int someMethod(String aString,
               List&lt;Integer&gt; aList,
               Map&lt;String, String&gt; aMap,
               int anInt,
               long aLong,
               Set&lt;Number&gt; aSet,
               double aDouble) {
    …
}
</pre></td>
<td><pre lang=java>
// If aligning the parameters vertically, don't put two
// parameters on one line
int someMethod(String aString,
               List&lt;Integer&gt; aList,
               Map&lt;String, String&gt; aMap,
               int anInt, long aLong,
               Set&lt;Number&gt; aSet,
               double aDouble) {
    …
}
</pre></td>
</tr>
</table>

-	If a expression line approaches the maximum character limit, always consider breaking it down into multiple statements / expressions instead of wrapping the line.

-	Break expression  before operators.

-	Break expression before the . in chained method calls.

<table>
<tr><th>SFW</th><th>NSFW</th></tr>
<tr>
<td><pre lang=java>
methodCall(a * simple - formula,
           some + complex - formula * spanning
                        + multiple - lines * may
                        + look - as * follows); 

popupMsg("Inbox notification: You have "
        + newMsgs + " new messages");


persons.stream()
       .map(Person::getName)
       .forEach(System.out::println);
</pre></td>
<td><pre lang=java>
// Arity unclear
methodCall(a * simple - formula,
           some + complex - formula * spanning +
           multiple - lines * should + not *
           look - as * follows);
// Looks like two arguments
popupMsg("Inbox notification: You have " +
         newMsgs + " new messages");
persons.stream().
        map(Person::getName).
        forEach(System.out::println);

</pre></td>
</tr>
</table>

### Variable Declarations and Annotations
-	One variable per declaration (and at most one declaration per line)

-	Square brackets of arrays should be at the type (String[] args) and not on the variable (String args[]).

<table>
<tr><th>SFW</th><th>NSFW</th></tr>
<tr>
<td><pre lang=java>
public int var1;
public int var 2;
public String [] array;
</pre></td>
<td><pre lang=java>
public int var1, var 2;
public String array [];
</pre></td>
</tr>
</table>

-	Declaration annotations should be put on a separate line from the declaration being annotated.

-	Few/short annotations annotating a single-line method may however be put on the same line as the method if it improves readability.

-	Either all annotations should be put on the same line or each annotation should be put on a separate line.


<table>
<tr><th>SFW</th><th>NSFW</th></tr>
<tr>
<td><pre lang=java>
@Deprecated
@Override
public void foo() {
    …
}

addListener(new Listener() {
 
    // Ignored events
    @Override public void event1() { }
    @Override public void event2() { }
    @Override public void event3() { }
 
    // Important event
    @Override
    public void event4() {
        …
    }
});
</pre></td>
<td><pre lang=java>
@Override @Deprecated public void foo() {
    …
}

@Override @Deprecated
@SafeVarargs
public void foo() {
    …
}
</pre></td>
</tr>
</table>

### Parentheses
-	Redundant grouping parentheses (i.e. parentheses that does not affect evaluation) may be used if they improve readability.

-	Redundant grouping parentheses should typically be left out in shorter expressions involving common operators but included in longer expressions or expressions involving operators whose precedence and associativity is unclear without parentheses. Ternary expressions with non-trivial conditions belong to the latter.

-	The entire expression following a return keyword must not be surrounded by parentheses.

<table>
<tr><th>SFW</th><th>NSFW</th></tr>
<tr>
<td><pre lang=java>
return flag ? "yes" : "no";
String cmp = (flag1 != flag2) ? "not equal" : "equal";
</pre></td>
<td><pre lang=java>
return (flag ? "yes" : "no");
</pre></td>
</tr>
</table>

### Literals
-	long literals should use the upper case letter L suffix.

-	Hexadecimal literals should use upper case letters A-F.

-	All other numerical prefixes, infixes, and suffixes should use lowercase letters

<table>
<tr><th>SFW</th><th>NSFW</th></tr>
<tr>
<td><pre lang=java>
long l = 5432L;
int i = 0x123 + 0xABC;
byte b = 0b1010;
float f1 = 1 / 5432f;
float f2 = 0.123e4f;
double d1 = 1 / 5432d;  // or 1 / 5432.0
double d2 = 0x1.3p2;
</pre></td>
<td><pre lang=java>
long l = 5432l;
int i = 0X123 + 0xabc;
byte b = 0B1010;
float f1 = 1 / 5432F;
float f2 = 0.123E4f;
double d1 = 1 / 5432D;
double d2 = 0x1.3P2;
</pre></td>
</tr>
</table>

### Javadoc
-	Start longer comments with a short summarizing sentence since Javadoc includes this in the method summary table.

-	Prefer inline tags (such as {@code …} and {@link …} etc) over corresponding HTML tags (&lt;code&gt;…&lt;/code&gt;, &lt;a href="…"&gt;…&lt;/a&gt; etc).

-	Use &lt;p&gt; to separate paragraphs (closing &lt;/p&gt; tags are not needed and should not be used)

<table>
<tr><th>SFW</th><th>NSFW</th></tr>
<tr>
<td><pre lang=java>
/** A short javadoc comment */

/**
 * …
 *
 * &lt;blockquote&gt;{@code
 *     List&lt;String&gt; names;
 * }&lt;/blockquote&gt;
 */
</pre></td>
<td><pre lang=java>
/** put on single line instead
 */

/**
 * The &lt;String&gt; below may interfere with the HTML!
 *
 * &lt;blockquote&gt;&lt;pre&gt;
 *     List&lt;String&gt; names;
 * &lt;/pre&gt;&lt;/blockquote&gt;
 *
 */
 </pre></td>
</tr>
</table>

# Naming

### Package names
<table>
<tr><th>SFW</th><th>NSFW</th></tr>
<tr>
<td><pre lang=java>
com.canecom.network
</pre></td>
<td><pre lang=java>
com.canecom.Network
com.Canecom.network
com.canecom._network
 </pre></td>
</tr>
</table>

### Class, Interface and Enum
-	Class and enum names should typically be nouns.

-	Interface names should typically be nouns or adjectives ending with …able.

-	Use mixed case with the first letter in each word in upper case.

-	Use whole words and avoid using abbreviations unless the abbreviation is more widely used than the long form.

-	Format an abbreviation as a word if the it is part of a longer class name.

<table>
<tr><th>SFW</th><th>NSFW</th></tr>
<tr>
<td><pre lang=java>
class EmptyCell {
}
interface Expandable {
}
class XmlParser {
}
</pre></td>
<td><pre lang=java>
class Empty {
}


// Abbreviation should be formatted as 'Xml'
class XMLParser {
}
 </pre></td>
</tr>
</table>

### Method name
-	Method names should typically be verbs or other descriptions of actions.

-	Use mixed case with the first letter in lower case.

<table>
<tr><th>SFW</th><th>NSFW</th></tr>
<tr>
<td><pre lang=java>
public void expand() {
    …
}

public boolean isExpanding() {
    …
}
public State getState() {
    …
}
</pre></td>
<td><pre lang=java>
public boolean expanding() {
    …
}
public State GetState() {
    …
}
public int get_index() {
    …
}
 </pre></td>
</tr>
</table>

### Variables
-	names should be in mixed case with the first letter in lower case, except static not constant variables should be started with s

<table>
<tr><th>SFW</th><th>NSFW</th></tr>
<tr>
<td><pre lang=java>
int currentIndex;
boolean dataAvailable;
</pre></td>
<td><pre lang=java>
int current_index;
boolean DataAvailable;
 </pre></td>
</tr>
</table>

### Constants 

<table>
<tr><th>SFW</th><th>NSFW</th></tr>
<tr>
<td><pre lang=java>
public static final int BUFFER_SIZE = 1024;
enum ApplicationMode { RUNNING, PAUSED, TERMINATED }
</pre></td>
<td><pre lang=java>
public final List&lt;String&gt; CURRENT_WORDS = new ArrayList&lt;&gt;();
enum ApplicationMode { Running, Paused, Terminated }
 </pre></td>
</tr>
</table>


