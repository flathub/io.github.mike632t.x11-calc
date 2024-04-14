# Flatpak packaging for [x11-calc](https://github.com/mike632t/x11-calc) HP RPN calculator emulator

User can launch any of the program emulators (microcode-level firmware interpreter).\
Application icon shows-up in desktop launcher after install.\
Right-click on icon to set default model for direct access, or launch a sample model from list.

Application may be started under terminal (to monitor eventual error messages):\
`flatpak run io.github.mike632t.x11-calc` (add `--setup` to set defaults)\
Defaults may be edited manually from host:\
`nano ~/.var/app/io.github.mike632t.x11-calc/config/x11-calc/x11-calc.conf`

Application is **strictly sandboxed**, so it can only process files (`*.dat`, `*.rom`) within host's:\
`~/.var/app/io.github.mike632t.x11-calc/data/x11-calc/`\
which `x11-calc` application can access there, or within sandboxed `/var/data/x11-calc/`.\
Similarly some read-only sample saved programs are in sandboxed `/app/share/x11-calc/prg/`.

## Building & testing
Install flatpak-builder.
Copy / clone this repo in a directory and then run:\
`flatpak-builder -v --force-clean build-dir io.github.mike632t.x11-calc.yaml`\
Test install:\
`flatpak-builder --user --install --force-clean build-dir io.github.mike632t.x11-calc.yaml`

Once ready, extract side-loadable `x11-calc.flatpak` package for later distribution:\
`flatpak build-bundle ~/.local/share/flatpak/repo x11-calc.flatpak io.github.mike632t.x11-calc`

