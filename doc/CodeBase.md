# Code base

## Tweaking

Add a `src/friends.js` with player names to ignore them from all attack
considerations.

E.g.:
`module.exports = ['TooAngel'];`


Add a `src/config_local.js` to overwrite configuration values. Copy
`config_local.js.example` to `src/config_local.js` as an example. `src/config.js`
has the default values.

## Debugging

Within the `config_local.js` certain `config.debug` flags can be enabled.
To add debug messages `Room.debugLog(TYPE, MESSAGE)` and
`Creep.creepLog(MESSAGE)` are suggested. Especially the `creepLog` allows
granular output of the creep behavior based on the room and the creep role.

## Upload

install dependencies

    npm install

add your account credentials

### to screeps.com

To deploy to the live server provide the credentials.

#### via env

    export email=EMAIL
    export password=PASSWORD

#### via git ignored file

    echo "module.exports = { email: 'your-email@here.tld', password: 'your-secret' };" > account.screeps.com.js
 or edit and rename account.screeps.com.js.sample to account.screeps.com.js   

And deploy to the server:

    grunt

### to private server
Create a `.localSync.js` file with content:
```
module.exports = [{
  cwd: 'src',
  src: [
    '*.js'
  ],
  dest: '$HOME/.config/Screeps/scripts/SERVER/default',
}];
```

    grunt local


## Develop

    grunt dev

## Release

Releasing to npm is done automatically by increasing the version and merging to `master`.

    npm version 10.0.1
    git push --follow-tags

Every deploy to `master` is automatically deployed to the live tooangel account.

## Testing

`node utils/test.js` will start a private server and add some bots as test
cases. Within in the `tmp-test-server` directory the server can be easily
started via `screeps start`.