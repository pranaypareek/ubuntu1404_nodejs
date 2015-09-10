ubuntu1404_nodejs
=================

Shippable CI image for Node.js on Ubuntu 14.04. Available Node.js versions:

1. 0.8.28
2. 0.10.23
3. 0.11.14
4. 0.12
5. 4.0.0


## How to use
You can use this image to run node.js builds on Shippable. Just update your
`shippable.yml` file and add the `build_image` directive. You should also
activate the appropriate nvm so your build runs against the
correct version of node.js. The node.js versions you specify in the `node.js`
directive in the YML will be available in the `$SHIPPABLE_NODE_VERSION` environment variable. Here's a sample YML file to get you going:

````
language: node_js
node_js:
  - 0.8
  - 0.10
  - 0.11
  - 0.12

build_image: shippableimages/ubuntu1404_nodejs

before_install:
  # activate the nvm
  - source ~/.nvm/nvm.sh && nvm install $SHIPPABLE_NODE_VERSION
  - node --version
  - npm install -g grunt-cli

install:
  - npm install

script:
  - grunt

````



