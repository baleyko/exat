# expat - react on file system events

[![Dependency Status](https://img.shields.io/david/baleyko/expat.svg)](https://david-dm.org/baleyko/expat)
[![NPM version](https://img.shields.io/npm/v/expat.svg)](https://www.npmjs.com/package/expat)
[![Downloads](https://img.shields.io/npm/dm/expat.svg)](https://www.npmjs.com/package/expat)
[![The MIT License](https://img.shields.io/badge/license-MIT-orange.svg)](http://opensource.org/licenses/MIT)

It's a tiny utility which just listen to file system events(like add/update/remove) and run some command once the such event is triggered.

## Installation

1. Install the expat utility via npm/yarn:

```bash
$ yarn global add expat
# -or-
$ npm i -g expat
```

## Usage (example)

1. Run the expat in any empty directory:

```bash
$ expat --filter=newfile.txt rm newfile.txt
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

The 'expat' supports the next options:

-t --timeout - when the timeout is reached, shutdown without the command execution

-p --poll - use operating system(nix/macos) facilities to be notified about file system events

-i --ignore - use simple pattern to ignore some paths

-f --filter - use regex to filter paths which could cause command execution

The rest arguments will be assumed as the command and its arguments.
All stdin/stdout/stderr streams is piped from/to the child process.
The child process exit code will be forwarded as an exit code of the 'expat'.

## License

[MIT License](https://opensource.org/licenses/MIT) - see the [LICENSE](https://github.com/baleyko/expat/blob/master/LICENSE.md) for more details.
