###########################################################################
##                                                                       ##
##                  Language Technologies Institute                      ##
##                     Carnegie Mellon University                        ##
##                         Copyright (c) 2014                            ##
##                        All Rights Reserved.                           ##
##                                                                       ##
##  Permission is hereby granted, free of charge, to use and distribute  ##
##  this software and its documentation without restriction, including   ##
##  without limitation the rights to use, copy, modify, merge, publish,  ##
##  distribute, sublicense, and/or sell copies of this work, and to      ##
##  permit persons to whom this work is furnished to do so, subject to   ##
##  the following conditions:                                            ##
##   1. The code must retain the above copyright notice, this list of    ##
##      conditions and the following disclaimer.                         ##
##   2. Any modifications must be clearly marked as such.                ##
##   3. Original authors' names are not deleted.                         ##
##   4. The authors' names are not used to endorse or promote products   ##
##      derived from this software without specific prior written        ##
##      permission.                                                      ##
##                                                                       ##
##  CARNEGIE MELLON UNIVERSITY AND THE CONTRIBUTORS TO THIS WORK         ##
##  DISCLAIM ALL WARRANTIES WITH REGARD TO THIS SOFTWARE, INCLUDING      ##
##  ALL IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS, IN NO EVENT   ##
##  SHALL CARNEGIE MELLON UNIVERSITY NOR THE CONTRIBUTORS BE LIABLE      ##
##  FOR ANY SPECIAL, INDIRECT OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES    ##
##  WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN   ##
##  AN ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION,          ##
##  ARISING OUT OF OR IN CONNECTION WITH THE USE OR PERFORMANCE OF       ##
##  THIS SOFTWARE.                                                       ##
##                                                                       ##
###########################################################################
##                                                                       ##
##  GCW-Zero: Open Source Gaming console                                 ##
##  http://www.gcw-zero.com/                                             ##
##                                                                       ## 
##  The core files for making a Bard.opk, and commands to build it       ##
##                                                                       ## 
##  This is set up for my particular installation, you'll need to edit   ##
##  some of the pathnames for your machine                               ## 
##                                                                       ## 
###########################################################################
TOP=..
DIRNAME=gcw0
BUILD_DIRS = 
ALL_DIRS = 
OTHERS = Bard_Help.html default.gcw0.desktop bard.sh \
         gcw0.COPYING
FILES = Makefile $(OTHERS)

ALL = opk

include $(TOP)/config/common_make_rules

opk: 
	rm -rf Bard
	mkdir -p Bard/voices
#       The following line is specific to awb's gcw0/host set up
	cp -pr ${FLITEDIR}/voices/*.flitevox Bard/voices
#       Create an empty file to identify the kal voice
	touch Bard/voices/kal.flitevox
	cp -pr bard.sh Bard/bard.sh
	cp -pr /usr/share/fonts/truetype/liberation/LiberationSerif-Regular.ttf Bard/LiberationSerif-Regular.ttf
	cp -pr default.gcw0.desktop Bard/default.gcw0.desktop
	cp -pr Bard_Help.html Bard/Bard_Help.html
	sed 's/<[^>]*>//g' Bard_Help.html >Bard/readme.txt
	cat ${TOP}/README >>Bard/readme.txt
	cat ${TOP}/COPYING >>Bard/readme.txt
	cat gcw0.COPYING >>Bard/readme.txt
	cp -pr ${TOP}/Bard32.png Bard/Bard32.png
	cp -pr ${TOP}/build/mipsel-linux-uclibc/bin/bard Bard/bard
	${GCW0TOOLCGHAIN}/usr/bin/mksquashfs Bard Bard_${PROJECT_VERSION}.opk -all-root -noappend -no-exports -no-xattrs

