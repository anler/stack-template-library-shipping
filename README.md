# Stack template for shipping

Haskell Stack template inspired by Chris Penner's [Shipping Haskell Via Homebrew](http://chrispenner.ca/post/homebrew-haskell).

## Usage ##

1. Download `library-shipping.hsfiles`
2. Create a new project using this template with `stack new <project name> <path to library-shipping.hsfiles>

## Shipping via Homebrew ##

If additionally you want to ship your project via Homebrew using Github you can do so by creating the file `<reponame>.rb` containing (you need to replace the `<...>` placeholders with the proper values):

```ruby
class Tempered < Formula
  desc "Program description."
  homepage "https://github.com/<githubuser>/<reponame>"
  url "https://github.com/<githubuser>/<reponame>/releases/download/v0.1.0/<reponame>-v0.1.0-osx.tar.gz"
  sha256 "<sha 256 checksum shown in Travis-CI logs for the osx build under the attach-binary.sh step>"

  bottle :unneeded

  def install
    bin.install "<reponame>"
  end

  test do
    system "#{bin}/<reponame>"
  end
end
```

in a repo named `homebrew-<tapname>`, after that you can install you program with: `brew install githubuser/tapname/reponame`
