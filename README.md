# CentOS Stream Contributor's Guide

This repository contains sources to the CentOS Stream Contributor's Guide, published at https://docs.centos.org/en-US/docs/.

## Structure

```
|-- README.md
|-- antora.yml ....................... 1.
|-- build.sh ......................... 2.
|-- preview.sh ....................... 3.
|-- site.yml ......................... 4.
`-- modules
    `-- ROOT ......................... 5.
        |-- assets
        |   `-- images ............... 6.
        |       `-- pizza.png
        |-- nav.adoc ................. 7.
        `-- pages .................... 8.
            |-- architecture.adoc
            |-- community.adoc
            |-- faq.adoc
            |-- index.adoc
            |-- pizza-dough.adoc
            `-- pizza-oven.adoc
```

1. Metadata definition.
2. A script that does a local build. Uses docker.
3. A script that shows a preview of the site in a web browser by running a local web server. Uses docker.
4. A definition file for the build script.
5. A "root module of this documentation component". Please read below for an explanation.
6. **Images** to be used on any page.
7. **Menu definition.** Also defines the hierarchy of all the pages.
8. **Pages with the actual content.** They can be also organised into subdirectories if desired.

## Components and Modules

Antora introduces two new terms:

* **Component** — Simply put, a component is a part of the documentation website with its own menu. Components can also be versioned. In the Fedora Docs, we use separate components for user documentation, the Fedora Poject, Fedora council, Mindshare, FESCO, but also subprojects such as CommOps or Modulartity.
* **Module** — A component can be broken down into multiple modules. Modules still share a single menu on the site, but their sources can be stored in different git repositories, even owned by different groups. The default module is called "ROOT" (that's what is in this example). If you don't want to use multiple modules, only use "ROOT". But to define more modules, simply duplicate the "ROOT" directory and name it anything you want. You can store modules in one or more git repositories.

## Local preview

This repo includes scripts to build and preview the contents of this repository.

Both scripts work on Fedora/CentOS (using Podman) and macOS (using Docker).

To build and preview the site, run:

```
$ ./build.sh && ./preview.sh
```

The result will be available at http://localhost:8080

### Installing Podman

Podman probably is not installed on your system by default. To install it, run:

```
$ sudo dnf install podman
```

Then, reboot your system.
