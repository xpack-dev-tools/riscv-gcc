# How to publish the GNU MCU Eclipse RISC-V Embedded GCC binaries?

## Build

Before starting the build, perform some checks.

### Check if repos are up-to-date

Be sure everything is committed and pushed

- `gnu-mcu-eclipse/riscv-binutils-gdb.git`
- `gnu-mcu-eclipse/riscv-none-gcc.git`
- `gnu-mcu-eclipse/riscv-newlib.git`

### Check tags

The names should look like `v8.2.0-2.1`.

For the binutils-gdb repo, a separate tag should be present, for the gdb build.

### Check the CHANGELOG file

Generally, apart from packing, there should be no local changes compared 
to the original RISC-V distribution.

Open the `CHANGELOG.txt` file from the
`gnu-mcu-eclipse/riscv-none-gcc-build.git` project git, and check if 
all new entries are in.

Note: if you missed to update the `CHANGELOG.txt` before starting the build, 
edit the file and rerun the build, it should take only a few minutes to 
recreate the archives with the correct file.

### Check the version

The `VERSION` file should refer to the actual release.

### Push the project git

In `gnu-mcu-eclipse/riscv-none-gcc-build.git`, if necessary, merge 
the `develop` branch into `master`.

Push it to GitHub.

Possibly push the helper project too.

### Run the build scripts

When everything is ready, follow the instructions on the 
[build](https://github.com/gnu-mcu-eclipse/riscv-none-gcc-build/blob/master/README.md) 
page.

## Test

Install the binaries on all supported platforms and check if they are 
functional.

## Create a new GitHub release

- go to the [GitHub Releases](https://github.com/gnu-mcu-eclipse/riscv-none-gcc/releases) page
- click **Draft a new release**
- name the tag like **v8.2.0-2.1-20190425** (mind the dashes in the middle!)
- select the target branch (like sifive-gcc-8.2.0-gme)
- name the release like **GNU MCU Eclipse RISC-V Embedded GCC v8.2.0-2.1 20190425** 
(mind the dash and the space)
- as description
  - add a downloads badge like `[![Github Releases (by Release)](https://img.shields.io/github/downloads/gnu-mcu-eclipse/riscv-none-gcc/v8.2.0-2.1-20190425/total.svg)]()`; use empty URL for now
  - draft a short paragraph explaining what are the main changes
- **attach binaries** and SHA (drag and drop from the archives folder will do it)
- **enable** the **pre-release** button
- click the **Publish Release** button

Note: at this moment the system should send a notification to all clients 
watching this project.


## Prepare a new blog post 

In the `gnu-mcu-eclipse.github.io-source.git` web git:

- add a new file to `_posts/riscv-none-gcc/releases`
- name the file like `2018-05-06-riscv-none-gcc-v8-2-0-2-1-20190425-released.md`
- name the post like: **GNU MCU Eclipse RISC-V Embedded GCC v8.2.0-2.1 20190425 released**.
- as `download_url` use the generic `https://github.com/gnu-mcu-eclipse/riscv-none-gcc/releases/tag/v8.2.0-2.1/` 
- update the `date:` field with the current date

If any, close [issues](https://github.com/gnu-mcu-eclipse/riscv-none-gcc/issues) 
on the way. Refer to them as:

- **[Issue:\[#1\]\(...\)]**.

## Update the SHA sums

Copy/paste the build report at the end of the post as:

```console
## Checksums
The SHA-256 hashes for the files are:

fdb6ab5badd0820e0562c288b1ec88566f8589f5fa26d81a0f57a2b95213d0cc
gnu-mcu-eclipse-riscv-none-gcc-7.2.0-3-20190425-1300-centos32.tgz

dd6985729df5c2182cc5ce699013146b4addc80cbe231a7b62ec89d095e81aca
gnu-mcu-eclipse-riscv-none-gcc-7.2.0-3-20190425-1300-centos64.tgz

5e10320563e49dd31a33a032496547375d0e07191df727d393e26daa14d3f526
gnu-mcu-eclipse-riscv-none-gcc-7.2.0-3-20190425-1300-macos.tgz

737f95fb3129b0e7f67c48fea39b844f574c379768bd0ea5088a6e976f8f7b14
gnu-mcu-eclipse-riscv-none-gcc-7.2.0-3-20190425-1300-win32.zip

98ac277287d8c51cc1c5f83a5a9945951bd8d5806b4570b41eea2c306e141a3b
gnu-mcu-eclipse-riscv-none-gcc-7.2.0-3-20190425-1300-win64.zip
```

## Update the Web

- commit the `gnu-mcu-eclipse.github.io-source` project; use a message 
like **GNU MCU Eclipse RISC-V Embedded GCC v8.2.0-2.1 20190425 released**
- wait for the Travis build to complete; occasionally links to not work,
 and might need to restart the build
- remember the post URL, since it must be updated in the release page

## Create the xPack release

Follow the instructions from the 
[gnu-mcu-eclipse/riscv-none-gcc-xpack](https://github.com/gnu-mcu-eclipse/riscv-none-gcc-xpack/blob/xpack/README.md#maintainer-info)
page.

## Create a final GitHub release

- go to the [GitHub Releases](https://github.com/gnu-mcu-eclipse/riscv-none-gcc/releases) page
- update the link behind the badge with the blog URL
- add a link to the Web page `[Continue reading »]()`; use an same blog URL
- copy/paste the **Easy install** section
- update the current release version
- copy/paste the **Download analytics** section
- update the current release version
- **disable** the **pre-release** button
- click the **Update Release** button

## Share on Facebook

- go to the new post and follow the Share link.
- DO NOT select **On your own Timeline**, but **On a Page you manage**
- select GNU MCU Eclipse
- posting as GNU MCU Eclipse
- click **Post to Facebook**
- check the post in the [Facebook page](https://www.facebook.com/gnu-mcu-eclipse)

## Share on Twitter

* go to the new post and follow the Tweet link
* copy the content to the clipboard
* DO NOT click the Tweet button here, it'll not use the right account
* in a separate browser windows, open [TweetDeck](https://tweetdeck.twitter.com/)
* using the `@gnu_mcu_eclipse` account, paste the content
* click the Tweet button
