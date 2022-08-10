# Open Web3 & Polkadot Textbook

This textbook is designed to be an introduction for developers looking to enter 
the Web3 space and develop within the Polkadot/Kusama ecospace.

The current structure of this textbook is heavily inspired by that of the first 
Polkadot Blockchain Academy that took place at Corpus Christi College, Cambridge 
in the Summer of 2022.

## Using this Textbook - mdbook

This textbook is designed around the use of mdbook as the primary method of 
consuming the content written within.

(mdbook)[https://rust-lang.github.io/mdBook/index.html] is a "command line tool 
to create books with Markdown."

### Requirements

To locally view the textbook, you will need mdbook installed on your system. 
This can be done in various ways depending on your development environment, 
please see the (official mdbook installation guide)[https://rust-lang.github.io/mdBook/guide/installation.html].

### Usage

Currently, the book is not remotely hosted and will need to be viewed locally. 
To do so, run the following commands in a directory of your choice:

```sh
# Assumes you have GitHub CLI, if not just clone the repo
gh repo clone PoisonPhang/open-web3-and-polkadot-text-book
# Enter the newly cloned repository
cd open-web3-and-polkadot-text-book/
# Locally serve the mdbook on port 3000 by default
mdbook serve --open
```

## Contributing

Currently, we are looking for contributions to the seven main chapters of this textbook.

Please see our (contributing guide)[./.github/CONTRIBUTING.md] for more details.

