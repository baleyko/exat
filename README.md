# exat - react on file system events

[![Dependency Status](https://img.shields.io/david/baleyko/exat.svg)](https://david-dm.org/baleyko/exat)
[![NPM version](https://img.shields.io/npm/v/exat.svg)](https://www.npmjs.com/package/exat)
[![Downloads](https://img.shields.io/npm/dm/exat.svg)](https://www.npmjs.com/package/exat)
[![The MIT License](https://img.shields.io/badge/license-MIT-orange.svg)](http://opensource.org/licenses/MIT)

It's a tiny utility which just listen to file system events(like add/update/remove) and run some command once the such event is triggered.

## Installation

1. Install the exat utility via npm/yarn:

```bash
$ yarn global add exat
# -or-
$ npm i -g exat
```

## Usage (example)

1. Run the exat in any empty directory:

```bash
$ exat --filter=newfile.txt rm newfile.txt
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

The 'exat' supports the next options:

-t --timeout - when the timeout is reached, shutdown without the command execution

-p --poll - use operating system(nix/macos) facilities to be notified about file system events

-i --ignore - use simple pattern to ignore some paths

-f --filter - use regex to filter paths which could cause command execution

The rest arguments will be assumed as the command and its arguments.
All stdin/stdout/stderr streams is piped from/to the child process.
The child process exit code will be forwarded as an exit code of the 'exat'.

## License

[MIT License](https://opensource.org/licenses/MIT) - see the [LICENSE](https://github.com/baleyko/exat/blob/master/LICENSE.md) for more details.
