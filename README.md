puppet-phantomjs
===============

Simple puppet module that installs PhantomJS - headless WebKit scriptable with a Javascript API.

Using
-----
To install PhantomJS with the [default module settings](https://github.com/3fs/puppet-phantomjs/blob/master/manifests/init.pp#L3-7), define the `class` like so:

    class { 'phantomjs': }

To specify your own settings:

    class { 'phantomjs':
      package_version => '1.9.7',
      package_update => true,
      install_dir => '/usr/bin',
      source_dir => '/opt',
    }

Note that the module installs the 64-bit version of PhantomJS by default,
which won't work if you're using a 32-bit virtual machine. If you're using
Vagrant, you can update your `Vagrantfile` to use a 64-bit box, like this:

    config.vm.box = "hashicorp/precise64"

Alternatively, if you wish to keep using a 32-bit box, you can tell the
puppet module to install the 32-bit version of PhantomJS:

    class { 'phantomjs':
      source_url => 'https://bitbucket.org/ariya/phantomjs/downloads/phantomjs-1.9.7-linux-i686.tar.bz2'
    }

The module pulls in *curl*, *bzip2* and *libfontconfig1* if you haven't defined those packages yourself.
