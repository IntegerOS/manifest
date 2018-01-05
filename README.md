# Integer OS Project #
## Still keeping it the sweet [Pixel Experience](https://github.com/PixelExperience/manifest)


### Installing repo ###

```bash
# Make a directory where repo will be stored and add it to the path
$ mkdir ~/bin
$ PATH=~/bin:$PATH

# Download repo itself
$ curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo

# Make repo executable
$ chmod a+x ~/bin/repo
```

### Initializing repo ###

```bash
# Create a directory for the source files
$ mkdir integer
$ cd integer

# Install repo in the created directory
# Use a real name/email combination, if you intend to submit patches
$ repo init -u https://github.com/IntegerOS/manifest -b omr1
```

### Downloading the source tree ###
This is what you will run each time you want to pull in upstream changes. Keep in mind that on your
first run, it is expected to take a while as it will download all the required Android source files
and their change histories.

```bash
# Let repo take care of all the hard work
#
# The -j# option specifies the number of concurrent download threads to run.
$ repo sync -j8 --no-clone-bundle --no-tags
```

### Syncing specific projects ###

In case you are not interested in syncing all the projects, you can specify what projects you do
want to sync. This can help if, for example, you want to make a quick change and quickly push it
back for review. You should note that this can sometimes cause issues when building if there is
a large change that spans across multiple projects.

```bash
# Specify one or more projects by either name or path
# For example, enter IntegerROM/android_frameworks_base or
# frameworks/base to sync the frameworks/base repository

$ repo sync $PROJECT
```

### Preparing the Build ###

```bash
# Set up environment
$ source build/envsetup.sh

# Choose a target (eg. potter)
$ lunch aosp_$device-$variant

# Build the code
$ mka bacon
```
