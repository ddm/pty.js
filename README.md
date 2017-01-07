# node-pty

**⚠️ This project will soon be published to npm under the name node-pty, in the meantime [c75c2dc](https://github.com/Tyriar/pty.js/commit/c75c2dcb6dcad83b0cb3ef2ae42d0448fb912642) is the stable version that should be used, *not* the `HEAD` of `master`. See [this issue](https://github.com/Microsoft/vscode/issues/13625) for more details.**

`forkpty(3)` bindings for node.js. This allows you to fork processes with pseudo
terminal file descriptors. It returns a terminal object which allows reads
and writes.

This is useful for:

- Writing a terminal emulator.
- Getting certain programs to *think* you're a terminal. This is useful if
  you need a program to send you control sequences.

## Example Usage

``` js
var pty = require('node-pty');

var term = pty.spawn('bash', [], {
  name: 'xterm-color',
  cols: 80,
  rows: 30,
  cwd: process.env.HOME,
  env: process.env
});

term.on('data', function(data) {
  console.log(data);
});

term.write('ls\r');
term.resize(100, 40);
term.write('ls /\r');

console.log(term.process);
```

## pty.js

This project is forked from [chjj/pty.js](https://github.com/chjj/pty.js) with the primary goals being to provide better support for later Node.JS versions and Windows.

## License

Copyright (c) 2012-2015, Christopher Jeffrey (MIT License).
Copyright (c) 2016, Daniel Imms (MIT License).
