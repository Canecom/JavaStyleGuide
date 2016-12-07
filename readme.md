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

-   Braces are recommended even where the language makes them optional, such as single-line if and loop bodies.
    o   If a block spans more than one line (including comments) it must have braces.
    o   If one of the blocks in a if / else statement has braces, the other block must too.
    o   If the block comes last in an enclosing block, it must have braces.
    
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
TBD

### Wrapping Lines
TBD

### Wrapping Class Declarations
TBD

### Wrapping Method Declarations and Expressions
TBD

### Variable Declarations and Annotations
TBD

### Parentheses
TBD

### Literals
TBD

### Javadoc
TBD


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

