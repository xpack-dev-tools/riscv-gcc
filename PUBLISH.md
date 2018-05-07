# How to publish the GNU MCU Eclipse RISC-V Embedded GCC binaries?

## Update the Change log

Generally, apart from packing, there should be no local changes compared 
to the original RISC-V distribution.

Open the `CHANGELOG.txt` file from  
`gnu-mcu-eclipse/riscv-none-gcc-build.git` project git, and copy 
entries to the web git.

In the web git, add new entries to the 
[Change log](https://gnu-mcu-eclipse.github.io/toolchain/riscv/change-log/) 
(`pages/toolchain/riscv/change-log.md`), grouped by days.

Note: if you missed to update the `CHANGELOG.txt` before starting the build, 
edit the file and rerun the build, it should take only a few minutes to 
recreate the archives with the correct file.

## Commit all project git

Commit all

- `gnu-mcu-eclipse/riscv-binutils-gdb.git`
- `gnu-mcu-eclipse/riscv-none-gcc.git`
- `gnu-mcu-eclipse/riscv-newlib.git`

## Edit the build script

Edit the `VERSION` file to refer to the actual release.

## Push the build script git

Push `gnu-mcu-eclipse/riscv-none-gcc-build.git` to GitHub.

Possibly push the helper project too.

## Build

Follow the instructions on the 
[build](https://github.com/gnu-mcu-eclipse/riscv-none-gcc-build/blob/master/README.md) 
page.

## Prepare a new blog post 

In the web git:

- add a new file to `_posts/riscv-none-gcc/releases`
- name the file like `2018-05-06-riscv-none-gcc-v7-2-0-3-20180506-released.md`
- name the post like: **GNU MCU Eclipse RISC-V Embedded GCC v7.2.0-3-20180506 released**.
- as `download_url` use the generic `https://github.com/gnu-mcu-eclipse/riscv-none-gcc/releases/` 
- update the `date:` field with the current date

If any, close [issues](https://github.com/gnu-mcu-eclipse/riscv-none-gcc/issues) 
on the way. Refer to them as:

- **[Issue:\[#1\]\(...\)]**.

## Update the SHA sums

Copy/paste the build report at the end of the post as:

```console
## Checksums
The SHA-256 hashes for the files are:

fdb6ab5badd0820e0562c288b1ec88566f8589f5fa26d81a0f57a2b95213d0cc ?
gnu-mcu-eclipse-riscv-none-gcc-7.2.0-3-20180506-1300-centos32.tgz

dd6985729df5c2182cc5ce699013146b4addc80cbe231a7b62ec89d095e81aca ?
gnu-mcu-eclipse-riscv-none-gcc-7.2.0-3-20180506-1300-centos64.tgz

5e10320563e49dd31a33a032496547375d0e07191df727d393e26daa14d3f526 ?
gnu-mcu-eclipse-riscv-none-gcc-7.2.0-3-20180506-1300-macos.tgz

737f95fb3129b0e7f67c48fea39b844f574c379768bd0ea5088a6e976f8f7b14 ?
gnu-mcu-eclipse-riscv-none-gcc-7.2.0-3-20180506-1300-win32.zip

98ac277287d8c51cc1c5f83a5a9945951bd8d5806b4570b41eea2c306e141a3b ?
gnu-mcu-eclipse-riscv-none-gcc-7.2.0-3-20180506-1300-win64.zip
```

## Update the Web

- commit the `gnu-mcu-eclipse.github.io-source` project; use a message 
like **GNU MCU Eclipse RISC-V Embedded GCC v7.2.0-3-20180506 released**
- wait for the Travis build to complete; occasionally links to not work,
 and might need to restart the build.
- remember the post URL, since it must be updated in the release page

Note: initially the link to binaries points to the parent releases folder, 
otherwise Travis will complain and do not publish the site to 
`gnu-mcu-eclipse.github.io`.

## Create a new GitHub release

- go to the [GitHub Releases](https://github.com/gnu-mcu-eclipse/riscv-none-gcc/releases) page
- click **Draft a new release**
- name the tag like **v7.2.0-3-20180506** (mind the dashes in the middle!)
- name the release like **GNU MCU Eclipse RISC-V Embedded GCC v7.2.0-3 20180506** 
(mind the dash and the space)
- as description
  - add a downloads badge like `[![Github Releases (by Release)](https://img.shields.io/github/downloads/gnu-mcu-eclipse/riscv-none-gcc/v7.2.0-3-20180506/total.svg)]()`; use empty URL for now
  - copy the first paragraph from the Web release page
- add a link to the Web page `[Continue reading »]()`; use an empty URL for now
- get URL from web and update the above links
- **attach binaries** and SHA (drag and drop from the archives folder will do it)
- click the **Publish Release** button

Note: at this moment the system should send a notification to all clients watching this project.

## Update the web link 

In the web git:

- `download_url: https://github.com/gnu-mcu-eclipse/riscv-none-gcc/releases/tag/v7.2.0-3-20180506`
- use something like `v7.2.0-3-20180506 update link` as message

## Share on Facebook

- go to the new post and follow the Share link.
- DO NOT select **On your own Timeline**, but **On a Page you manage**
- select GNU MCU Eclipse
- posting as GNU MCU Eclipse
- click **Post to Facebook**
- check the post in the [Facebook page](https://www.facebook.com/gnu-mcu-eclipse)

