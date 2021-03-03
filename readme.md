# ssl-serve

## Note by Tim Daubenschütz

During a re-write vercel removed the support for `serve`'s `--ssl` flag.
However, a user named jwarby [pointed
out](https://github.com/vercel/serve/issues/627#issuecomment-708460881) that
version 6 still included it and was working fine. I noticed that version 6 had
vulnerabilities though, so I decided to fork v6 of vercel/serve to remove them.

I'm likely to maintain this this package as I'm planning on using it in my
projects.

## Usage

```bash
npm install -g ssl-serve
```

Once that's done, you can run this command inside your project's directory:

```bash
serve [options] <path>
```

### Serve Content Via HTTP and automatic SSL Cert generation

Just use the `--ssl` option. Make sure to accept the self-signed certificate
in your browser too.

### Options

Run this command to see a list of all available options:

```bash
serve help
```

### Authentication

If you set the `--auth` flag, the package will look for a username and password
in the `SERVE_USER` and `SERVE_PASSWORD` environment variables.

As an example, this is how such a command could look like:

```bash
SERVE_USER=leo SERVE_PASSWORD=1234 serve --auth
```

## API

You can also use the package inside your application. Just load it:

```js
const serve = require('serve')
```

And call it with flags (run [this command](#options) for the full list):

```js
const server = serve(__dirname, {
  port: 1337,
  ignore: ['node_modules']
})
```

Later in the code, you can stop the server using this method:

```js
server.stop()
```

## Contributing

I'm happy to merge contributor's PRs.

## License

See [License](./LICENSE).

## Authors

Leo Lamprecht ([@notquiteleo](https://twitter.com/notquiteleo)) - [Vercel](https://vercel.com)
Tim Daubenschuetz <tim.daubenschuetz@gmail.com>
