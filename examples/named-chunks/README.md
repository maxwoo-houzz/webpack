# example.js

```javascript
var a = require("a");

require.ensure(["b"], function(require) {
	// a named chunk
	var c = require("c");
}, "my own chunk");

require.ensure(["b"], function(require) {
	// another chunk with the same name
	var d = require("d");
}, "my own chunk");

require.ensure([], function(require) {
	// the same again
}, "my own chunk");

require.ensure(["b"], function(require) {
	// chunk without name
	var d = require("d");
});
```

# dist/output.js

```javascript
/******/ (() => { // webpackBootstrap
/******/ 	var __webpack_modules__ = ([
/* 0 */,
/* 1 */
/*!***************************!*\
  !*** ./node_modules/a.js ***!
  \***************************/
/*! exports [maybe provided (runtime-defined)] [no usage info] */
/*! runtime requirements:  */
/***/ (() => {

// module a

/***/ })
/******/ 	]);
/************************************************************************/
/******/ 	// The module cache
/******/ 	var __webpack_module_cache__ = {};
/******/ 	
/******/ 	// The require function
/******/ 	function __webpack_require__(moduleId) {
/******/ 		// Check if module is in cache
/******/ 		if(__webpack_module_cache__[moduleId]) {
/******/ 			return __webpack_module_cache__[moduleId].exports;
/******/ 		}
/******/ 		// Create a new module (and put it into the cache)
/******/ 		var module = __webpack_module_cache__[moduleId] = {
/******/ 			i: moduleId,
/******/ 			l: false,
/******/ 			exports: {}
/******/ 		};
/******/ 	
/******/ 		// Execute the module function
/******/ 		__webpack_modules__[moduleId](module, module.exports, __webpack_require__);
/******/ 	
/******/ 		// Flag the module as loaded
/******/ 		module.l = true;
/******/ 	
/******/ 		// Return the exports of the module
/******/ 		return module.exports;
/******/ 	}
/******/ 	
/******/ 	// expose the modules object (__webpack_modules__)
/******/ 	__webpack_require__.m = __webpack_modules__;
/******/ 	
/************************************************************************/
/******/ 	/* webpack/runtime/ensure chunk */
/******/ 	!function() {
/******/ 		__webpack_require__.f = {};
/******/ 		// This file contains only the entry chunk.
/******/ 		// The chunk loading function for additional chunks
/******/ 		__webpack_require__.e = (chunkId) => {
/******/ 			return Promise.all(Object.keys(__webpack_require__.f).reduce((promises, key) => {
/******/ 				__webpack_require__.f[key](chunkId, promises);
/******/ 				return promises;
/******/ 			}, []));
/******/ 		};
/******/ 	}();
/******/ 	
/******/ 	/* webpack/runtime/get javascript chunk filename */
/******/ 	!function() {
/******/ 		// This function allow to reference async chunks
/******/ 		__webpack_require__.u = (chunkId) => {
/******/ 			// return url for filenames based on template
/******/ 			return "" + chunkId + ".output.js";
/******/ 		};
/******/ 	}();
/******/ 	
/******/ 	/* webpack/runtime/publicPath */
/******/ 	!function() {
/******/ 		__webpack_require__.p = "dist/";
/******/ 	}();
/******/ 	
/******/ 	/* webpack/runtime/jsonp chunk loading */
/******/ 	!function() {
/******/ 		
/******/ 		
/******/ 		// object to store loaded and loading chunks
/******/ 		// undefined = chunk not loaded, null = chunk preloaded/prefetched
/******/ 		// Promise = chunk loading, 0 = chunk loaded
/******/ 		var installedChunks = {
/******/ 			179: 0
/******/ 		};
/******/ 		
/******/ 		
/******/ 		
/******/ 		
/******/ 		__webpack_require__.f.j = (chunkId, promises) => {
/******/ 				// JSONP chunk loading for javascript
/******/ 				var installedChunkData = Object.prototype.hasOwnProperty.call(installedChunks, chunkId) ? installedChunks[chunkId] : undefined;
/******/ 				if(installedChunkData !== 0) { // 0 means "already installed".
/******/ 		
/******/ 					// a Promise means "currently loading".
/******/ 					if(installedChunkData) {
/******/ 						promises.push(installedChunkData[2]);
/******/ 					} else {
/******/ 						if(true) { // all chunks have JS
/******/ 							// setup Promise in chunk cache
/******/ 							var promise = new Promise((resolve, reject) => {
/******/ 								installedChunkData = installedChunks[chunkId] = [resolve, reject];
/******/ 							});
/******/ 							promises.push(installedChunkData[2] = promise);
/******/ 		
/******/ 							// start chunk loading
/******/ 							var url = __webpack_require__.p + __webpack_require__.u(chunkId);
/******/ 							var loadingEnded = () => {
/******/ 								if(Object.prototype.hasOwnProperty.call(installedChunks, chunkId)) {
/******/ 									installedChunkData = installedChunks[chunkId];
/******/ 									if(installedChunkData !== 0) installedChunks[chunkId] = undefined;
/******/ 									if(installedChunkData) return installedChunkData[1];
/******/ 								}
/******/ 							};
/******/ 							var script = document.createElement('script');
/******/ 							var onScriptComplete;
/******/ 		
/******/ 							script.charset = 'utf-8';
/******/ 							script.timeout = 120;
/******/ 							if (__webpack_require__.nc) {
/******/ 								script.setAttribute("nonce", __webpack_require__.nc);
/******/ 							}
/******/ 							script.src = url;
/******/ 		
/******/ 							// create error before stack unwound to get useful stacktrace later
/******/ 							var error = new Error();
/******/ 							onScriptComplete = function (event) {
/******/ 								onScriptComplete = function() {};
/******/ 								// avoid mem leaks in IE.
/******/ 								script.onerror = script.onload = null;
/******/ 								clearTimeout(timeout);
/******/ 								var reportError = loadingEnded();
/******/ 								if(reportError) {
/******/ 									var errorType = event && (event.type === 'load' ? 'missing' : event.type);
/******/ 									var realSrc = event && event.target && event.target.src;
/******/ 									error.message = 'Loading chunk ' + chunkId + ' failed.\n(' + errorType + ': ' + realSrc + ')';
/******/ 									error.name = 'ChunkLoadError';
/******/ 									error.type = errorType;
/******/ 									error.request = realSrc;
/******/ 									reportError(error);
/******/ 								}
/******/ 							};
/******/ 							var timeout = setTimeout(function(){
/******/ 								onScriptComplete({ type: 'timeout', target: script });
/******/ 							}, 120000);
/******/ 							script.onerror = script.onload = onScriptComplete;
/******/ 							document.head.appendChild(script);
/******/ 						} else installedChunks[chunkId] = 0;
/******/ 		
/******/ 						// no HMR
/******/ 					}
/******/ 				}
/******/ 		
/******/ 				// no chunk preloading needed
/******/ 		};
/******/ 		
/******/ 		// no prefetching
/******/ 		
/******/ 		// no HMR
/******/ 		
/******/ 		// no HMR manifest
/******/ 		
/******/ 		// no deferred startup or startup prefetching
/******/ 		
/******/ 		// install a JSONP callback for chunk loading
/******/ 		function webpackJsonpCallback(data) {
/******/ 			var chunkIds = data[0];
/******/ 			var moreModules = data[1];
/******/ 		
/******/ 			var runtime = data[3];
/******/ 		
/******/ 			// add "moreModules" to the modules object,
/******/ 			// then flag all "chunkIds" as loaded and fire callback
/******/ 			var moduleId, chunkId, i = 0, resolves = [];
/******/ 			for(;i < chunkIds.length; i++) {
/******/ 				chunkId = chunkIds[i];
/******/ 				if(Object.prototype.hasOwnProperty.call(installedChunks, chunkId) && installedChunks[chunkId]) {
/******/ 					resolves.push(installedChunks[chunkId][0]);
/******/ 				}
/******/ 				installedChunks[chunkId] = 0;
/******/ 			}
/******/ 			for(moduleId in moreModules) {
/******/ 				if(Object.prototype.hasOwnProperty.call(moreModules, moduleId)) {
/******/ 					__webpack_require__.m[moduleId] = moreModules[moduleId];
/******/ 				}
/******/ 			}
/******/ 			if(runtime) runtime(__webpack_require__);
/******/ 			if(parentJsonpFunction) parentJsonpFunction(data);
/******/ 		
/******/ 			while(resolves.length) {
/******/ 				resolves.shift()();
/******/ 			}
/******/ 		
/******/ 		};
/******/ 		
/******/ 		var jsonpArray = window["webpackJsonp"] = window["webpackJsonp"] || [];
/******/ 		var oldJsonpFunction = jsonpArray.push.bind(jsonpArray);
/******/ 		jsonpArray.push = webpackJsonpCallback;
/******/ 		
/******/ 		var parentJsonpFunction = oldJsonpFunction;
/******/ 	}();
/******/ 	
/************************************************************************/
!function() {
/*!********************!*\
  !*** ./example.js ***!
  \********************/
/*! exports [maybe provided (runtime-defined)] [no usage info] */
/*! runtime requirements: __webpack_require__, __webpack_require__.e, __webpack_require__.* */
var a = __webpack_require__(/*! a */ 1);

__webpack_require__.e(/*! require.ensure | my own chunk */ 666).then((function(require) {
	// a named chunk
	var c = __webpack_require__(/*! c */ 3);
}).bind(null, __webpack_require__)).catch(__webpack_require__.oe);

__webpack_require__.e(/*! require.ensure | my own chunk */ 666).then((function(require) {
	// another chunk with the same name
	var d = __webpack_require__(/*! d */ 4);
}).bind(null, __webpack_require__)).catch(__webpack_require__.oe);

__webpack_require__.e(/*! require.ensure | my own chunk */ 666).then((function(require) {
	// the same again
}).bind(null, __webpack_require__)).catch(__webpack_require__.oe);

__webpack_require__.e(/*! require.ensure */ 885).then((function(require) {
	// chunk without name
	var d = __webpack_require__(/*! d */ 4);
}).bind(null, __webpack_require__)).catch(__webpack_require__.oe);

}();
/******/ })()
;
```

# dist/666.output.js

```javascript
(window["webpackJsonp"] = window["webpackJsonp"] || []).push([[666],[
/* 0 */,
/* 1 */,
/* 2 */
/*!***************************!*\
  !*** ./node_modules/b.js ***!
  \***************************/
/*! exports [maybe provided (runtime-defined)] [no usage info] */
/*! runtime requirements:  */
/***/ (() => {

// module b

/***/ }),
/* 3 */
/*!***************************!*\
  !*** ./node_modules/c.js ***!
  \***************************/
/*! exports [maybe provided (runtime-defined)] [no usage info] */
/*! runtime requirements:  */
/***/ (() => {

// module c

/***/ }),
/* 4 */
/*!***************************!*\
  !*** ./node_modules/d.js ***!
  \***************************/
/*! exports [maybe provided (runtime-defined)] [no usage info] */
/*! runtime requirements:  */
/***/ (() => {

// module d

/***/ })
]]);
```

# dist/885.output.js

```javascript
(window["webpackJsonp"] = window["webpackJsonp"] || []).push([[885],[
/* 0 */,
/* 1 */,
/* 2 */
/*!***************************!*\
  !*** ./node_modules/b.js ***!
  \***************************/
/*! exports [maybe provided (runtime-defined)] [no usage info] */
/*! runtime requirements:  */
/***/ (() => {

// module b

/***/ }),
/* 3 */,
/* 4 */
/*!***************************!*\
  !*** ./node_modules/d.js ***!
  \***************************/
/*! exports [maybe provided (runtime-defined)] [no usage info] */
/*! runtime requirements:  */
/***/ (() => {

// module d

/***/ })
]]);
```

# Info

## Unoptimized

```
Hash: 0a1b2c3d4e5f6a7b8c9d
Version: webpack 5.0.0-beta.6
        Asset       Size
666.output.js  814 bytes  [emitted]  [name: my own chunk]
885.output.js  582 bytes  [emitted]
    output.js   8.77 KiB  [emitted]  [name: main]
Entrypoint main = output.js
chunk output.js (main) 432 bytes (javascript) 4.23 KiB (runtime) [entry] [rendered]
    > ./example.js main
 ./example.js 421 bytes [built]
     [used exports unknown]
     entry ./example.js main
 ./node_modules/a.js 11 bytes [built]
     [used exports unknown]
     cjs require a ./example.js 1:8-20
     + 4 hidden chunk modules
chunk 666.output.js (my own chunk) 33 bytes [rendered]
    > ./example.js 13:0-15:18
    > ./example.js 3:0-6:18
    > ./example.js 8:0-11:18
 ./node_modules/b.js 11 bytes [built]
     [used exports unknown]
     require.ensure item b ./example.js 3:0-6:18
     require.ensure item b ./example.js 8:0-11:18
     require.ensure item b ./example.js 17:0-20:2
 ./node_modules/c.js 11 bytes [built]
     [used exports unknown]
     cjs require c ./example.js 5:9-21
 ./node_modules/d.js 11 bytes [built]
     [used exports unknown]
     cjs require d ./example.js 10:9-21
     cjs require d ./example.js 19:9-21
chunk 885.output.js 22 bytes [rendered]
    > ./example.js 17:0-20:2
 ./node_modules/b.js 11 bytes [built]
     [used exports unknown]
     require.ensure item b ./example.js 3:0-6:18
     require.ensure item b ./example.js 8:0-11:18
     require.ensure item b ./example.js 17:0-20:2
 ./node_modules/d.js 11 bytes [built]
     [used exports unknown]
     cjs require d ./example.js 10:9-21
     cjs require d ./example.js 19:9-21
```

## Production mode

```
Hash: 0a1b2c3d4e5f6a7b8c9d
Version: webpack 5.0.0-beta.6
        Asset      Size
666.output.js  99 bytes  [emitted]  [name: my own chunk]
885.output.js  84 bytes  [emitted]
    output.js  1.64 KiB  [emitted]  [name: main]
Entrypoint main = output.js
chunk output.js (main) 432 bytes (javascript) 4.23 KiB (runtime) [entry] [rendered]
    > ./example.js main
 ./example.js 421 bytes [built]
     [no exports used]
     entry ./example.js main
 ./node_modules/a.js 11 bytes [built]
     cjs require a ./example.js 1:8-20
     + 4 hidden chunk modules
chunk 666.output.js (my own chunk) 33 bytes [rendered]
    > ./example.js 13:0-15:18
    > ./example.js 3:0-6:18
    > ./example.js 8:0-11:18
 ./node_modules/b.js 11 bytes [built]
     require.ensure item b ./example.js 3:0-6:18
     require.ensure item b ./example.js 8:0-11:18
     require.ensure item b ./example.js 17:0-20:2
 ./node_modules/c.js 11 bytes [built]
     cjs require c ./example.js 5:9-21
 ./node_modules/d.js 11 bytes [built]
     cjs require d ./example.js 10:9-21
     cjs require d ./example.js 19:9-21
chunk 885.output.js 22 bytes [rendered]
    > ./example.js 17:0-20:2
 ./node_modules/b.js 11 bytes [built]
     require.ensure item b ./example.js 3:0-6:18
     require.ensure item b ./example.js 8:0-11:18
     require.ensure item b ./example.js 17:0-20:2
 ./node_modules/d.js 11 bytes [built]
     cjs require d ./example.js 10:9-21
     cjs require d ./example.js 19:9-21
```
