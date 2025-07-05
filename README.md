![reelfish banner](https://raw.github.com/apero-ratio/reelfish/master/static/images/fishing.avif)

reelfish
=======

A fork of [Gophish](https://getgophish.com) that has been modified to **remove noob-traps** and alter recognizable features (such as the 404 page) to make it less identifiable by targets.
This fork is not supposed to become it's own thing! So, **feature parity with Gophish** will be maintained, and **no additional features will be added.**

This fork is heavily based upon the work of Nicholas Anastasi on ["Never had a bad day phishing. How to set up GoPhish to evade security controls."](https://www.sprocketsecurity.com/blog/never-had-a-bad-day-phishing-how-to-set-up-gophish-to-evade-security-controls) with some added touches.

## Modified features

| Feature | Description | Related Commits |
|---------|-------------|-----------------| 
| Stripping X-Gophish-Contact | Replaced `X-Gophish-Contact` with `X-Contact` in multiple files: `models/email_request_test.go`, `models/maillog.go`, `models/maillog_test.go`, `models/email_request.go` | [1e1b6fa](https://github.com/apero-ratio/reelfish/commit/1e1b6fa526cc6078ffcb72cda47774745e798c7d) | 
| Stripping X-Gophish-Signature | Replaced `X-Gophish-Signature` with `X-Signature` in `webhook/webhook.go` | [383b5ac](https://github.com/apero-ratio/reelfish/commit/383b5ac32eaf0a5bed259d63e53a69536879a141) |
| Changing server name | Changed the server name from `gophish` to `IGNORE` in `config/config.go` (this will change the value of the X-Mailer header) | [ac9efb6](https://github.com/apero-ratio/reelfish/commit/ac9efb6e5b540948c689f4965c1f3af15e355c1d) |
| Changing rid value | Changed the recipient parameter from `rid` to `userid` in `models/campaign.go` | [b024ae1](https://github.com/apero-ratio/reelfish/commit/b024ae12aa0cc67d94c2889474c59261a379d7b4) |
| Added a custom 404 page | Gophish original 404 can be used for detection as proven in [this article](https://insomniasec.com/blog/identifying-gophish-servers). Changes were to made to `controllers/phish.go` to load a custom 404 page at `templates/404.html` | [a6a9235](https://github.com/apero-ratio/reelfish/commit/a6a92358abdb1e21f52c73cb67c70615e073bb65) [1685e8d](https://github.com/apero-ratio/reelfish/commit/1685e8d7845aa9e16102262f201befa273eab886) |

### Install

Installation of reelfish is as simple as [Gophish](https://docs.getgophish.com/user-guide/installation) since it's the same project - just download and extract the zip containing the [release for your system](https://github.com/apero-ratio/reelfish/releases/), and run the binary. 
reelfish has binary releases for Windows, Mac, and Linux platforms.

### Building From Source
> [!IMPORTANT]
> If you are building from source, please note that reelfish requires Go v1.10 or above!

To build reelfish from source, simply run ```git clone https://github.com/apero-ratio/reel-fishin.git``` and ```cd``` into the project source directory. Then, run ```go build```. After this, you should have a binary called ```gophish``` in the current directory.

### Setup
After running the reelfish binary, open an Internet browser to https://localhost:3333 and login with the default username and password listed in the log output.
e.g.
```
time="2025-07-05T03:42:23Z" level=info msg="Please login with the username admin and the password 4304d5255378177d"
```

### Documentation

Documentation about gophish features can be found on the [Gophish documentation](http://getgophish.com/documentation).

### Contributing
> [!WARNING]  
> Features or issues related to Gophish features should be directed upstream towards the [Gophish repository](https://github.com/apero-ratio/reelfish/issues).

But if you do find something buggy or have a feature idea, that we can act on, please do feel free to [file an issue](https://github.com/apero-ration/reelfish/issues/new) on this repo.
