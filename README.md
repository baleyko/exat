# expatr - react on file system events

[![Dependency Status](https://img.shields.io/david/baleyko/expatr.svg)](https://david-dm.org/baleyko/expatr)
[![NPM version](https://img.shields.io/npm/v/expatr.svg)](https://www.npmjs.com/package/expatr)
[![Downloads](https://img.shields.io/npm/dm/expatr.svg)](https://www.npmjs.com/package/expatr)
[![The MIT License](https://img.shields.io/badge/license-MIT-orange.svg)](http://opensource.org/licenses/MIT)

It's a tiny utility which just listen to file system events(like add/update/remove) and run some command once the such event is triggered.

## Installation

1. Install the expatr utility via npm/yarn:

```bash
$ yarn global add expatr
# -or-
$ npm i -g expatr
```

## Usage (example)

1. Run the expatr in any empty directory:

```bash
$ expatr --filter=newfile.txt rm newfile.txt
```

2. Trigger file system change in another terminal:

```bash
$ touch newfile.txt
```

3. Make sure that the 'rm newfile.txt' command was executed:

```bash
$ cat newfile.txt
cat: can't open 'newfile.txt': No such file or directory
```

The 'expatr' supports the next options:

-t --timeout - when the timeout is reached, shutdown without the command execution

-p --poll - use operating system(nix/macos) facilities to be notified about file system events

-i --ignore - use simple pattern to ignore some paths

-f --filter - use regex to filter paths which could cause command execution

The rest arguments will be assumed as the command and its arguments.
All stdin/stdout/stderr streams is piped from/to the child process.
The child process exit code will be forwarded as an exit code of the 'expatr'.

## License

[MIT License](https://opensource.org/licenses/MIT) - see the [LICENSE](https://github.com/baleyko/expatr/blob/master/LICENSE.md) for more details.
