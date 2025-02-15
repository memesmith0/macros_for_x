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

#get this file
##rename it mcr5_my_language_name_interpreter.sh
#$mv old_name.sh new_name.sh
#$chmod +x mcr5_my_language_name_inteprreter.sh
#$mcr5_my_language_name_interpreter "command_to_run_my_languages_interpeter"

#or

##get this file
#$wget 
##rename it mcr5_my_language_name.sh
#$mv old_name.sh new_name.sh

##make the language runnnable
#$chmod +x mcr5_my_language_name.sh

##apply macros to code
#$cat x_source.x | mcr5_my_language_name.sh



#if "~" is a command in x change that string to something unique that is not planned to go into the grammar of x
mcr5(){ (m(){ (unset f l c;while read -r l;do if [ "~" = "$l" ] ;then read -r l;c="$c$l";read -r l;f="$f$l";else echo "$l"|awk "$f{l=\$0}END{$c print l}"||exit;fi;done);};m|m)};
mcr5_x{ mcr5; } #nothing special needs to be changed about mcr5 to make it compatible with x
mcr5_x_interpreter(){ mcr5_x | sh -c "$1" >&2;}; #"$1" must be an interpreter for x
mcr5_x_interpeter "$1"; # if this doesnt work comment out the line and uncomment the next line
#mcr5_x #you are meant to send your source code for x including the inline macros into stdin

#some x code;
#some x code;
#some x code;
#~
#an awk function in one line
#this line of awk goes into END
#more x code. now a new macro is applied to each line.
#more macro code in x
#more macro code in x
#//macros are recursive by one additional layer
