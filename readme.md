# Screw'd Android #

## Grabbing the source ##

[Repo](http://source.android.com/source/developing.html) is a tool provided by Google that
simplifies using [Git](http://git-scm.com/book) in the context of the Android source.

### Installing Repo ###

```bash
# Make a directory where Repo will be stored and add it to the path
$ mkdir ~/bin
$ PATH=~/bin:$PATH

# Download Repo itself
$ curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo

# Make Repo executable
$ chmod a+x ~/bin/repo
```

### Initializing Repo ###

```bash
# Create a directory for the source files
# This can be located anywhere (as long as the fs is case-sensitive)
$ mkdir WORKSPACE
$ cd WORKSPACE

# Install Repo in the created directory
# If you are building for CAF based device such as OnePlus 5, use the n7x-caf branch by running.
$ repo init -u https://github.com/ScrewdAOSP/platform_manifest -b n7x-caf
```

### Downloading the source tree ###

This is what you will run each time you want to pull in upstream changes. Keep in mind that on your
first run, it is expected to take a while as it will download all the required Android source files
and their change histories.

```bash
# Let Repo take care of all the hard work
$ repo sync -j4
```

## Building the entire ROM ##

The bundled builder tool `./rom-build.sh`handles all the building steps for 
the specified device automatically. As the device value, you just feed it with the device codename 
(for example, 'cheeseburger' for the OnePlus 5).

```bash
# Go to the root of the source tree...
$ cd WORKSPACE
# ...and run the builder tool.
$ ./rom-build.sh DEVICE
# So if you want to build for the OnePlus 5, run:
$ ./rom-build.sh cheeseburger
```

If all goes well, you will see a message showing where the completed build is located.




