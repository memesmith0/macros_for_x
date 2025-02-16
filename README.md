#!/usr/bin/sh
#Copyright (C) 2025 by john morris beck <john.morris.beck@hotmail.com>
#
#Permission to use, copy, modify, and/or distribute this software for any purpose with or without fee is hereby granted.
#
#THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES WITH REGARD TO THIS SOFTWARE INCLUDING ALL
#
#IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR ANY SPECIAL, DIRECT, INDIRECT, OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES WHATSOEVER
#A
#RESULTING FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF OR IN CONNECTION WITH THE USE OR PERFORMANCE OF
#
#THIS SOFTWARE.

##create a new directory
#$mkdir mcr14_your_langauge_name

##go to that directory
#$cd mcr14_your_language_name

##get this file
#$wget https://raw.githubusercontent.com/memesmith0/macros_for_x/refs/heads/main/README.md

##rename it mcr14_you_language_name.sh
#$cp README.md mcr14_your_language_name.sh

##mark it as executable
#$chmod +x mcr14_your_language_name.sh

##edit this file in places where it says to edit it particularly the variable named interpreter if your language is interpreted

##if the langauge is compiled run this command
#$./mcr14_my_language_name.sh < my_source_file_name.txt #your filename might not end with .txt

##if your langauge is interpreted run this command
#$./mcr14_my_language_name.sh

#or

##get this file
#$wget 
##rename it mcr5_my_language_name.sh
#$mv old_name.sh new_name.sh

##make the language runnnable
#$chmod +x mcr5_my_language_name.sh

##apply macros to code
#$cat x_source.x | mcr5_my_language_name.sh


#this code implements the core of the macro system
#if "m" is a command in x change that string to something unique that is not planned to go into the grammar of x
anymcr(){ if [ "$2" = "" ] ;then sh -c "$1"|sh -c "$1";else sh -c "$1"|sh -c "$1"|sh -c "$2">&2; fi;};mcr14(){ (a="(unset c f;while read -r i;do if [ \"\$i\" = m ] ;then read -r i;c=\"\$c\$i\";read -r i;f=\"\$f\$i\";else echo \"\$i\"|awk \"\$f{o=\\\$0;\$c print o}\"||exit;fi;done;)";if [ "$2" = "" ] ;then if  [ "$1" = "" ] ;then anymcr "$a"; else anymcr "$1"; fi; elif [ "$1" = "" ] ; then anymcr "$a" "$2"; else anymcr "$1" "$2"; fi;)};mcr14sh(){ mcr14 "" "sh";};

macro_system="" #if you want a custom macro system change macro_system to a shell command that runs that macro system
interpreter="" #if you want an interpreter change interpreter to be a shell command that runs your interpreter. if your language is compiled leave this empty
               #if you want the shell as an additional layer to the macros change the interpreter string to "sh"

#this is the code that will allow you to turn your language into a macro language
mcr14_your_langauge_name(){ mcr14 "$macro_system" "$interpreter"; } #change _x to be the name of your language.


#some x code;
#some x code;
#some x code;
#m
#an awk function in one line
#this line of awk goes into END
#more x code. now a new macro is applied to each line.
#more macro code in x
#more macro code in x
#//macros are recursive by one additional layer
