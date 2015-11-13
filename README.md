# npm-install-error
Exemplifies an error that occurs when installing a module from a local folder.
This test was created using npm 3.4.0.

To test, first install dependencies for *test-project-1*:

    cd test-project-1
    npm install
    npm ls
  
You'll see all the dependencies have been installed correctly:

    npm-install-error/test-project-1
    ├── js-cookie@2.0.4
    ├── lodash@3.10.1
    ├── object-assign@4.0.1
    └─┬ react@0.14.2
      ├─┬ envify@3.4.0
      │ ├─┬ jstransform@10.1.0
      │ │ ├── base62@0.1.1
      │ │ ├── esprima-fb@13001.1001.0-dev-harmony-fb
      │ │ └─┬ source-map@0.1.31
      │ │   └── amdefine@1.0.0
      │ └── through@2.3.8
      └─┬ fbjs@0.3.2
        ├── core-js@1.2.6
        ├─┬ loose-envify@1.1.0
        │ └── js-tokens@1.0.2
        ├─┬ promise@7.0.4
        │ └── asap@2.0.3
        ├── ua-parser-js@0.7.9
        └── whatwg-fetch@0.9.0
    
Next, install *test-project-2* into *test-project-1*, saving it as a dependency:

    npm install ../test-project-2 --save
    npm ls
    
You'll see that *test-project-2* was correctly installed:

    npm-install-error/proj1
    ├── js-cookie@2.0.4
    ├── lodash@3.10.1
    ├── object-assign@4.0.1
    ├─┬ react@0.14.2
    │ ├─┬ envify@3.4.0
    │ │ ├─┬ jstransform@10.1.0
    │ │ │ ├── base62@0.1.1
    │ │ │ ├── esprima-fb@13001.1001.0-dev-harmony-fb
    │ │ │ └─┬ source-map@0.1.31
    │ │ │   └── amdefine@1.0.0
    │ │ └── through@2.3.8
    │ └─┬ fbjs@0.3.2
    │   ├── core-js@1.2.6
    │   ├─┬ loose-envify@1.1.0
    │   │ └── js-tokens@1.0.2
    │   ├─┬ promise@7.0.4
    │   │ └── asap@2.0.3
    │   ├── ua-parser-js@0.7.9
    │   └── whatwg-fetch@0.9.0
    └─┬ test-project-2@1.0.0
      ├── classnames@2.2.0
      └── underscore@1.8.3
    
Now, install *test-project-2* again:

    npm install ../test-project-2
    npm ls
    
You'll see that dependencies these two modules share in common have been removed.

    npm-install-error/proj1
    ├── UNMET DEPENDENCY js-cookie@^2.0.4
    ├── lodash@3.10.1
    ├── UNMET DEPENDENCY object-assign@^4.0.1
    ├── UNMET DEPENDENCY react@^0.14.2
    └── test-project-2@1.0.0

    npm ERR! missing: js-cookie@^2.0.4, required by test-project-1@1.0.0
    npm ERR! missing: object-assign@^4.0.1, required by test-project-1@1.0.0
    npm ERR! missing: react@^0.14.2, required by test-project-1@1.0.0