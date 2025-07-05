![Reel-fishing banner](https://raw.github.com/apero-ratio/reel-fishing/master/static/images/fishing.avif)

Reel-fishing
=======

A fork of [Gophish](https://getgophish.com) that has been modified to **remove noob-traps** and alter recognizable features (such as the 404 page) to make it less identifiable by targets.
This fork is not supposed to become it's own thing! So, **feature parity with Gophish** will be maintained, and **no additional features will be added.**

This fork is heavily based upon the work of Nicholas Anastasi on ["Never had a bad day phishing. How to set up GoPhish to evade security controls."](https://www.sprocketsecurity.com/blog/never-had-a-bad-day-phishing-how-to-set-up-gophish-to-evade-security-controls) with some added touches.

## Modified features

| Feature | Description |
|---------|-------------|
| Stripping X-Gophish-Contact | Replaced `X-Gophish-Contact` with `X-Contact` in multiple files: `models/email_request_test.go`, `models/maillog.go`, `models/maillog_test.go`, `models/email_request.go` |
| Stripping X-Gophish-Signature | Replaced `X-Gophish-Signature` with `X-Signature` in `webhook/webhook.go` |
| Changing server name | Changed the server name from `gophish` to `IGNORE` in `config/config.go` (this will change the value of the X-Mailer header) |
| Changing rid value | Changed the recipient parameter from `rid` to `userid` in `models/campaign.go` |

### Install

Installation of reel-fishing is as simple as [Gophish](https://docs.getgophish.com/user-guide/installation) since it's the same project - just download and extract the zip containing the [release for your system](https://github.com/apero-ratio/reel-fishing/releases/), and run the binary. 
Reel-fishing has binary releases for Windows, Mac, and Linux platforms.

### Building From Source
> [!IMPORTANT]
> If you are building from source, please note that Reel-fishing requires Go v1.10 or above!

To build Reel-fishing from source, simply run ```git clone https://github.com/apero-ratio/reel-fishin.git``` and ```cd``` into the project source directory. Then, run ```go build```. After this, you should have a binary called ```gophish``` in the current directory.

### Setup
After running the reel-fishing binary, open an Internet browser to https://localhost:3333 and login with the default username and password listed in the log output.
e.g.
```
time="2025-07-05T03:42:23Z" level=info msg="Please login with the username admin and the password 4304d5255378177d"
```

### Documentation

Documentation about gophish features can be found on the [Gophish documentation](http://getgophish.com/documentation).

### Contributing
> [!WARNING]  
> Features or issues related to Gophish features should be directed upstream towards the [Gophish repository](https://github.com/gophish/gophish/issues).

But if you do find something buggy or have a feature idea, that we can act on, please do feel free to [file an issue](https://github.com/apero-ration/reel-fishing/issues/new) on this repo.
