# DOM manipulation

# Concepts
+ Event Loop has 3 parts: Call STACK, WebAPI's/Browser, Event QUEUE
+ Call Stack: when functions are called, they are added on top of the call stack, then synchronously invoked
+ eventListeners are NOT synchronous and "wait" in the Browser until current synchronous code is finished ("run-to-completion")
+ asynchronous code runs outside the Event Loop and sends event when done
+ once the asynchronus code is called, it waits in the QUEUE until the Call Stack is empty and then is passed to therein
+ a function invoked by an event starts in the BROWSER, on invokation jumps in the QUEUE and waits for synchronous code to run complete, and then is placed on Call STACK

# Performance
+ performance.now() ->start measunring from page load on; 
+ document.createDocumentFragment() to avoid triggering reflow and repaint
    - reflow is the process of recalculating the dimensions and positions of page elements (slow)
    - repaint draws the pixel to the screen (faster)
+ hide - several changes - show, avoids repaints
+ setTimeout(function myResourceHeavyBlockyFunction (){}, 0); -> is given to Browser after 0 milliseconds and from there enters QUEUE and then STACK, thus can be broken up and let the STACK a chance to handle user interaction/events

# Browser Events
+ .removeEventlistener();
+ .dispatchtEvent();
+ <event-target>.addEventListener('event', callbackFunction(e), useCapture);
    - event-lifecycle has 3 phases: capturing (going down the DOM), at target and bubbling (going to parent nodes in DOM) 
    - useCapture = true -> invokes listener during the capturing phase, not later in the bubbling phase. Thus we can capture events on children although parent(s) may have events as well.
    - most used method of event object: e.preventDefault();
    - use 'e.target' to alter a child-target but to run the listener function in bubble phase on the parent. Thus lesser events are needed.
    - document.addEventListener('DOMContentLoaded', function(e)); to avoid null-pointer errors while building the DOM
    - document.onload() takes longer and waits for images, stylesheets etc. 


# styling
+ element.style.<prop> -> .style.fontSize = '2em'
+ element.cssText = 'color: red; font-size: 2em'
+ element.setAttribut() -> setAttribute('style', color: blue')
+ element.className
+ element.classList.
    - .add()
    - .remove()
    - .toggle()
    - .contains()

## disthingush between '.innerHTML', '.innerText' and '.textContent'
+ '.innerHTML' gives everything including html code
+ '.textContent' gives text without CSS like 'display: none'
+ '.innerText' gives text WITH respect to CSS

## creating
+ document.createElement('');
+ document.createTextNode();
+ element.appendChild('');
+ element.insertAdjacentHTML('location', 'text');
    - beforebegin
    - afterbegin
    - beforeend
    - afterend

## removing
+ element.removeChild();
+ element.remove();


## traversing DOM
+ element.firstChild() -> might return whitespace
+ element.firstElementChild();
+ element.parentElement();

