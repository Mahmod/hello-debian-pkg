Creating a Debian package involves several steps. Below is a step-by-step guide to help you create a simple Debian package that prints "Hello, World!" when installed and run.

### 1. Set Up Your Environment

First, make sure you have the necessary tools installed:

```sh
sudo apt-get update
sudo apt-get install build-essential dh-make devscripts lintian fakeroot
```

### 2. Create Your Project Directory

Create a directory for your project:

```sh
mkdir hello-world
cd hello-world
```


### 3. Create the Changelog File

Run `dch --create` and follow the prompts to create an initial changelog entry. This will create a file named `changelog`.

### 4. Build the Package

Go back to the root of your project directory (`hello-world`), and build the package:

```sh
debuild -us -uc
```

This will create several files in the parent directory. Among them will be a `.deb` file named something like `hello-world_1.0-1_amd64.deb`.

### 5. Install and Test the Package

Install the package:

```sh
sudo dpkg -i ../hello-world_1.0-1_amd64.deb
```

Now, you should be able to run your program:

```sh
hello-world
```

And it should print:

```sh
Hello, World!
```

You’ve just created and installed a Debian package! Remember, this is a very simple example. Real-world Debian packages will require more careful setup and configuration, especially if they need to start services, handle configuration files, or manage user permissions.