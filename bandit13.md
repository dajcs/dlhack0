bandit12@bandit:~$ mktemp -d
/tmp/tmp.k3pFckSuou
bandit12@bandit:~$ 


You can find the header formats in the descriptions:

    Zip (.zip) format description, starts with 0x50, 0x4b, 0x03, 0x04 (unless empty — then the last two are 0x05, 0x06 or 0x06, 0x06)
    Gzip (.gz) format description, starts with 0x1f, 0x8b, 0x08
    xz (.xz) format description, starts with 0xfd, 0x37, 0x7a, 0x58, 0x5a, 0x00

Others:

    zlib (.zz) format description, starts with two bytes (in bits) 0aaa1000 bbbccccc, where ccccc is chosen so that the first byte viewed as a int16 times 256 plus the second byte viewed as a int16 is a multiple of 31. e.g: 01111000(bits) = 120(int16), 10011100(bits) = 156(int16), 120 * 256 + 156 = 30876 which is a multiple of 31
    compress (.Z) starts with 0x1f, 0x9d
    bzip2 (.bz2) starts with 0x42, 0x5a, 0x68
    Zstandard (.zstd) format description, frame starts with a 4 byte magic number using little-endian format 0xFD2FB528, a skipable frame starts with 0x184D2A5? (question mark is any value from 0 to F), and dictionary starts with 0xEC30A437.


bandit12@bandit:~$ mktemp -d
/tmp/tmp.k3pFckSuou
bandit12@bandit:~$ ls -al
total 24
drwxr-xr-x   2 root     root     4096 Apr  3 15:17 .
drwxr-xr-x 150 root     root     4096 Apr  3 15:20 ..
-rw-r--r--   1 root     root      220 Mar 31  2024 .bash_logout
-rw-r--r--   1 root     root     3851 Apr  3 15:10 .bashrc
-rw-r-----   1 bandit13 bandit12 2575 Apr  3 15:17 data.txt
-rw-r--r--   1 root     root      807 Mar 31  2024 .profile
bandit12@bandit:~$ cd /tmp
bandit12@bandit:/tmp$ ls -al
ls: cannot open directory '.': Permission denied
bandit12@bandit:/tmp$ cd tmp.k3pFckSuou
bandit12@bandit:/tmp/tmp.k3pFckSuou$ 
bandit12@bandit:/tmp/tmp.k3pFckSuou$ 
bandit12@bandit:/tmp/tmp.k3pFckSuou$ cd
bandit12@bandit:~$ mkdir
mkdir: missing operand
Try 'mkdir --help' for more information.
bandit12@bandit:~$ mkdir /tmp/b13
bandit12@bandit:~$ cp data.txt /tmp/b13
bandit12@bandit:~$ cd /tmp/b13
bandit12@bandit:/tmp/b13$ ls -al
total 11996
drwxrwxr-x    2 bandit12 bandit12     4096 May 29 09:14 .
drwxrwx-wt 2565 root     root     12271616 May 29 09:14 ..
-rw-r-----    1 bandit12 bandit12     2575 May 29 09:14 data.txt
bandit12@bandit:/tmp/b13$ cat data.txt 
00000000: 1f8b 0808 00da cf69 0203 6461 7461 322e  .......i..data2.
00000010: 6269 6e00 0136 02c9 fd42 5a68 3931 4159  bin..6...BZh91AY
00000020: 2653 5978 ae89 f600 001c 7fff db7d bfef  &SYx.........}..
00000030: 8ff7 f7ff ffc2 ffcd 7cbd 2ee4 dff9 aff3  ........|.......
00000040: ef7b d577 e9f7 adbd dfbb fbff b001 3b30  .{.w..........;0
00000050: 63a0 6806 8326 400d 0031 0000 00d1 a313  c.h..&@..1......
00000060: 2000 001a 034d 1a19 0000 0032 0681 89a6   ....M.....2....
00000070: 9a32 0da9 934c 6847 9220 0034 0346 9a00  .2...LhG. .4.F..
00000080: d340 3462 0006 d4d3 d41a 064d 0308 6868  .@4b.......M..hh
00000090: 0340 1a19 3264 321b 50f5 00c8 01ea 0d00  .@..2d2.P.......
000000a0: 7a80 d00d 030e 9ea1 a3d2 6231 0346 20c4  z.........b1.F .
000000b0: c801 a068 c200 d188 687a 9a00 0340 0000  ...h....hz...@..
000000c0: 0034 0d34 d034 c8c2 34c8 0c9a 3400 0013  .4.4.4..4...4...
000000d0: 6006 9600 30e0 6902 600b 990b ffd0 6e9e  `...0.i.`.....n.
000000e0: a8fc 1813 42c5 2e19 2331 c580 7009 1956  ....B...#1..p..V
000000f0: 3156 0e5f 2ff4 d9a9 12f3 f97c 4c4b 0127  1V._/......|LK.'
00000100: 5a43 cdd9 3ec3 c4e5 eedb 7357 7d5a 3054  ZC..>.....sW}Z0T
00000110: 1d24 7fc5 562f 1a86 8ac8 5a19 7890 125c  .$..V/....Z.x..\
00000120: 103b 6d80 fbf1 fdec 2d7e 1838 e1ed 3dae  .;m.....-~.8..=.
00000130: 47d8 5023 073f 3a1b 2c10 6784 9c90 b67d  G.P#.?:.,.g....}
00000140: 3ba5 3515 9a10 7002 2eca c60c 38c7 3ccd  ;.5...p.....8.<.
00000150: e3fd 7af3 a647 086c 5e7f 5bd0 d526 128f  ..z..G.l^.[..&..
00000160: ace4 2bd0 d744 e9cf 5182 8886 4a26 a938  ..+..D..Q...J&.8
00000170: f860 c668 c5ad 8444 98e4 cbd8 ca6f c22b  .`.h...D.....o.+
00000180: afa2 3cdc c540 03b2 387b 4309 c9a0 913a  ..<..@..8{C....:
00000190: a9c5 0d39 dab7 9544 b83b dca3 9466 5020  ...9...D.;...fP 
000001a0: 2a3f 3bc8 552d 426f e422 7a99 2cd0 ed62  *?;.U-Bo."z.,..b
000001b0: ac90 0bac 1a3e fbb2 a3e3 5a34 a0c8 785f  .....>....Z4..x_
000001c0: d2a9 3a57 a554 35a8 76df 18da f622 21f6  ..:W.T5.v...."!.
000001d0: b3f0 56ab 68ad 6825 3926 9491 60a1 f979  ..V.h.h%9&..`..y
000001e0: 6203 ad30 0482 1684 d9f3 c0cf 68ac 63b9  b..0........h.c.
000001f0: ed20 ea11 7fb6 78ad 4366 f218 2549 d2b8  . ....x.Cf..%I..
00000200: 0268 5f2b 0678 85de 283b 3807 9aba 6e2c  .h_+.x..(;8...n,
00000210: 1061 04c0 0007 85f4 511e e974 bcc6 cfc8  .a......Q..t....
00000220: 3889 3265 ff28 c2f9 2f2a d163 290b bb90  8.2e.(../*.c)...
00000230: 5274 43e0 0054 86d7 cce2 5933 7dd3 1e95  RtC..T....Y3}...
00000240: 4fb8 4103 fe2e e48a 70a1 20f1 5d13 ecd3  O.A.....p. .]...
00000250: 2afd bb36 0200 00                        *..6...
bandit12@bandit:/tmp/b13$ ls -l
total 4
-rw-r----- 1 bandit12 bandit12 2575 May 29 09:14 data.txt
bandit12@bandit:/tmp/b13$ gunzip data.txt
gzip: data.txt: unknown suffix -- ignored
bandit12@bandit:/tmp/b13$ cp data.txt data.zip
bandit12@bandit:/tmp/b13$ gunzip data.zip
gzip: data.zip: unknown suffix -- ignored
bandit12@bandit:/tmp/b13$ mv data.zip data.gzip
bandit12@bandit:/tmp/b13$ gunzip data.gzip
gzip: data.gzip: unknown suffix -- ignored
bandit12@bandit:/tmp/b13$ mv data.gzip data.gz
bandit12@bandit:/tmp/b13$ gunzip data.gz

gzip: data.gz: not in gzip format
bandit12@bandit:/tmp/b13$ cat data.txt
00000000: 1f8b 0808 00da cf69 0203 6461 7461 322e  .......i..data2.
00000010: 6269 6e00 0136 02c9 fd42 5a68 3931 4159  bin..6...BZh91AY
00000020: 2653 5978 ae89 f600 001c 7fff db7d bfef  &SYx.........}..
00000030: 8ff7 f7ff ffc2 ffcd 7cbd 2ee4 dff9 aff3  ........|.......
00000040: ef7b d577 e9f7 adbd dfbb fbff b001 3b30  .{.w..........;0
00000050: 63a0 6806 8326 400d 0031 0000 00d1 a313  c.h..&@..1......
00000060: 2000 001a 034d 1a19 0000 0032 0681 89a6   ....M.....2....
00000070: 9a32 0da9 934c 6847 9220 0034 0346 9a00  .2...LhG. .4.F..
00000080: d340 3462 0006 d4d3 d41a 064d 0308 6868  .@4b.......M..hh
00000090: 0340 1a19 3264 321b 50f5 00c8 01ea 0d00  .@..2d2.P.......
000000a0: 7a80 d00d 030e 9ea1 a3d2 6231 0346 20c4  z.........b1.F .
000000b0: c801 a068 c200 d188 687a 9a00 0340 0000  ...h....hz...@..
000000c0: 0034 0d34 d034 c8c2 34c8 0c9a 3400 0013  .4.4.4..4...4...
000000d0: 6006 9600 30e0 6902 600b 990b ffd0 6e9e  `...0.i.`.....n.
000000e0: a8fc 1813 42c5 2e19 2331 c580 7009 1956  ....B...#1..p..V
000000f0: 3156 0e5f 2ff4 d9a9 12f3 f97c 4c4b 0127  1V._/......|LK.'
00000100: 5a43 cdd9 3ec3 c4e5 eedb 7357 7d5a 3054  ZC..>.....sW}Z0T
00000110: 1d24 7fc5 562f 1a86 8ac8 5a19 7890 125c  .$..V/....Z.x..\
00000120: 103b 6d80 fbf1 fdec 2d7e 1838 e1ed 3dae  .;m.....-~.8..=.
00000130: 47d8 5023 073f 3a1b 2c10 6784 9c90 b67d  G.P#.?:.,.g....}
00000140: 3ba5 3515 9a10 7002 2eca c60c 38c7 3ccd  ;.5...p.....8.<.
00000150: e3fd 7af3 a647 086c 5e7f 5bd0 d526 128f  ..z..G.l^.[..&..
00000160: ace4 2bd0 d744 e9cf 5182 8886 4a26 a938  ..+..D..Q...J&.8
00000170: f860 c668 c5ad 8444 98e4 cbd8 ca6f c22b  .`.h...D.....o.+
00000180: afa2 3cdc c540 03b2 387b 4309 c9a0 913a  ..<..@..8{C....:
00000190: a9c5 0d39 dab7 9544 b83b dca3 9466 5020  ...9...D.;...fP 
000001a0: 2a3f 3bc8 552d 426f e422 7a99 2cd0 ed62  *?;.U-Bo."z.,..b
000001b0: ac90 0bac 1a3e fbb2 a3e3 5a34 a0c8 785f  .....>....Z4..x_
000001c0: d2a9 3a57 a554 35a8 76df 18da f622 21f6  ..:W.T5.v...."!.
000001d0: b3f0 56ab 68ad 6825 3926 9491 60a1 f979  ..V.h.h%9&..`..y
000001e0: 6203 ad30 0482 1684 d9f3 c0cf 68ac 63b9  b..0........h.c.
000001f0: ed20 ea11 7fb6 78ad 4366 f218 2549 d2b8  . ....x.Cf..%I..
00000200: 0268 5f2b 0678 85de 283b 3807 9aba 6e2c  .h_+.x..(;8...n,
00000210: 1061 04c0 0007 85f4 511e e974 bcc6 cfc8  .a......Q..t....
00000220: 3889 3265 ff28 c2f9 2f2a d163 290b bb90  8.2e.(../*.c)...
00000230: 5274 43e0 0054 86d7 cce2 5933 7dd3 1e95  RtC..T....Y3}...
00000240: 4fb8 4103 fe2e e48a 70a1 20f1 5d13 ecd3  O.A.....p. .]...
00000250: 2afd bb36 0200 00                        *..6...
bandit12@bandit:/tmp/b13$ mv data.gz data.bz2
bandit12@bandit:/tmp/b13$ bzip2 --decompress data.bz2
bzip2: data.bz2 is not a bzip2 file.
bandit12@bandit:/tmp/b13$ mv data.bz2 data.bin.gz
bandit12@bandit:/tmp/b13$ gunzip data.bin.gz

gzip: data.bin.gz: not in gzip format
bandit12@bandit:/tmp/b13$ 
bandit12@bandit:/tmp/b13$ ls -al
total 12000
drwxrwxr-x    2 bandit12 bandit12     4096 May 29 09:23 .
drwxrwx-wt 2566 root     root     12271616 May 29 09:24 ..
-rw-r-----    1 bandit12 bandit12     2575 May 29 09:16 data.bin.gz
-rw-r-----    1 bandit12 bandit12     2575 May 29 09:14 data.txt
bandit12@bandit:/tmp/b13$ gzip --list data.bin.gz

gzip: data.bin.gz: not in gzip format
bandit12@bandit:/tmp/b13$ xxd -revert -postscript data.txt data.bin
bandit12@bandit:/tmp/b13$ ls -l
total 12
-rw-rw-r-- 1 bandit12 bandit12  752 May 29 09:28 data.bin
-rw-r----- 1 bandit12 bandit12 2575 May 29 09:16 data.bin.gz
-rw-r----- 1 bandit12 bandit12 2575 May 29 09:14 data.txt
bandit12@bandit:/tmp/b13$ cat 752
cat: 752: No such file or directory
bandit12@bandit:/tmp/b13$ cat data.bin
4�4��4� ����h�шhz�@�4@2d2�������}��0��������|�.�����@�{�w����߻���;0Pc�h�&@
       �4�`�0�i`
                �
                 ��n���B�.#1ŀp  V�1V_/�٩��|LK'ZC��>�����sW}Z0T$�V/���Zx�\ ;m�����-~8��=�0G�P#?:����}@;�5�p.��
                                                                                                             8�<�P��z�l^[��&�`��+��9ڷ�D�;ܣ�fP �*?;�U-Bo�"z�,��b�����@�8{C  ɠ�:���
                               �>����Z4��x_�ҩ:W�T5�v���"!�г�V�h�h%9&��`��y�b�0������h�c��� ��x�Cf�%IҸh_+x��(;8��n,a���Q�t���� 8�2e�(��/*�c)
        ��.0RtC�T����Y3}��@O�A�.�p� �]��P*��6bandit12@bandit:/tmp/b13$ rm data.bin.gz
bandit12@bandit:/tmp/b13$ mv data.bin data.bin.gz
bandit12@bandit:/tmp/b13$ gunzip data.bin.gz

gzip: data.bin.gz: not in gzip format
bandit12@bandit:/tmp/b13$ ls -l
total 8
-rw-rw-r-- 1 bandit12 bandit12  752 May 29 09:28 data.bin.gz
-rw-r----- 1 bandit12 bandit12 2575 May 29 09:14 data.txt
bandit12@bandit:/tmp/b13$ bzip2 --decompress data.bin.gz
bzip2: Can't guess original name for data.bin.gz -- using data.bin.gz.out
bzip2: data.bin.gz is not a bzip2 file.
bandit12@bandit:/tmp/b13$ cp data.bin.gz data.bin.bz2
bandit12@bandit:/tmp/b13$ bzip2 --decompress data.bin.bz2
bzip2: data.bin.bz2 is not a bzip2 file.
bandit12@bandit:/tmp/b13$ man xxd
bandit12@bandit:/tmp/b13$ ls -l
total 12
-rw-rw-r-- 1 bandit12 bandit12  752 May 29 09:30 data.bin.bz2
-rw-rw-r-- 1 bandit12 bandit12  752 May 29 09:28 data.bin.gz
-rw-r----- 1 bandit12 bandit12 2575 May 29 09:14 data.txt
bandit12@bandit:/tmp/b13$ rm data.bin.*
bandit12@bandit:/tmp/b13$ xxd -r data.txt data.bin
bandit12@bandit:/tmp/b13$ ls -l
total 8
-rw-rw-r-- 1 bandit12 bandit12  599 May 29 09:32 data.bin
-rw-r----- 1 bandit12 bandit12 2575 May 29 09:14 data.txt
bandit12@bandit:/tmp/b13$ mv data.bin data.bin.gz
bandit12@bandit:/tmp/b13$ gunzip data.bin.gz
bandit12@bandit:/tmp/b13$ ls -lrt
total 8
-rw-r----- 1 bandit12 bandit12 2575 May 29 09:14 data.txt
-rw-rw-r-- 1 bandit12 bandit12  566 May 29 09:32 data.bin
bandit12@bandit:/tmp/b13$ cat data.bin
4�4��4� ���h�шhz�@4@2d2���|�.������{�w����߻���;0c�h�&@
       �4`�0�i`
               �
                ��n���B�.#1ŀp   V1V_/�٩��|LK'ZC��>�����sW}Z0T$�V/���Zx�\;m�����-~8��=�G�P#?:����};�5�p.��
                                                                                                         8�<���z�l^[��&���+��D��Q��9ڷ�D�;ܣ�fP *?;�U-Bo�"z�,��b��C  ɠ�:��
                             �>����Z4��x_ҩ:W�T5�v���"!���V�h�h%9&��`��yb�0������h�c�� ��x�Cf�%IҸh_+x��(;8��n,a���Q�t����8�2e�(��/*�c)
  ��RtC�T����Y3}��O�A�.�p� �]�bandit12@bandit:/tmp/b13$ ls -lrt
total 8
-rw-r----- 1 bandit12 bandit12 2575 May 29 09:14 data.txt
-rw-rw-r-- 1 bandit12 bandit12  566 May 29 09:32 data.bin
bandit12@bandit:/tmp/b13$ xxd data.bin data.bin.txt
bandit12@bandit:/tmp/b13$ ls -l
total 24
-rw-rw-r-- 1 bandit12 bandit12   566 May 29 09:32 data.bin
-rw-rw-r-- 1 bandit12 bandit12 15000 May 29 09:34 data.bin.txt
-rw-r----- 1 bandit12 bandit12  2575 May 29 09:14 data.txt
bandit12@bandit:/tmp/b13$ cat data.bin.txt
00000000: 425a 6839 3141 5926 5359 78ae 89f6 0000  BZh91AY&SYx.....
00000010: 1c7f ffdb 7dbf ef8f f7f7 ffff c2ff cd7c  ....}..........|
00000020: bd2e e4df f9af f3ef 7bd5 77e9 f7ad bddf  ........{.w.....
00000030: bbfb ffb0 013b 3063 a068 0683 2640 0d00  .....;0c.h..&@..
00000040: 3100 0000 d1a3 1320 0000 1a03 4d1a 1900  1...... ....M...
00000050: 0000 3206 8189 a69a 320d a993 4c68 4792  ..2.....2...LhG.
00000060: 2000 3403 469a 00d3 4034 6200 06d4 d3d4   .4.F...@4b.....
00000070: 1a06 4d03 0868 6803 401a 1932 6432 1b50  ..M..hh.@..2d2.P
00000080: f500 c801 ea0d 007a 80d0 0d03 0e9e a1a3  .......z........
00000090: d262 3103 4620 c4c8 01a0 68c2 00d1 8868  .b1.F ....h....h
000000a0: 7a9a 0003 4000 0000 340d 34d0 34c8 c234  z...@...4.4.4..4
000000b0: c80c 9a34 0000 1360 0696 0030 e069 0260  ...4...`...0.i.`
000000c0: 0b99 0bff d06e 9ea8 fc18 1342 c52e 1923  .....n.....B...#
000000d0: 31c5 8070 0919 5631 560e 5f2f f4d9 a912  1..p..V1V._/....
000000e0: f3f9 7c4c 4b01 275a 43cd d93e c3c4 e5ee  ..|LK.'ZC..>....
000000f0: db73 577d 5a30 541d 247f c556 2f1a 868a  .sW}Z0T.$..V/...
00000100: c85a 1978 9012 5c10 3b6d 80fb f1fd ec2d  .Z.x..\.;m.....-
00000110: 7e18 38e1 ed3d ae47 d850 2307 3f3a 1b2c  ~.8..=.G.P#.?:.,
00000120: 1067 849c 90b6 7d3b a535 159a 1070 022e  .g....};.5...p..
00000130: cac6 0c38 c73c cde3 fd7a f3a6 4708 6c5e  ...8.<...z..G.l^
00000140: 7f5b d0d5 2612 8fac e42b d0d7 44e9 cf51  .[..&....+..D..Q
00000150: 8288 864a 26a9 38f8 60c6 68c5 ad84 4498  ...J&.8.`.h...D.
00000160: e4cb d8ca 6fc2 2baf a23c dcc5 4003 b238  ....o.+..<..@..8
00000170: 7b43 09c9 a091 3aa9 c50d 39da b795 44b8  {C....:...9...D.
00000180: 3bdc a394 6650 202a 3f3b c855 2d42 6fe4  ;...fP *?;.U-Bo.
00000190: 227a 992c d0ed 62ac 900b ac1a 3efb b2a3  "z.,..b.....>...
000001a0: e35a 34a0 c878 5fd2 a93a 57a5 5435 a876  .Z4..x_..:W.T5.v
000001b0: df18 daf6 2221 f6b3 f056 ab68 ad68 2539  ...."!...V.h.h%9
000001c0: 2694 9160 a1f9 7962 03ad 3004 8216 84d9  &..`..yb..0.....
000001d0: f3c0 cf68 ac63 b9ed 20ea 117f b678 ad43  ...h.c.. ....x.C
000001e0: 66f2 1825 49d2 b802 685f 2b06 7885 de28  f..%I...h_+.x..(
000001f0: 3b38 079a ba6e 2c10 6104 c000 0785 f451  ;8...n,.a......Q
00000200: 1ee9 74bc c6cf c838 8932 65ff 28c2 f92f  ..t....8.2e.(../
00000210: 2ad1 6329 0bbb 9052 7443 e000 5486 d7cc  *.c)...RtC..T...
00000220: e259 337d d31e 954f b841 03fe 2ee4 8a70  .Y3}...O.A.....p
00000230: a120 f15d 13ec                           . .]..
bandit12@bandit:/tmp/b13$ ls -l
total 24
-rw-rw-r-- 1 bandit12 bandit12   566 May 29 09:32 data.bin
-rw-rw-r-- 1 bandit12 bandit12 15000 May 29 09:34 data.bin.txt
-rw-r----- 1 bandit12 bandit12  2575 May 29 09:14 data.txt
bandit12@bandit:/tmp/b13$ rm data.bin.txt
bandit12@bandit:/tmp/b13$ 
bandit12@bandit:/tmp/b13$ 
bandit12@bandit:/tmp/b13$ 
bandit12@bandit:/tmp/b13$ 
bandit12@bandit:/tmp/b13$ cat data.txt
00000000: 1f8b 0808 00da cf69 0203 6461 7461 322e  .......i..data2.
00000010: 6269 6e00 0136 02c9 fd42 5a68 3931 4159  bin..6...BZh91AY
00000020: 2653 5978 ae89 f600 001c 7fff db7d bfef  &SYx.........}..
00000030: 8ff7 f7ff ffc2 ffcd 7cbd 2ee4 dff9 aff3  ........|.......
00000040: ef7b d577 e9f7 adbd dfbb fbff b001 3b30  .{.w..........;0
00000050: 63a0 6806 8326 400d 0031 0000 00d1 a313  c.h..&@..1......
00000060: 2000 001a 034d 1a19 0000 0032 0681 89a6   ....M.....2....
00000070: 9a32 0da9 934c 6847 9220 0034 0346 9a00  .2...LhG. .4.F..
00000080: d340 3462 0006 d4d3 d41a 064d 0308 6868  .@4b.......M..hh
00000090: 0340 1a19 3264 321b 50f5 00c8 01ea 0d00  .@..2d2.P.......
000000a0: 7a80 d00d 030e 9ea1 a3d2 6231 0346 20c4  z.........b1.F .
000000b0: c801 a068 c200 d188 687a 9a00 0340 0000  ...h....hz...@..
000000c0: 0034 0d34 d034 c8c2 34c8 0c9a 3400 0013  .4.4.4..4...4...
000000d0: 6006 9600 30e0 6902 600b 990b ffd0 6e9e  `...0.i.`.....n.
000000e0: a8fc 1813 42c5 2e19 2331 c580 7009 1956  ....B...#1..p..V
000000f0: 3156 0e5f 2ff4 d9a9 12f3 f97c 4c4b 0127  1V._/......|LK.'
00000100: 5a43 cdd9 3ec3 c4e5 eedb 7357 7d5a 3054  ZC..>.....sW}Z0T
00000110: 1d24 7fc5 562f 1a86 8ac8 5a19 7890 125c  .$..V/....Z.x..\
00000120: 103b 6d80 fbf1 fdec 2d7e 1838 e1ed 3dae  .;m.....-~.8..=.
00000130: 47d8 5023 073f 3a1b 2c10 6784 9c90 b67d  G.P#.?:.,.g....}
00000140: 3ba5 3515 9a10 7002 2eca c60c 38c7 3ccd  ;.5...p.....8.<.
00000150: e3fd 7af3 a647 086c 5e7f 5bd0 d526 128f  ..z..G.l^.[..&..
00000160: ace4 2bd0 d744 e9cf 5182 8886 4a26 a938  ..+..D..Q...J&.8
00000170: f860 c668 c5ad 8444 98e4 cbd8 ca6f c22b  .`.h...D.....o.+
00000180: afa2 3cdc c540 03b2 387b 4309 c9a0 913a  ..<..@..8{C....:
00000190: a9c5 0d39 dab7 9544 b83b dca3 9466 5020  ...9...D.;...fP 
000001a0: 2a3f 3bc8 552d 426f e422 7a99 2cd0 ed62  *?;.U-Bo."z.,..b
000001b0: ac90 0bac 1a3e fbb2 a3e3 5a34 a0c8 785f  .....>....Z4..x_
000001c0: d2a9 3a57 a554 35a8 76df 18da f622 21f6  ..:W.T5.v...."!.
000001d0: b3f0 56ab 68ad 6825 3926 9491 60a1 f979  ..V.h.h%9&..`..y
000001e0: 6203 ad30 0482 1684 d9f3 c0cf 68ac 63b9  b..0........h.c.
000001f0: ed20 ea11 7fb6 78ad 4366 f218 2549 d2b8  . ....x.Cf..%I..
00000200: 0268 5f2b 0678 85de 283b 3807 9aba 6e2c  .h_+.x..(;8...n,
00000210: 1061 04c0 0007 85f4 511e e974 bcc6 cfc8  .a......Q..t....
00000220: 3889 3265 ff28 c2f9 2f2a d163 290b bb90  8.2e.(../*.c)...
00000230: 5274 43e0 0054 86d7 cce2 5933 7dd3 1e95  RtC..T....Y3}...
00000240: 4fb8 4103 fe2e e48a 70a1 20f1 5d13 ecd3  O.A.....p. .]...
00000250: 2afd bb36 0200 00                        *..6...
bandit12@bandit:/tmp/b13$ cat data.bin
4�4��4� ���h�шhz�@4@2d2���|�.������{�w����߻���;0c�h�&@
       �4`�0�i`
               �
                ��n���B�.#1ŀp   V1V_/�٩��|LK'ZC��>�����sW}Z0T$�V/���Zx�\;m�����-~8��=�G�P#?:����};�5�p.��
                                                                                                         8�<���z�l^[��&���+��D��Q��9ڷ�D�;ܣ�fP *?;�U-Bo�"z�,��b��C  ɠ�:��
                             �>����Z4��x_ҩ:W�T5�v���"!���V�h�h%9&��`��yb�0������h�c�� ��x�Cf�%IҸh_+x��(;8��n,a���Q�t����8�2e�(��/*�c)
  ��RtC�T����Y3}��O�A�.�p� �]�bandit12@bandit:/tmp/b13$ gunzip data.bin
gzip: data.bin: unknown suffix -- ignored
bandit12@bandit:/tmp/b13$ bzip2 --decompress data.bin
bzip2: Can't guess original name for data.bin -- using data.bin.out
bandit12@bandit:/tmp/b13$ ls -l
total 8
-rw-rw-r-- 1 bandit12 bandit12  428 May 29 09:32 data.bin.out
-rw-r----- 1 bandit12 bandit12 2575 May 29 09:14 data.txt
bandit12@bandit:/tmp/b13$ cat data.bin.out 
��idata4.bin��AH�q���x1�D��`��[����wSO�F�dM1��6������:�
                                                       /�ɋ2F�D�B�.�q.�)��U��\���y.�X$1w���)��A-8Ru�w�����7̓���.T�(����HRUE2�H����*V���W��x�^�x��C��n�aggx���W���ڗ��ގ俪=52U�'�b      �?V��k�*����0l;�ǲ����@�u&��Q
                                                                            =*�#*l�G�n�̰P�Us�S�^9kɝ���7��W��-��.On�j���<����%�F>ߞ�䖮<�
?�6�b�^�tl�V����,Ժ��-燫cj��gs0|n|S>�?*��߼X��O��
                                               �֦���W��>��Pbandit12@bandit:/tmp/b13$ bzip2 --decompress data.bin.out
bzip2: Can't guess original name for data.bin.out -- using data.bin.out.out
bzip2: data.bin.out is not a bzip2 file.
bandit12@bandit:/tmp/b13$ ls -l
total 8
-rw-rw-r-- 1 bandit12 bandit12  428 May 29 09:32 data.bin.out
-rw-r----- 1 bandit12 bandit12 2575 May 29 09:14 data.txt
bandit12@bandit:/tmp/b13$ gunzip data.bin.out
gzip: data.bin.out: unknown suffix -- ignored
bandit12@bandit:/tmp/b13$ ls -lrt
total 8
-rw-r----- 1 bandit12 bandit12 2575 May 29 09:14 data.txt
-rw-rw-r-- 1 bandit12 bandit12  428 May 29 09:32 data.bin.out
bandit12@bandit:/tmp/b13$ unzip
UnZip 6.00 of 20 April 2009, by Debian. Original by Info-ZIP.

Usage: unzip [-Z] [-opts[modifiers]] file[.zip] [list] [-x xlist] [-d exdir]
  Default action is to extract files in list, except those in xlist, to exdir;
  file[.zip] may be a wildcard.  -Z => ZipInfo mode ("unzip -Z" for usage).

  -p  extract files to pipe, no messages     -l  list files (short format)
  -f  freshen existing files, create none    -t  test compressed archive data
  -u  update files, create if necessary      -z  display archive comment only
  -v  list verbosely/show version info       -T  timestamp archive to latest
  -x  exclude files that follow (in xlist)   -d  extract files into exdir
modifiers:
  -n  never overwrite existing files         -q  quiet mode (-qq => quieter)
  -o  overwrite files WITHOUT prompting      -a  auto-convert any text files
  -j  junk paths (do not make directories)   -aa treat ALL files as text
  -U  use escapes for all non-ASCII Unicode  -UU ignore any Unicode fields
  -C  match filenames case-insensitively     -L  make (some) names lowercase
  -X  restore UID/GID info                   -V  retain VMS version numbers
  -K  keep setuid/setgid/tacky permissions   -M  pipe through "more" pager
  -O CHARSET  specify a character encoding for DOS, Windows and OS/2 archives
  -I CHARSET  specify a character encoding for UNIX and other archives

See "unzip -hh" or unzip.txt for more help.  Examples:
  unzip data1 -x joe   => extract all files except joe from zipfile data1.zip
  unzip -p foo | more  => send contents of foo.zip via pipe into program more
  unzip -fo foo ReadMe => quietly replace existing ReadMe if archive file newer
bandit12@bandit:/tmp/b13$ ls -lrt
total 8
-rw-r----- 1 bandit12 bandit12 2575 May 29 09:14 data.txt
-rw-rw-r-- 1 bandit12 bandit12  428 May 29 09:32 data.bin.out
bandit12@bandit:/tmp/b13$ unzip data.bin.out
Archive:  data.bin.out
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of data.bin.out or
        data.bin.out.zip, and cannot find data.bin.out.ZIP, period.
bandit12@bandit:/tmp/b13$ ls -l
total 8
-rw-rw-r-- 1 bandit12 bandit12  428 May 29 09:32 data.bin.out
-rw-r----- 1 bandit12 bandit12 2575 May 29 09:14 data.txt
bandit12@bandit:/tmp/b13$ xz --decompress data.bin.out
xz: data.bin.out: File format not recognized
bandit12@bandit:/tmp/b13$ gzip --list data.bin.out
         compressed        uncompressed  ratio uncompressed_name
                428               20480  98.0% data.bin.out
bandit12@bandit:/tmp/b13$ man gzip
bandit12@bandit:/tmp/b13$ gzip --stdout --decompress data.bin.out
data5.bin0000644000000000000000000002400015163755000011242 0ustar  rootrootdata6.bin00006440000000000000000000000331151637550000112���Ah�@���P��M5�*��x(���E']� )@������j@�}�� [#�t!�@f �
�}�X�a��/�VY~障�*��R�J�o��{�^�$'��W&�D� �I�9BY
                                              �Ԁ�j����U%JQ�`��rE8P��VI]bandit12@bandit:/tmp/b13$ 
bandit12@bandit:/tmp/b13$ 
bandit12@bandit:/tmp/b13$ 
bandit12@bandit:/tmp/b13$ 
bandit12@bandit:/tmp/b13$ cp data.bin.out data.bin.gz
bandit12@bandit:/tmp/b13$ gzip --decompress data.bin.gz
bandit12@bandit:/tmp/b13$ ls -al
total 12020
drwxrwxr-x    2 bandit12 bandit12     4096 May 29 09:48 .
drwxrwx-wt 2576 root     root     12271616 May 29 09:48 ..
-rw-rw-r--    1 bandit12 bandit12    20480 May 29 09:48 data.bin
-rw-rw-r--    1 bandit12 bandit12      428 May 29 09:32 data.bin.out
-rw-r-----    1 bandit12 bandit12     2575 May 29 09:14 data.txt
bandit12@bandit:/tmp/b13$ cat data.bin
data5.bin0000644000000000000000000002400015163755000011242 0ustar  rootrootdata6.bin00006440000000000000000000000331151637550000112���Ah�@���P��M5�*��x(���E']� )@������j@�}�� [#�t!�@f �
�}�X�a��/�VY~障�*��R�J�o��{�^�$'��W&�D� �I�9BY
                                              �Ԁ�j����U%JQ�`��rE8P��VI]bandit12@bandit:/tmp/b13$ 
bandit12@bandit:/tmp/b13$ 
bandit12@bandit:/tmp/b13$ 
bandit12@bandit:/tmp/b13$ 
bandit12@bandit:/tmp/b13$ gzip --list data.bin

gzip: data.bin: not in gzip format
bandit12@bandit:/tmp/b13$ man zip
bandit12@bandit:/tmp/b13$ unzip data.bin
Archive:  data.bin
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of data.bin or
        data.bin.zip, and cannot find data.bin.ZIP, period.
bandit12@bandit:/tmp/b13$ man xz
bandit12@bandit:/tmp/b13$ unxz data.bin
unxz: data.bin: File format not recognized
bandit12@bandit:/tmp/b13$ cp data.bin data.bin.tar
bandit12@bandit:/tmp/b13$ tar xvf data.bin.tar
data5.bin
bandit12@bandit:/tmp/b13$ ls -al
total 12052
drwxrwxr-x    2 bandit12 bandit12     4096 May 29 09:54 .
drwxrwx-wt 2580 root     root     12271616 May 29 09:54 ..
-rw-r--r--    1 bandit12 bandit12    10240 Apr  3 15:17 data5.bin
-rw-rw-r--    1 bandit12 bandit12    20480 May 29 09:48 data.bin
-rw-rw-r--    1 bandit12 bandit12      428 May 29 09:32 data.bin.out
-rw-rw-r--    1 bandit12 bandit12    20480 May 29 09:54 data.bin.tar
-rw-r-----    1 bandit12 bandit12     2575 May 29 09:14 data.txt
bandit12@bandit:/tmp/b13$ cat data5.bin 
���Ah�@���P��M5�*��x(���E']� )@��0000033115163755000011244 0ustar  rootrootBZh91AY&SY�VI]����j@�}�� [#�t!�@f �
�}�X�a��/�VY~障�*��R�J�o��{�^�$'��W&�D� �I�9BY
                                              �Ԁ�j����U%JQ�`��rE8P��VI]bandit12@bandit:/tmp/b13$ cp data5.bin data5.bin.tar
bandit12@bandit:/tmp/b13$ tar xvf data5.bin.tar
data6.bin
bandit12@bandit:/tmp/b13$ ls -lrt
total 76
-rw-r--r-- 1 bandit12 bandit12   217 Apr  3 15:17 data6.bin
-rw-r--r-- 1 bandit12 bandit12 10240 Apr  3 15:17 data5.bin
-rw-r----- 1 bandit12 bandit12  2575 May 29 09:14 data.txt
-rw-rw-r-- 1 bandit12 bandit12   428 May 29 09:32 data.bin.out
-rw-rw-r-- 1 bandit12 bandit12 20480 May 29 09:48 data.bin
-rw-rw-r-- 1 bandit12 bandit12 20480 May 29 09:54 data.bin.tar
-rw-r--r-- 1 bandit12 bandit12 10240 May 29 09:55 data5.bin.tar
bandit12@bandit:/tmp/b13$ cat data6.bin
���Ah�@���P��M5�*��x(���E']� )@�� �
�}�X�a��/�VY~障�*��R�J�o��{�^�$'��W&�D� �I�9BY
                                              �Ԁ�j����U%JQ�`��rE8P��VI]bandit12@bandit:/tmp/b13$ 
bandit12@bandit:/tmp/b13$ 
bandit12@bandit:/tmp/b13$ file data6.bin
data6.bin: bzip2 compressed data, block size = 900k
bandit12@bandit:/tmp/b13$ bzip2 --decompress data6.bin
bzip2: Can't guess original name for data6.bin -- using data6.bin.out
bandit12@bandit:/tmp/b13$ ls -lrt
total 84
-rw-r--r-- 1 bandit12 bandit12 10240 Apr  3 15:17 data6.bin.out
-rw-r--r-- 1 bandit12 bandit12 10240 Apr  3 15:17 data5.bin
-rw-r----- 1 bandit12 bandit12  2575 May 29 09:14 data.txt
-rw-rw-r-- 1 bandit12 bandit12   428 May 29 09:32 data.bin.out
-rw-rw-r-- 1 bandit12 bandit12 20480 May 29 09:48 data.bin
-rw-rw-r-- 1 bandit12 bandit12 20480 May 29 09:54 data.bin.tar
-rw-r--r-- 1 bandit12 bandit12 10240 May 29 09:55 data5.bin.tar
bandit12@bandit:/tmp/b13$ cat data6.bin.out
data8.bin0000644000000000000000000000011715163755000011250 0ustar  rootroo��idata9.bin
�.6*K   q)w��>�2A1bandit12@bandit:/tmp/b13$ file data6.bin.out                        �HU(H,..�/JQ�,Vp�7M)w+N6HNJ���0Ȱ�2J
data6.bin.out: POSIX tar archive (GNU)
bandit12@bandit:/tmp/b13$ cp data6.bin.out data6.bin.tar
bandit12@bandit:/tmp/b13$ tar xvf data6.bin.tar
data8.bin
bandit12@bandit:/tmp/b13$ file data8.bin
data8.bin: gzip compressed data, was "data9.bin", last modified: Fri Apr  3 15:17:20 2026, max compression, from Unix, original size modulo 2^32 49
bandit12@bandit:/tmp/b13$ cp data8.bin data8.bin.gz
bandit12@bandit:/tmp/b13$ gunzip data8.bin.gz
gzip: data8.bin already exists; do you wish to overwrite (y or n)? n
        not overwritten
bandit12@bandit:/tmp/b13$ gunzip data8.bin.gz
gzip: data8.bin already exists; do you wish to overwrite (y or n)? y
bandit12@bandit:/tmp/b13$ ls -lrt
total 100
-rw-r--r-- 1 bandit12 bandit12 10240 Apr  3 15:17 data6.bin.out
-rw-r--r-- 1 bandit12 bandit12 10240 Apr  3 15:17 data5.bin
-rw-r----- 1 bandit12 bandit12  2575 May 29 09:14 data.txt
-rw-rw-r-- 1 bandit12 bandit12   428 May 29 09:32 data.bin.out
-rw-rw-r-- 1 bandit12 bandit12 20480 May 29 09:48 data.bin
-rw-rw-r-- 1 bandit12 bandit12 20480 May 29 09:54 data.bin.tar
-rw-r--r-- 1 bandit12 bandit12 10240 May 29 09:55 data5.bin.tar
-rw-r--r-- 1 bandit12 bandit12 10240 May 29 09:57 data6.bin.tar
-rw-r--r-- 1 bandit12 bandit12    49 May 29 09:58 data8.bin
bandit12@bandit:/tmp/b13$ cat data8.bin
The password is FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn