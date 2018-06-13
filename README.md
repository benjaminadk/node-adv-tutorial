## Advance Node Project

### Redis

- to store the value of mongoose queries - caching
- key value pairs
- less communication overhead with database
- can only store numbers or letters
- need to expire at some point
- want consistent but unique queries to store as keys in redis
- expiration - `EX` and time (sec) as 3rd, and 4th arguement to set
- expensive so try to manage caching

### Mongoose

- over write `exec()` to check redis for query first
- it also caches result of query when there isn't one cached
- `query.getOptions()` returns object with all the query options
- uses classic prototypal inheritance
- alter and add on to mongoose

### Testing

- **_Jest_**
  - test runner
  - global setup file - set in `package.json`
- **_puppeteer_**
  - Chromium browser instance
  - does everything
- oauth is needed for many tests
  - automating oauth is not a great option
  - many attempts will lead to google locking us out
  - service accounts only work for google
  - faking a session is a universal solution
  - we reverse engineer a cookie from a valid user id
  - `keygrip` used to make or verify cookie
  - `keygrip.sign('session=' + session)` returns sig
  - `keygrip.verify('session=' + session, sig)` returns boolean
  - set session and sig on puppeteer page instance
- **_ Factory Function _**
  - code that gets reused alot - we need fresh copies
  - in this case session and user

### Notes

- `console.log` alone as a callback
- `utils` has a `promisify` function for anything that takes a callback
- `photos[0].value` profile pic

### Cookies

- `set-cookie` - `session=` and `sesson.sig=` in headers
- `session.sig` makes sure session is not tampered with
- `const Buffer = require('safe-buffer').Buffer`
- `Buffer.from(session, 'base64').toString('utf8')` gets the cookie in human readable
- `cookie-session` get cookie checks it decodes it sets it `req.session`
- `passport` looks at `req.session` for a user then an id and passes that to `deserializeUser` gets back a user from db and assigns to `req.user`

### Proxy ES2015

- combines classes or objects for cool functionality

### CI Continuous Integration

- CI Flow
  1.  Dev pushes code to Github
  2.  CI Server detects new push of code has occured
  3.  CI Server clones project in a cloud based virtual machine
  4.  Ci Server runs all tests
  5.  If all tests pass CI Server marks build as 'passing' and does optional followup
- YAML or `yml` files
