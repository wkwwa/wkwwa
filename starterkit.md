# MacOS Tools

Install brew from the instructions given in the link below.
```
https://brew.sh/
```

After installing homebrew
Create a file in users home directory with name .curlrc with content “-k”
(-k without quotes and give a new line character after -k.)
Steps:
  1. open Terminal
  2. echo -k > ~/.curlrc
  3. cat ~/.curlrc

Run all the below commands in Terminal
```
brew install --cask virtualbox (Not For MacOs M1/M2)
brew install --cask vagrant
brew install --cask vagrant-manager
brew install git
brew install openjdk@17
sudo ln -sfn $HOMEBREW_PREFIX/opt/openjdk@17/libexec/openjdk.jdk /Library/Java/JavaVirtualMachines/openjdk.jdk
exec zsh -l
brew install maven
brew install --cask visual-studio-code
brew install --cask intellij-idea
brew install --cask intellij-idea-ce
brew install --cask sublime-text
brew install awscli
```