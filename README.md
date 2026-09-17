# Running

The files in this repo were obtained by just saving whatever was served up by slowroads.io, so you need a local http server to run this. You can use `http-server` from npm. To do this you will first need nodejs. Once you have nodejs installed, run

```sh
npm i -g http-server
```

to install `http-server` globally. Then `cd` into the repo and run

```sh
http-server
```

to start the server. `http-server` will print the address to connect to - this will probably be something like `http://127.0.0.1:8081`. Visit this address in your browser to play the game. If you change a file, CTRL + F5 will invalidate the cache and reload the entire page.

# Contributing

Any contributions are welcome. I am working on improving the handling of the new cars and giving them textures as well as fixing the ultra+ bug. I am also naming minified variables as I figure out what they mean.
