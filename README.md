# make-bookmarklet-notepad
Macro for Notepad++ to convert javascript into Bookmarklet

After researching best way to convert javascript to bookmarklet that works with modern browsers I collated and tested several regex replacements that can be recorded as Notepad++ macro in that sequence.

|Seq.|Find What:|Replace With:|Description|
|---|---|---|---|
|1|`(/\*([^*]\|[\r\n]\|(\*+([^*/]\|[\r\n])))*\*+/)\|(//.*)`|`<empty>`|Remove comments|
|2|`\s*\n\s*`|`\n`|Condense spaces|
|3|`\h+`|`<space>`|Condense spaces|
|4|`\h([^A-Za-z0-9\_\$])`|`$1`|Replace unnecessary horizontal spaces around non variables|
|5|`([^[Z-Za-z0-9\_\$])\h`|`$1`|Replace unnecessary horizontal spaces around non variables|
|6|`\s?([\(\[{])\s?`|`$1`|Replace unnecessary spaces around brackets and parantheses|
|7|`\s([\)\]}])`|`$1`|Replace unnecessary spaces around brackets and parantheses|
|8|`\s?([\.=:\-+,])\s?`|`$1`|Replace unnecessary spaces around operators|
|9|`;\n`|`;`|Replace unnecessary new lines after semicolon|
|10|`;}`|`}`|Replace unnecessary selicolons|
|11|`^\s+\|\R\s*`|`<empty>`|Remove rest of new lines|
|12|`%`|`%25`|Html encode special chars|
|13|`&`|`%26`|Html encode special chars|
|14|`<`|`%3C`|Html encode special chars|
|15|`>`|`%3E`|Html encode special chars|
|16|`#`|`%23`|Html encode special chars|
|17|`"`|`%22`|Html encode special chars|
|18|`'`|`%27`|Html encode special chars|
|19|`\s`|`%20`|Html encode special chars|
|20|`^(.*)$`|`javascript:$1`|Prepend javascript protocol|

If you don't fancy recording macro yourself you can merge code in shortcuts.xml with your shortcuts.xml file that normally is located in %APPDATA%/Notepad++ folder.
Threre are some edge usecases  this macro does not cover but should be good for majority of conversions.
