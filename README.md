# How to Install Rails on Mac

Installing Rails can be a headache. Here's a step by step guide on how I managed to do it successfully on my laptop. I use a Macbook Pro running Mac OS Sierra 10.12.3.

## Getting Started

```
Give examples
```

### Installing

1. Install Homebrew

```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

2. Install Ruby (version 2.4.0 as of Feburary 8, 2017)

```
brew install rbenv ruby-build

# Add rbenv to bash so that it loads every time you open a terminal
echo 'if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi' >> ~/.bash_profile
source ~/.bash_profile

rbenv install 2.4.0
rbenv global 2.4.0
ruby -v
```
3. Install Rails (version 5.0.1 as of February 8, 2017)

```
gem install rails -v 5.0.1
```
The above code will most likely reach an error trying to install nokogiri. Run the following to fix it.

```
gem install nokogiri -- --use-system-libraries=true --with-xml2-include=/Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX10.12.sdk/usr/include/libxml2/
```

Attempt to install Rails again, this time hopefully errorless. Rails is now installed, but in order for us to use the Rails executable, we need to tell rbenv to see it:

```
rbenv rehash
```

Verify that Rails has been installed by checking the version:

```
rails -v
```

4. Install Database

You can choose between SQLite, MySQL, or PostgreSQL

```
brew install sqlite3
brew install postgresql
brew install mysql
```

5. Running Rails

```
rails new myapp
cd myapp
rake db:create
rails server
```
Check if your website is running successfully on Rails by visiting http://localhost:3000.
