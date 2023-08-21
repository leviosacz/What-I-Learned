# Fix "aclocal: not found" Error on Ubuntu/Linux

Encountered the frustrating "aclocal: not found" error while running a script on Ubuntu/Linux? No worries, here's a quick guide to get you back on track.

## Understanding the Error

When you see an error message like the one below while running a script, it means that the 'aclocal' command is missing:

```bash
./autogen.sh: 11: aclocal: not found
```

## Step 1: Install Required Packages

To fix this issue, you need to install the necessary packages: `autotools-dev` and `automake`. Open a terminal and run:

```bash
$ sudo apt-get update
$ sudo apt-get install autotools-dev
$ sudo apt-get install automake
```

## Step 2: Execute the Script Again

Once the packages are installed, run your script again. You should see it executing successfully this time:

```bash
$ ./autogen.sh
+ test -d Tools/config
+ aclocal -I Tools/config
+ autoheader
+ automake --add-missing --copy --force-missing
...
```

## Conclusion

The "aclocal: not found" error can be resolved by installing the `autotools-dev` and `automake` packages. These packages provide essential tools for the build process and ensure that your scripts run without a hitch.

Happy coding!