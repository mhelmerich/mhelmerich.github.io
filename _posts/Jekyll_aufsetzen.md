---
title: Wie man eine Dokumentation in Jekyll aufsetzt
date: 25.12.2023 22:30
categories: [homelab,dokumentation]
tags: [jekyll]
---

# Jekyll als Dokumentationstool einsetzen

Wie man den static Site Generator Jekyll einsetzt um Dokumentationen (die man auf github hosten kann) zu erstellen.

## Install Dependencies

```bash
sudo apt update
sudo apt install ruby-full build-essential zlib1g-dev git

echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

Install the Jekyll **bundler**

```bash
gem install jekyll bundler
```

## Creating the template

Go to [Chirpy Starter](https://github.com/cotes2020/chirpy-starter) and click <kbd>Use this Template</kbd> > <kbd>Create new repository</kbd>, name the Repo <kbd>USERNAME.github.io</kbd>.

## Clone the new repository to your local machine

```bash
git clone git@github.com:mhelmerich/mhelmerich.github.io.git
```

## Starting Jekyll for the first time

Go to the root directory of your site and run 

```bash
cd mhelmerich.github.io
$ bundle
```

When the installation is done you can start jekyll for the first time:

```bash
bundle exec jekyll s
```
