---
date: 2016-09-09T10:24:16-04:00
title: Working with Vue.JS Directives
---


Working with Vue.JS Directives

What are directives?
Directives are tiny commands that we put on dom elements.  
There are 2 types of directives, built-in directives and custom directives.  In General, a built-in directive starts with v-.  For example v-if, v-text, v-html.
Creating a custom directive is relatively easy.  A directive has 5 methods that you can use with your custom directive.

<img src="/tmoodley/strata-cms-template/blob/master/site/static/images/hooks.jpg?raw=true" alt="hooks.jpg">
 
The first method Bind gives us access to the element, methods, and virtual node.  In the code below we can access the style property of the element being passed in.  In this case, we access the backgroundColor attribute and set it to the value element.
 
<img src="/tmoodley/strata-cms-template/blob/master/site/static/images/v-directives.jpg?raw=true" alt="v-directives.jpg">
 
When building custom directives, you have to know the difference between:
•	binding.arg – this is the value you pass after the dot such as v-customdirective.click = “click”
•	binding.value – this is the value you pass directly such as v-customdirective.click = “click”
One of the most powerful features of custom directives is that it gives you direct DOM access via the first arguments (el).  This will allow you to run any javascript function with a HTML element.
Let’s build a custom directive that will replace the v-on built in directive using the binding.value and binding.arg method.
Below we will replace the v-on:click built in directive:
<button v-customdirective:click="clicked" class="btn btn-primary">Click Me</button>
<script>
    export default {
        directives: {
            customdirective: {
                bind(el, binding) { 
                    const type = binding.arg;
                    const fn = binding.value;
                    el.addEventListener(type, fn);
                }
            }
        },
        methods: {
            clicked() {
                alert('I was clicked!');
            } 
        }
    }
</script>

Official Docs - Custom Directives: http://vuejs.org/guide/custom-directive.html

