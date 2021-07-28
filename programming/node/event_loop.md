## Event Loop

Event loop in NodeJS based on Event Loop from NGINX Server, where used Event Demultiplexer, but becouse of every OS has it's own realization of Demultiplexer, Node's author Rayan Dahl decide to write libuv(wrapper library for different Event Demultiplexers) on C lang.   

In NodeJs Event Loop(libuv) has 7 phases of execution: 
1. timers
2. pending callback
3. idle
4. prepare
5. poll
6. check
7. close callbacks

Depending on OS, it may be from 6 to 8 phases.

**idle** and **prepare** not used in NodeJS, and only used internally in libuv.

Each phase has a FIFO queue of callbacks to execute. While each phase is special in its own way, generally, when the event loop enters a given phase, it will perform any operations specific to that phase, then execute callbacks in that phase's queue until the queue has been exhausted or the maximum number of callbacks has executed. When the queue has been exhausted or the callback limit is reached, the event loop will move to the next phase, and so on.

Phases Overview
**timers:** this phase executes callbacks scheduled by setTimeout() and setInterval().
**pending callbacks:** executes I/O callbacks deferred to the next loop iteration.
**idle, prepare:** only used internally.
**poll:** retrieve new I/O events; execute I/O related callbacks (almost all with the exception of close callbacks, the ones scheduled by timers, and setImmediate()); node will block here when appropriate.
**check:** setImmediate() callbacks are invoked here.
**close callbacks:** some close callbacks, e.g. socket.on('close', ...).

We have access for each phase from our JS code, except `idle, prepare`, through:
- timers: setTimeout, setInterval
- pending callbacks: I/O callbacks, as functions that executes after DB request or another resource or read/write file
- poll: in that phase all our js code executes, if we would execute some complex task here, our app will freeze and wait for a moment when that task will end
- check: setImmediate
- close callbacks: web-socket closing or something similar

## Examples
```js
// Example #1
console.log('start script');

const interval = setInterval(() => {
  console.log('setInterval');
}, 0);

setTimeout(() => {
  console.log('setTimeout 1');
  Promise.resolve()
    .then(() => {
      console.log('promise 3');
    })
    .then(() => {
      console.log('promise 4');
    })
    .then(() => {
      setTimeout(() => {
        console.log('setTimeout 2');
        Promise.resolve()
          .then(() => {
            console.log('promise 5');
          })
          .then(() => {
            console.log('promise 6');
          })
          .then(() => {
            clearInterval(interval);
          });
      }, 0);
    });
}, 0);

Promise.resolve()
  .then(() => {
    console.log('promise 1');
  })
  .then(() => {
    console.log('promise 2');
  });

// Example #2
const fs = require('fs');

fs.readFile(__filename, () => {
  // poll
  console.log('readFile'); // 6 poll sync

  setTimeout(() => console.log('timeout1')); // 10 poll timers
  setImmediate(() => console.log('immediate1')); // 9 poll because was executed in I/O callback check
  Promise.resolve().then(() => console.log('Promise.resolve1')); // 8 poll microtask after process.tick
  process.nextTick(() => console.log('process.nextTick1')); // 7 poll between phase callbacks
});

setTimeout(() => console.log('timeout2')); // timers 4
setImmediate(() => console.log('immediate2')); // check 5
Promise.resolve().then(() => console.log('Promise.resolve2')); // 3 microtask after process.tick
process.nextTick(() => console.log('process.nextTick2')); // 2 between phase callbacks

console.log('sync code'); // 1 sync
```

## Additional links:
- [nodejs docs](https://nodejs.org/en/docs/guides/event-loop-timers-and-nexttick/)
- [nodejs docs 2](https://nodejs.org/en/docs/guides/dont-block-the-event-loop/)
- [Reactor pattern](https://en.wikipedia.org/wiki/Reactor_pattern)
- [rising stack](https://blog.risingstack.com/node-js-at-scale-understanding-node-js-event-loop/)
- [medium](https://medium.com/devschacht/event-loop-timers-and-nexttick-18579cd122e0)
- [medium 2](https://blog.insiderattack.net/event-loop-and-the-big-picture-nodejs-event-loop-part-1-1cb67a182810)
- [medium 3](https://medium.com/the-node-js-collection/what-you-should-know-to-really-understand-the-node-js-event-loop-and-its-metrics-c4907b19da4c)
- [youtube (ru)](https://www.youtube.com/watch?v=7f787SsgknA)
- [habr (ru)](https://habr.com/ru/post/479062/)
- [habr EL libuv (ru)](https://habr.com/ru/post/336498/)
- [habr working threads (ru)](https://habr.com/ru/company/ruvds/blog/415659/)