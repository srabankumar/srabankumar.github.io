---
layout: post
title: "'this' keyword under the hood in javascript"
date: 2018-06-21 11:59:25 +0530
comments: true
categories: this,javascript
---
Hi Friends,
    In this post we will discuss about 'this' keyword in javascript and how it works in javascript. I will try to make this post as simple as possible. let's jump into it .
    
###concept-1
    
    
When we are declaring a variable or function in javascript it became a property of window object . In the global excution context 'this' keyword always refer to 'window' object. so example: 
     
        var a = 'javascript';
        console.log(a) // javascript
        console.log(window.a) // javascript
        console.log(this.a) // javascript
        function xyz(){
            console.log(this.a) 
        }
        xyz() // javascript
     
     
###concept-2

"this" keyword inside a method always refers to calling object .Example:

        var obj = {
                name:'javascript',
                print : function(){
                    console.log(this.name)
                }
            }
            obj.print(); // javascript
    
Here object 'obj' is calling 'print' method. so 'this' keyword inside print will refer to object 'obj' .
     
###concept-3

   When we are using a inner function inside a method then 'this' keyword inside that inner function refers to 'window' object, not calling object.
   
Example:
     
        var name = 'window';
        var obj = {
                name:'javascript',
                print : function(){
                    return function(){
                        console.log(this.name)
                    }
                }
            }
            obj.print()(); // window 
     
>Then how to fix this . 

We have to assign 'this' object to some other object inside print function.Now
     
        var name = 'window';
        var obj = {
                name:'javascript',
                print : function(){
                    var self = this // here we assigned "this" object to self object.
                    return function(){
                        console.log(self.name)
                    }
                }
            }
            obj.print()(); // javascript
            
I hope these three concepts are clear now. 

Happy Coding :)
     
     
    
    
