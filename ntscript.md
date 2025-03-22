## NTScript Documentation
> **Note:** This Documentation assumes you know some JavaScript

NTScript is a JavaScript Based Programming Language. Its part of the ecosystem of NTML which is based in HTML.

## The temp keyword
This keyword (temp) behaves like var but with a duration in milliseconds of how long it will last before it deletes.

    temp example = "This variable will be deleted" 1000
After the value, the duration is entered, Like const, temp can't start without a value

## Deleting Variables
To delete variables you use the keyword "delete", It can delete "var", "let", "const", "temp" and variables that aren't made with a keyword.

    var example = "This will be deleted!"
    delete example
    if (example) {
	    console.log("example still exists")
    } else {
	    console.log("example doesn't exist now")
    }

## The perm keyword
The perm keyword behaves almost the same as "let". With the difference it can't be deleted.

    perm permvar = "This variable can't be deleted!"
    delete permvar // Uncaught TypeError: Can't delete "perm" variable
   But it can be reassigned
   

    perm permvar = "This variable can't be deleted!"
    permvar = "But it can be reassgined"
    console.log(permvar) //Output: But it can be reassgined
You can combine the perm keyword with const to make "perm const" and it will not be able to be modified and neither be deleted, Useful for Core Functions

    perm const coreFunc = ()=>{
    console.log("This is a Core Function that can't be deleted and neither reassgined")
    }
    delete coreFunc // Uncaught TypeError: Can't delete "perm" variable
    coreFunc = ()=>{ // Uncaught TypeError: invalid assignment to const 'coreFunc'
    console.log("Overwroten")
    }

## Making Custom Operators
NTScript supports making custom operators using "createOperator()"
The first argument is the operator symbol, This can't be an already existing one including custom ones,
The second argument is a function, its given the 2 operands as arguments,
The third argument is a Object and optional, And it defines order. Its used something like {"+":"before","-":"after"}

    createOperator("°",(one,two)=>{
    return one * two * two
    })
    console.log(4 ° 4) // 64
Custom operators can't overwrite existing operators. Doing multiple characters is allowed. If the third argument isn't putted, It will do by order
