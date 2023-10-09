# Install Node Canvas on Mac

you might see this error when you install node-canvas on Mac:

```bash
/bin/sh: pkg-config: command not found
gyp: Call to 'pkg-config pixman-1 --libs' returned exit status 127 while in binding.gyp. while trying to load binding.gyp
gyp ERR! configure error
gyp ERR! stack Error: `gyp` failed with exit code: 1
gyp ERR! stack     at ChildProcess.onCpExit (/Users/ilyasayunda/.nvm/versions/node/v20.8.0/lib/node_modules/npm/node_modules/node-gyp/lib/configure.js:325:16)
gyp ERR! stack     at ChildProcess.emit (node:events:514:28)
gyp ERR! stack     at ChildProcess._handle.onexit (node:internal/child_process:294:12)
gyp ERR! System Darwin 22.4.0
```

to fix this, you need to install `pkg-config`:

```bash
brew install pkg-config cairo pango libpng jpeg giflib librsvg
```

then install node-canvas again:

```bash
npm install canvas
```
