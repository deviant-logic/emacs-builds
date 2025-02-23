<p align="center">
  <img width="192px" src="https://github.com/emacs-mirror/emacs/raw/emacs-27.2/etc/images/icons/hicolor/scalable/apps/emacs.svg" alt="Logo">
</p>

<h1 align="center">
  Emacs Builds
</h1>

<p align="center">
  <a href="https://github.com/jimeh/emacs-builds/releases/latest"><img alt="GitHub release (stable)" src="https://img.shields.io/endpoint?url=https%3A%2F%2Fraw.githubusercontent.com%2Fjimeh%2Fhomebrew-emacs-builds%2Fmeta%2FCasks%2Femacs-app%2Fshield.json"></a>
  <a href="https://github.com/jimeh/emacs-builds/releases?q=pretest&expanded=true"><img alt="GitHub release (pretest)" src="https://img.shields.io/endpoint?url=https%3A%2F%2Fraw.githubusercontent.com%2Fjimeh%2Fhomebrew-emacs-builds%2Fmeta%2FCasks%2Femacs-app-pretest%2Fshield.json"></a>
  <a href="https://github.com/jimeh/emacs-builds/releases?q=master&expanded=true"><img alt="GitHub release (nightly)" src="https://img.shields.io/endpoint?url=https%3A%2F%2Fraw.githubusercontent.com%2Fjimeh%2Fhomebrew-emacs-builds%2Fmeta%2FCasks%2Femacs-app-nightly%2Fshield.json"></a>
  <a href="https://github.com/jimeh/emacs-builds/releases?q=emacs-28&expanded=true"><img alt="GitHub release (nightly@emacs-28)" src="https://img.shields.io/endpoint?url=https%3A%2F%2Fraw.githubusercontent.com%2Fjimeh%2Fhomebrew-emacs-builds%2Fmeta%2FCasks%2Femacs-app-nightly-28%2Fshield.json"></a>
  <a href="https://github.com/jimeh/emacs-builds/issues/7"><img alt="GitHub release (known good nightly)" src="https://img.shields.io/endpoint?url=https%3A%2F%2Fraw.githubusercontent.com%2Fjimeh%2Fhomebrew-emacs-builds%2Fmeta%2FCasks%2Femacs-app-good%2Fshield.json"></a>
  <a href="https://github.com/jimeh/emacs-builds/issues"><img alt="GitHub issues" src="https://img.shields.io/github/issues-raw/jimeh/emacs-builds?style=flat&logo=github&logoColor=white"></a>
  <a href="https://github.com/jimeh/emacs-builds/pulls"><img alt="GitHub pull requests" src="https://img.shields.io/github/issues-pr-raw/jimeh/emacs-builds?style=flat&logo=github&logoColor=white"></a>
  <a href="https://github.com/jimeh/emacs-builds/releases"><img alt="GitHub all releases" src="https://img.shields.io/endpoint?url=https%3A%2F%2Fraw.githubusercontent.com%2Fjimeh%2Femacs-builds%2Fmeta%2Ftotal-downloads%2Fshield.json"></a>
</p>

<p align="center">
  <strong>
    Self-contained Emacs.app builds for macOS, with native-compilation support.
  </strong>
</p>

## Features

- Self-contained Emacs.app application bundle, with no external dependencies.
- Native compilation ([gccemacs][]), only in Emacs 28.x and later builds.
- Native JSON parsing via libjansson.
- SVG rendering via librsvg.
- Various image formats are supported via macOS native image APIs.
- Xwidget-webkit support is enabled, allowing access to a embedded WebKit-based
  browser with `M-x xwidget-webkit-browse-url`.
- Native XML parsing via libxml2.
- Dynamic module loading.
- Includes the [fix-window-role][] and [system-appearance][] patches from the
  excellent [emacs-plus][] project.
- Emacs source is fetched from the [emacs-mirror/emacs][] GitHub repository.
- Build creation is transparent and public through the use of GitHub Actions,
  allowing anyone to inspect git commit SHAs, full source code, and exact
  commands used to produce a build.
- Emacs.app is signed with a developer certificate and notarized by Apple.
- Uses [build-emacs-for-macos][] to build the self-contained application bundle.

[build-emacs-for-macos]: https://github.com/jimeh/build-emacs-for-macos
[gccemacs]: https://www.emacswiki.org/emacs/GccEmacs
[fix-window-role]:
  https://github.com/d12frosted/homebrew-emacs-plus/blob/master/patches/emacs-28/fix-window-role.patch
[system-appearance]:
  https://github.com/d12frosted/homebrew-emacs-plus/blob/master/patches/emacs-28/system-appearance.patch
[emacs-plus]: https://github.com/d12frosted/homebrew-emacs-plus
[emacs-mirror/emacs]: https://github.com/emacs-mirror/emacs

## System Requirements

- macOS 10.15.x or later (uses Rosetta2 on Apple Silicon machines).
- Xcode Command Line Tools for native compilation (Emacs 28.x and later).

## Installation

### Manual Download

See the [Releases][] page to download latest builds, or [here](latest) for the
latest stable release.

Nightly builds of Emacs are for the most part just fine, but if you don't like
living too close to the edge, see issue [#7 Known Good Nightly Builds][7] for a
list of recent nightly builds which have been actively used by a living being
for a day or two without any obvious issues.

[releases]: https://github.com/jimeh/emacs-builds/releases
[latest]: https://github.com/jimeh/emacs-builds/releases/latest
[7]: https://github.com/jimeh/emacs-builds/issues/7

### Homebrew Cask

1. Install the
   [`jimeh/emacs-builds`](https://github.com/jimeh/homebrew-emacs-builds)
   Homebrew tap:
   ```
   brew tap jimeh/emacs-builds
   ```
2. Install one of the available casks:
   - `emacs-app` for the latest stable release of Emacs (does not include
     native-comp at time of writing):
     ```
     brew install --cask emacs-app
     ```
   - `emacs-app-pretest` for the latest pretest build from Emacs:
     ```
     brew install --cask emacs-app-pretest
     ```
   - `emacs-app-nightly` for the latest nightly build from Emacs' `master`
     branch:
     ```
     brew install --cask emacs-app-nightly
     ```
   - `emacs-app-good` for the latest known good nightly build listed on [#7][7]:
     ```
     brew install --cask emacs-app-good
     ```
   - `emacs-app-nightly-28` for the latest Emacs 28.x nightly build from the
     `emacs-28` branch:
     ```
     brew install --cask emacs-app-nightly-28
     ```

[7]: https://github.com/jimeh/emacs-builds/issues/7

## Use Emacs.app as `emacs` CLI Tool

### Installed via Homebrew Cask

The cask installation method sets up CLI usage automatically by exposing a
`emacs` command. However it will launch Emacs into GUI mode. To instead have
`emacs` in your terminal open a terminal instance of Emacs, add the following
alias to your shell setup:

```bash
alias emacs="emacs -nw"
```

### Installed Manually

Builds come with a custom `emacs` shell script launcher for use from the command
line, located next to `emacsclient` in `Emacs.app/Contents/MacOS/bin`.

The custom `emacs` script makes sure to use the main
`Emacs.app/Contents/MacOS/Emacs` executable from the correct path, ensuring it
finds all the relevant dependencies within the Emacs.app bundle, regardless of
if it's exposed via `PATH` or symlinked from elsewhere.

To use it, simply add `Emacs.app/Contents/MacOS/bin` to your `PATH`. For
example, if you place Emacs.app in `/Applications`:

```bash
if [ -d "/Applications/Emacs.app/Contents/MacOS/bin" ]; then
  export PATH="/Applications/Emacs.app/Contents/MacOS/bin:$PATH"
  alias emacs="emacs -nw" # Always launch "emacs" in terminal mode.
fi
```

If you want `emacs` in your terminal to launch a GUI instance of Emacs, don't
use the alias from the above example.

## Build Process

Building Emacs is done using the [jimeh/build-emacs-for-macos][] build script,
executed within a GitHub Actions [workflow][]. This is why macOS 10.15.x or
later is required, as it's the oldest version of macOS available in GitHub
Actions.

[jimeh/build-emacs-for-macos]: https://github.com/jimeh/build-emacs-for-macos
[workflow]:
  https://github.com/jimeh/emacs-builds/blob/main/.github/workflows/build.yml

Full history for all builds is available on GitHub Actions [here][actions].
Build logs are only retained by GitHub for 90 days though.

[actions]: https://github.com/jimeh/emacs-builds/actions

Nightly builds are scheduled for 0:00 UTC every night, based on the latest
commit from the `master` branch of the [emacs-mirror/emacs][] repository. This
means a nightly build will only be produced if there have been new commits since
the last nightly build.

## Application Signing / Trust

As of June 21st, 2021, all builds are fully signed and notarized. The signing
certificate used is: `Developer ID Application: Jim Myhrberg (5HX66GF82Z)`

To verify the application signature and notarization, you can use `spctl`:

```bash
$ spctl -vvv --assess --type exec /Applications/Emacs.app
/Applications/Emacs.app: accepted
source=Notarized Developer ID
origin=Developer ID Application: Jim Myhrberg (5HX66GF82Z)
```

All builds also come with a SHA256 checksum file, which itself can be double
checked against the SHA256 checksum log output from the packaging step of the
GitHub Actions workflow run which produced the build.

[emacs-mirror/emacs]: https://github.com/emacs-mirror/emacs

## Issues / To-Do

Please see [Issues][] for details of things to come, or to report issues.

[issues]: https://github.com/jimeh/emacs-builds/issues
