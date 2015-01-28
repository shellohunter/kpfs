backup from google code. I am not the auther. :)


kpfs is a filesystem for accessing kuaipan.cn based on FUSE.
=====================================================
(You can use it in commercial software, but please let me know.)
This application is dedicated to my lovely son (Hean Yu).

How to build kpfs from svn source code?
=====================================================
o download:
  svn checkout http://kpfs.googlecode.com/svn/trunk/ kpfs-read-only

o prepare before configure
  please install depends, on ubuntu e.g.:
  sudo apt-get install gtk-doc-tools libfuse-dev libjson0-dev libcurl4-nss-dev liboauth-dev

  - liboauth will be used for oauth to kuaipan.cn
    - maybe you should compile liboauth by yourself
    - http://code.google.com/p/kpfs/wiki/why_and_how_to_compile_install_liboauth_0_9_5
  - json-c will be used for parse response of request to kuaipan, and load/save kpfs.conf and kpfs_oauth.json
  - glib will be used for hash table

o configure:
  cd kpfs-read-only
  ./autogen.sh
  ./configure
  (run ./configure --help for more options)

o build:
  make

o install (need root)
  make install

o prepare before run
  please edit kpfs.conf as you wish, e.g.:
{
        "consumer_key": "xc8D2NfL9c53vkrP",
        "consumer_secret": "p7Lo7Q6XBMipbHBw",
        "mount_point": "/tmp/kpfs",
        "oauth_json_file": "/tmp/kpfs_oauth.json",
        "log_path": "/tmp"
}
  "mount_point" is the mount point which you want mount kuaipan to;
  "oauth_json_file" will store the oauth information, then you do not need to input your ID and Password again on webpage.
  "log_path" is the path which will be used in debug mode.

o run:
  mkdir /tmp/kpfs
  cd src/
  ./kpfs -c ../kpfs.conf

How to build and run kpfs on target board.
=====================================================
TODO

Where can I get more information:
=====================================================
DOC:  docs/* 
BLOG: http://blog.csdn.net/mimepp
WIKI: http://code.google.com/p/kpfs/wiki/
Google Group: http://groups.google.com/group/kpfs
Still have problems please send email to yut616@gmail.com
