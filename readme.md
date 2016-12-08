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
public boolean getResult() { int value = getValue(); return value < 0 ? 0 : value; }

for (int i = 0; i < size; i++) { sum += data[i]; }
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

IntUnaryOperator inc = x -> x + 1;

</pre></td>
<td><pre lang=java>
int    someInt;
String myString;
char   aChar;
long   sixtyfourFlags;

if( isFlagSet( GO ) ) {
    …
}

IntUnaryOperator inc = x->x + 1;

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
public class MyGenericClass<T, S>
        extends HashMap<T, S>
        implements Comparable<T> {
    …
}
public class AnotherClass<K, R> implements Collector<T extends K,
                                                     Set<? extends R>,
                                                     List<R>> {
    …
}
</pre></td>
<td><pre lang=java>
public class MyGenericClass<T> implements Comparable<T>,
        Predicate<T> {
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
               List<Integer> aList,
               Map<String, String> aMap,
               int anInt,
               long aLong,
               Set<Number> aSet,
               double aDouble) {
    …
}
</pre></td>
<td><pre lang=java>
// If aligning the parameters vertically, don't put two
// parameters on one line
int someMethod(String aString,
               List<Integer> aList,
               Map<String, String> aMap,
               int anInt, long aLong,
               Set<Number> aSet,
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
TBD

<table>
<tr><th>SFW</th><th>NSFW</th></tr>
<tr>
<td><pre lang=java>

</pre></td>
<td><pre lang=java>

</pre></td>
</tr>
</table>

### Parentheses
TBD

<table>
<tr><th>SFW</th><th>NSFW</th></tr>
<tr>
<td><pre lang=java>

</pre></td>
<td><pre lang=java>

</pre></td>
</tr>
</table>

### Literals
TBD

<table>
<tr><th>SFW</th><th>NSFW</th></tr>
<tr>
<td><pre lang=java>

</pre></td>
<td><pre lang=java>

</pre></td>
</tr>
</table>

### Javadoc
TBD

<table>
<tr><th>SFW</th><th>NSFW</th></tr>
<tr>
<td><pre lang=java>

</pre></td>
<td><pre lang=java>

</pre></td>
</tr>
</table>

# Naming

### Package names
TBD

### Class, Interface and Enum
TBD

### Method name
TBD 

### Variables
TBD

### Constants 
TBD

