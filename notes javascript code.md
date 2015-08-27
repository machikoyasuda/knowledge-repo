## Code Conventions for the JavaScript Programming Language

http://javascript.crockford.com/code.html

http://google-styleguide.googlecode.com/svn/trunk/javascriptguide.xml#var

===

"All of our JavaScript code is sent directly to the public. It should always be of publication quality. Neatness counts."

- <script src=filename.js> placed as late in the body as possible
- Indentation = 4 spaces
- Avoid lines longer than 80 char
- Place break after comma and indent 8 spaces
- Comments: Focus on what is not immediately visible

## Variables

- Variables: All variables should be declared before used. Var statement should be first statements in function body, in alphabetical order, given its own line and comment.
- JavaScript does not have block scope, so defining vars in blocks can confuse programmers. Define all at the top.

## Function declarations

- All functions should be declared before they are used. Inner fxns should follow the var statement. 

- There should be no spaces between the name of a function and the ( of its paratmeter list. There should be one space between ) and {. The } is aligned with the line containing the begining of the declaration of the fxn.

function outer(c, d) {
    var e = c * d;
    
    function inner(a, b) {
        return (e * a) + b;
    }
    
    return inner(0,1);
}

## Anonymous functions
- If a function literal is anonymous, there should be one space between the word function and the (. If a space is omitted, then it can appear that the function's name is function, which is an incorrect reading.

div.onclick = function (e) {
    return false;
};

# Statements
- Each line should contain at most one statment. Put ; at the end of every simple statement.
- Assignments & invocations are the only expressions taht should be used as statements.

# Compound statements
- Compound statements are statements that contain lists of statements enclosed in {}
- Label: while, do, for, switch

# If
    if (condition) {         statements     }          if (condition) {         statements     } else {         statements     }          if (condition) {         statements     } else if (condition) {         statements     } else {         statements     }

# For

    for (initialization; condition; update) {
        statements
    }

    for (variable in object) {
        if (filter) {
            statements
        } 
    }

The first form should be used with arrays and with loops of a predeterminable number of iterations.
The second form should be used with objects. 

Be aware that members that are added to the prototype of the object will be included in the enumeration. It is wise to program defensively by using the hasOwnProperty method to distinguish the true members of the object:
    for (variable in object) {         if (object.hasOwnProperty(variable)) {             statements         }      }

# while Statement
A while statement should have the following form:
    while (condition) {         statements     }
    
# do Statement
A do statement should have the following form:
    do {         statements     } while (condition);
Unlike the other compound statements, the do statement always ends with a ; (semicolon).

# switch Statement
A switch statement should have the following form:
    switch (expression) {     case expression:         statements     default:         statements     }
Each case is aligned with the switch. This avoids over-indentation.
Each group of statements (except the default) should end with break, return, or throw. Do not fall through.

# try Statement
The try class of statements should have the following form:
    try {         statements     } catch (variable) {         statements     }      try {         statements     } catch (variable) {         statements    } finally {         statements     }
    
# === and !== Operators.

It is almost always better to use the === and !== operators. The == and != operators do type coercion. In particular, do not use == to compare against falsy values.

