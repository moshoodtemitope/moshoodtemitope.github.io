---
layout: posts
title: "The art of Javascript Async-Await "
date: 2017-11-12
categories: javascript 
tags: javascript
ispageApost : true
comments: true
isJsPost: true
---

<p>
    Javascript by default is <em> single threaded </em>(one line of code executes at a time), the script is executed in the order in which the lines of codes appear. This flow comes with several limitations. For instance, we have a basic snippet below: 
</p>
{% highlight javascript %}
const syncCode = () => {
    console.log('This is line 1'); //line 1
    console.log('This is line 2'); //line 2
}
{% endhighlight %} 
<p> 
    Synchronous means line 2 <em> cannot </em> start executing until after line 1 has finished executing. 
</p>
<h3 class="sub-section-title">A deeper illustration</h3>
<p>
    We need to execute a function <em>showUsers</em> only after the function <em>addUser</em>  has been successfully executed. While <em>addUser</em> is being executed, we want to be able to execute other portions of the script. A portion of the <em>showUsers</em> function depends on the <em>addUser</em> function.
</p>
<p>
    The problem is that the function <em>addUser</em> could take some time before completely executing, while we <em>wait</em> for the result of <em>addUser</em>, we dont want other portions of the script to be blocked from executing. Also, we don't want the <em>showUsers</em> function generating unwanted results.
</p>
<p id="my-element">
{% highlight javascript %}
let userData = [{name: 'Karl Max', age: 32, profession:'teacher', taxId: 'e312' }];

const addUser = (time) => {
    setTimeout(function(){ // wait 2500milliseconds then push a new object 
        userData.push({name: 'Johhn Doe ', 
        age: 44, profession: 'doctor',
        taxId: 'e422'});
    }, time);
}

const showUsers = () =>{
    addUser(2500);
    console.log(`All users:\n ${JSON.stringify(userData)}`);
}

showUsers();

{% endhighlight %} 
</p>
<p>
We execute the snippet above,  and the function <em>showUsers</em> is called. Oh yeah!, we expect the output of <em>showUsers</em> to give us an updated version of <em>userData</em> since we are calling <em>addUser</em>  before displaying the updated <em>userData</em>. Run the snippet above in your browser console. 
</p>
<h5 class="paragraphy-heading">The result after we run the snippet above</h5>
{% highlight html %}
All users:
[{"name":"Karl Max","age":32,"profession":"teacher","taxId":"e312"}]
{% endhighlight %} 
<p>There is a problem here, we need to be able to delay the execution of some section of our code if this section is dependent on some execution whose result might not be immediately available. <em>showUsers</em> excutes the console statement without regards to whether <em>addUser</em> is done adding the new user data. However, <em>showUsers</em> is unable to get the updated data from <em>addUser</em> at the moment the console statement is being executed.</p>
<p>Initially, Callbacks were the solution considered to ensure that dependency on some section of code doesn't cause a function to yield unexpected results. We pass the dependent function as a parameter to the function it depends on, then we call the dependent function inside the function it depends on. This is illustrated below.</p>

<p>
{% highlight javascript %}
let userData = [{name: 'Karl Max', age: 32, profession:'teacher', taxId: 'e312' }];

/* we pass the dependent function
to the function it depends on */
const addUser = (time, callback) => { 
    setTimeout(()=>{ 
        userData.push({name: 'Johhn Doe ', 
        age: 44, profession: 'doctor',
        taxId: 'e422'});

        /* we call the dependent function inside the function it depends on */
	callback(); 

    }, time); 
} 
 
const showUsers = () =>{
    console.log(`All users:\n ${JSON.stringify(userData)}`); 
}
addUser(2500, showUsers);
{% endhighlight %}
</p>
<h5 class="paragraphy-heading">The result after we run the snippet above</h5>
{% highlight html %}
All users:
 [{"name":"Karl Max","age":32,"profession":"teacher","taxId":"e312"},{"name":"Johhn Doe ","age":44,"profession":"doctor","taxId":"e422"}]
{% endhighlight %} 
<p>
 This becomes tedious to maintain and can be difficult to read or understand when several levels of callback nesting are required. This was the case when Javascript ES5 was the best acceptable standard. 
</p>
<p>
ES6/ES2015 came with Promises, an alternative to callbacks which made it more comfortable to write maintainable   chained(dependent) asynchronous flows such as our illustration without running into the problem nested callbacks causes.
Promises ensure callbacks will not be called until the current execution has completed. There was also an improvement in the usage of mulitple callbacks which saved us the stress of callback nesting.
</p>

<h5 class="paragraphy-heading">Re-writing our illustration with Promises goes thus: </h5>

{% highlight javascript %}
let userData = [{name: 'Karl Max', age: 32, profession:'teacher', taxId: 'e312' }];
const addUser =  (time) => {
  return new Promise(resolve => {
    setTimeout(() => {
      userData.push({name: 'Johhn Doe ',age: 44,
        profession: 'doctor',
        taxId:'e422'});
      resolve (JSON.stringify(userData));
    }, time);
  });
}

const showUsers = (res) =>{
    console.log(`All users:\n ${res}`); 
}

addUser(2500).then(res => showUsers(res));
{% endhighlight %} 
<h5 class="paragraphy-heading">The result after we run the snippet above</h5>
{% highlight html %}
All users:
 [{"name":"Karl Max","age":32,"profession":"teacher","taxId":"e312"},{"name":"Johhn Doe ","age":44,"profession":"doctor","taxId":"e422"}]
{% endhighlight %} 
<p>Our code looks cleaner and more readable with the introduction of Promises. Also adding multiple callbacks becomes easier with the chaining feature of promises, which is applied by appending <em>.then(callbackFunction)</em> for each callbacks after the function that returns a promise as thus: <em>addUser().then(callback).then(callback)</em> </p>
<p>A flaw with promises is that it becomes difficult to maintain multiple callbacks. This results from several expressions and nesting of callbacks.</p>

<h3 class="sub-section-title">Meet Javascript Async-Await</h3>
<p>Introduced as part of ES2017 Implementation is the use of <em>Async</em> functions which allows us to write asynchronous-based code to be readable as though they are synchrounous code. A base syntax to use the Async-await feature is illustrated thus:  </p>
{% highlight javascript %}
async function tryAsync(){

    /* aPromiseFunction() is a function that returns a promise */
    const valueFromPromise = await aPromiseFunction(); 
}
{% endhighlight %} 
<p>The <em>async</em> and <em>await</em> keywords work together in such a way that placing <em>async</em> before any <em>function</em> declaration defines the function as an asynchronous function. Regardless of whether the <em>await</em> is used inside an async function, the async function will always return a promise. The promise returned resolves with whatever the async function returns.</p>

{% highlight javascript %}
async function tryAsync(){

    /* aPromiseFunction() is a function that returns a promise */
    const valueFromPromise = await aPromiseFunction();  
    return 'value from async';
}

//Arrow functions version
const tryAsync = async () =>{

    /* aPromiseFunction() is a function  that returns a promise */
    const valueFromPromise = await aPromiseFunction(); 
    return 'value from async';
};
{% endhighlight %} 
<p> <em>tryAsync()</em> returns a promise which is fulfilled with <em>'value from async'</em>. The execution of an async function is paused whenever an <em>await</em> expression is encountered till the promise in the await expression has been resolved.</p>
<h5 class="paragraphy-heading">Re-writing our userData illustration with Async-Await goes thus: </h5>
<iframe height='300' scrolling='no' title='The art of Javascript Async-Await' src='//codepen.io/moshoodtemitope/embed/bvdVWJ/?height=300&theme-id=32804&default-tab=js,result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='https://codepen.io/moshoodtemitope/pen/bvdVWJ/'>The art of Javascript Async-Await</a> by Moshood Temitope (<a href='https://codepen.io/moshoodtemitope'>@moshoodtemitope</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>
<p>The usage of Async-Await provides a neatly refined version of the <em>addUser</em> illustration, the promise returned by <em>addUser()</em> is waited for with <em>await addUser()</em> inside the <em>showUsers()</em> function. Also, because <em>showUsers()</em> returns a promise which resolves to a return value of: ( JSON.stringify(userData, null, ' ') ), we can chain and easily maintain more callbacks. </p>
<p> <h5 class="paragraphy-heading">Parallelism with Async-Await</h5></p>
<p>Considering the following snippet, we want to await two asynchronous function calls at the same time.</p>
{% highlight javascript %}
async function twoAsyncs(){

    /* awaiting a promise from someAsync for 1000ms */
    const someAsyncValue = await someAsync(1000); 

    /* awaiting another promise from anotherAsync for 1000ms */
    const anotherAsyncvalue= await anotherAsync(1000);

    return someAsyncValue + anotherAsyncvalue; 
}
{% endhighlight %} 
<p>The snippet above will need a total of 2000ms to return the value expected. However, we can save time by making the two asynchronous function calls at the same time. Take a look at the refined version of the <em>twoAsyncs()</em> function below, we await the return value of the two functions togther at the same time in the return statement.</p>
{% highlight javascript %}
async function twoAsyncs(){
    const someAsyncValue =  someAsync(1000); //  execute promise from someAsync for 1000ms
    const anotherAsyncvalue =  anotherAsync(1000); //execute promise from anotherAsync for 1000ms

    // await the return values of someAsync() and anotherAsync() for just 1000ms 
    return await someAsyncValue + await anotherAsyncvalue;  
}
{% endhighlight %} 
<h5 class="paragraphy-heading">An alternative to the parallelism above is by separately listing references to the functions to be awaited </h5>
<p>The references to the functions to be awaited are listed in the sequence with which we wish to await them. Execution would be paused the moment the first await statemtent is encountered till all the await statements have executed.</p>
{% highlight javascript %}
async function twoAsyncs(){
    const someAsyncValue =  someAsync(1000); //  execute promise from someAsync for 1000ms
    const anotherAsyncvalue =  anotherAsync(1000); //execute promise from anotherAsync for 1000ms

    // await the return values of someAsync() and anotherAsync() for just 1000ms
    await someAsyncValue;
    await anotherAsyncvalue;
     
    return  someAsyncValue + anotherAsyncvalue;  
}
{% endhighlight %}
<h5 class="paragraphy-heading">Another approach to the parallelism illustration is the use of destructuring assignment to unpack values from a Promise.all() array</h5>
<p>This allows us to take advantage of Javascript destructuring to get return value of all awaited functions provided the   promise-based functions are independent of eachother. </p>
{% highlight javascript %}
async function twoAsyncs(){
    const [someAsyncValue, anotherAsyncvalue ] = await Promise.all([
        someAsync(1000),
        anotherAsync(1000)
    ]) 
    /* value of resolved promises in someAsync() and anotherAsync() 
    are stored in someAsyncValue and anotherAsyncvalue respectively */

    return  someAsyncValue + anotherAsyncvalue;  
}
{% endhighlight %}
<h5 class="paragraphy-heading">Error handling in Async-Await functions</h5>
<p>It is a great practice to take care of errors that could arise from failures in the promises that are being awaited. This errors can be handled by wrapping the statements inside an async function in a pair <em>try</em> and <em>catch</em> blocks as illustrated below </p>
{% highlight javascript %}
async function twoAsyncs(){
    try{
        const someAsyncValue =  await someAsync(1000); //  execute promise from someAsync for 1000ms
        
        return  someAsyncValue;  
    }
    catch(errResponse){ // how the error should be handled is stated inside this block
        
        console.log(`There was an error with the result : ${errResponse}`);
    }
}
{% endhighlight %}
<p class="emphasis">The different approaches shared in the illustrations above are applicable to different use cases. Some might be inapplicable to some use cases, alternative approaches stated can be implemented in these cases.</p>