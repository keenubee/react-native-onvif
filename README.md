# react-native-onvif
React Native wrapper for node-onvif library

1. Install and shim

  ```
  npm i --save react-native-onvif
  # install peer deps
  npm i --save react-native-randombytes
  react-native link react-native-randombytes
  npm i --save react-native-udp
  react-native link react-native-udp
  # install node core shims and recursively hack package.json files
  # in ./node_modules to add/update the "browser"/"react-native" field with relevant mappings
  ./node_modules/.bin/rn-nodeify --hack --install
  # if using yarn:
  ./node_modules/.bin/rn-nodeify --hack --install --yarn
  ```
  2. rn-nodeify will create a shim.js in the project root directory.

  Manually uncomment the line to `require('crypto')` in shim.js, this is because as of react-native 0.49, dynamically requiring a library is no longer allowed.

  ```
  // index.js
  // make sure you use `import` and not `require`!
  import './shim.js'
  // ...the rest of your code
  ```