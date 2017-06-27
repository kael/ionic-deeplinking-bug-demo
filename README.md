This is a demo to illustrate IonicPage DeepLinking bug (https://github.com/ionic-team/ionic-app-scripts/issues/848).

At this time, it's not possible to navigate with deeplinking nor to call the PageModule with `navCtrl.push`.

- Navigating with an URI: `http://localhost/#/navigation`:

```js
    core.es5.js:1084 ERROR Error: Uncaught (in promise): invalid views to insert
        at c (polyfills.js:3)
        at Object.reject (polyfills.js:3)
        at NavControllerBase._fireError (nav-controller-base.js:320)
        at NavControllerBase._failed (nav-controller-base.js:308)
        at nav-controller-base.js:363
        at t.invoke (polyfills.js:3)
        at Object.onInvoke (core.es5.js:4149)
        at t.invoke (polyfills.js:3)
        at r.run (polyfills.js:3)
        at polyfills.js:3
```

- Pushing the module using `this.navCtrl.push('navigation')`:

```js
   core.es5.js:1084 ERROR Error: Uncaught (in promise): TypeError: undefined is not a function
    TypeError: undefined is not a function
        at Array.map (native)
        at webpackAsyncContext (https://localhost/build/main.js:74253:34)
        at loadAndCompile (https://localhost/build/main.js:73415:36)
        at NgModuleLoader.load (https://localhost/build/main.js:73380:83)
        at ModuleLoader.load (https://localhost/build/main.js:55510:44)
        at DeepLinker.getNavLinkComponent (https://localhost/build/main.js:20466:39)
        at DeepLinker.getComponentFromName (https://localhost/build/main.js:20449:25)
        at getComponent (https://localhost/build/main.js:29687:23)
        at convertToView (https://localhost/build/main.js:29705:16)
        at convertToViews (https://localhost/build/main.js:29724:32)
        at Array.map (native)
        at webpackAsyncContext (https://localhost/build/main.js:74253:34)
        at loadAndCompile (https://localhost/build/main.js:73415:36)
        at NgModuleLoader.load (https://localhost/build/main.js:73380:83)
        at ModuleLoader.load (https://localhost/build/main.js:55510:44)
        at DeepLinker.getNavLinkComponent (https://localhost/build/main.js:20466:39)
        at DeepLinker.getComponentFromName (https://localhost/build/main.js:20449:25)
        at getComponent (https://localhost/build/main.js:29687:23)
        at convertToView (https://localhost/build/main.js:29705:16)
        at convertToViews (https://localhost/build/main.js:29724:32)
        at c (https://localhost/build/polyfills.js:3:13535)
        at Object.reject (https://localhost/build/polyfills.js:3:12891)
        at NavControllerBase._fireError (https://localhost/build/main.js:44060:16)
        at NavControllerBase._failed (https://localhost/build/main.js:44048:14)
        at https://localhost/build/main.js:44103:59
        at t.invoke (https://localhost/build/polyfills.js:3:9283)
        at Object.onInvoke (https://localhost/build/main.js:4427:37)
        at t.invoke (https://localhost/build/polyfills.js:3:9223)
        at r.run (https://localhost/build/polyfills.js:3:4452)
        at https://localhost/build/polyfills.js:3:14076
```

Versions:
- _npm_: `3.10.10`
- _node_: `v6.11.0`
- _ionic_: `3.4.0`
- _cli-utils_: `1.4.0`
- _cli-scripts_: `0.2.0`