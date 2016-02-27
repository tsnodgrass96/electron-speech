# electron-speech

> Speech recognition in node and the browser using Electron.

## Usage

### CLI

This module installs the `electron-speech` command:

```
$ electron-speech
listening..
(whatever is said is written here, to stdout)
```

`-q|--quiet` to omit the `listening..` message. (it's on stderr anyways though)

`-c|--continuous` to keep on listening after each result.

### API

```javascript
var Speech = require('electron-speech')
```

#### var speech = Speech(opts)

Returns `speech`, an EventEmitter and Readable stream.

`opts` accepts multiple keys:

- `opts.lang` - recognize speech in the language `lang`. Defaults to `'en-US'`.
- `opts.continuous` - if true, `text` events will keep on being emitted as recognition
occurs.

#### speech.on('ready')

Emitted when the microphone has begun to listen for speech.

#### speech.on('text', function (text) {})

Emitted when speech has been recognized.

#### speech.on('error', function (err) {})

Emitted when an error has occurred in recognition.

#### speech.on('close')

Emitted when recognition has ended. Does not fire if `continuous` was set to
true.

#### speech.pipe(stream)

Uses `speech` as a readable stream for text rather than an event emitter.
Results have newlines appended to them for parsing convenience.


## License

ISC
