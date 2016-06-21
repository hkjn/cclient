cclient
=======

Repo cclient is a server-side chromium setup.

Using [headless
mode](https://chromium.googlesource.com/chromium/src/+/master/headless/),
we serve a browser session over HTTPS, so clients can send key events
and receive rendered bitmaps and not need to run arbitrary insecure
Javascript code.

Steps to build chromium with headless:

1. `git clone https://chromium.googlesource.com/chromium/tools/depot_tools.git`
2. `export PATH=$PATH:$(pwd)/depot_tools`
3. `fetch chromium && cd src/`
4. `./build/install-build-deps.sh`
5. `gclient runhooks`
6. `mkdir -p out/Debug`
7. `echo 'import("//build/args/headless.gn")' > out/Debug/args.gn`
8. `gn gen out/Debug`
9. `ninja -C out/Debug headless_shell`

Then the shell can be started with `out/Debug/headless_shell https://www.google.com`.

Then navigate to http://127.0.0.1:9222 with your browser.

# References

- https://github.com/elgalu/docker-selenium

