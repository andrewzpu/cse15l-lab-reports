# **Lab Report 3**

## Grep Command
The grep command is used to look for a certain String inside the contents of a file
The default format is as follows:
```
grep [String] [Filename]
```
Here is what it looks like when the default grep command is run with no options:
```
$ grep "Israel is a" written_2/travel_guides/berlitz1/*.txt
written_2/travel_guides/berlitz1/WhatToIsrael.txt:        Shopping in Israel is as exotic or as straightforward as you
written_2/travel_guides/berlitz1/WhereToIsrael.txt:        Israel is a small country, measuring just 445 km (260 miles)

$ grep "Lucayans" written_2/travel_guides/berlitz2/*.txt
written_2/travel_guides/berlitz2/Bahamas-History.txt:Centuries before the arrival of Columbus, a peaceful Amerindian people who called themselves the Luccucairi had settled in the Bahamas. Originally from South America, they had traveled up through the Caribbean islands, surviving by cultivating modest crops and from what they caught from sea and shore. Nothing in the experience of these gentle people could have prepared them for the arrival of the Pinta, the Niña, and the Santa Maria at San Salvador on 12 October 1492. Columbus believed that he had reached the East Indies and mistakenly called these people Indians. We know them today as the Lucayans. Columbus claimed the island and others in the Bahamas for his royal Spanish patrons, but not finding the gold and other riches he was seeking, he stayed for only two weeks before sailing towards Cuba.
written_2/travel_guides/berlitz2/Bahamas-History.txt:The Spaniards never bothered to settle in the Bahamas, but the number of shipwrecks attest that their galleons frequently passed through the archipelago en route to and from the Caribbean, Florida, Bermuda, and their home ports. On Eleuthera the explorers dug a fresh-water well — at a spot now known as “Spanish Wells” — which was used to replenish the supplies of water on their ships before they began the long journey back to Europe with their cargoes of South American gold. As for the Lucayans, within 25 years all of them, perhaps some 30,000 people, were removed from the Bahamas to work — and die — in Spanish gold mines and on farms and pearl fisheries on Hispaniola (Haiti), Cuba, and elsewhere in the Caribbean
```
In each location where the String pattern is found, the grep command prints the file it was found in, followed by the text that contains the String

## -l option
[Info from grep man page](https://linuxcommand.org/lc3_man_pages/grep1.html)

The -l option lists all the files that the String was found in and does not include the actual text
```
grep -l [String] [Filename]
```
Here are the commands we ran before but with the -l option
```
$ grep -l "Israel is a" written_2/travel_guides/berlitz1/*.txt
written_2/travel_guides/berlitz1/WhatToIsrael.txt
written_2/travel_guides/berlitz1/WhereToIsrael.txt

$ grep -l "Lucayans" written_2/travel_guides/berlitz2/*.txt
written_2/travel_guides/berlitz2/Bahamas-History.txt
```
As you can see, the same files are returned as the default grep we ran earlier, but the excess text after the file path are removed

## -f option
[Info from grep man page](https://linuxcommand.org/lc3_man_pages/grep1.html)

The -f option allows us to input a file, and the contents of the file are used as the String pattern
```
grep -f [Pattern File] [File to Search]
```
In the following code, we input the String pattern into a file before using the -f option to search
```
$ echo "Israel is a" > GrepTest1.txt

$ echo "Lucayans" > GrepTest2.txt

$ grep -f GrepTest1.txt written_2/travel_guides/berlitz1/*.txt
written_2/travel_guides/berlitz1/WhatToIsrael.txt:        Shopping in Israel is as exotic or as straightforward as you
written_2/travel_guides/berlitz1/WhereToIsrael.txt:        Israel is a small country, measuring just 445 km (260 miles)

$grep -f GrepTest2.txt written_2/travel_guides/berlitz2/*.txt
written_2/travel_guides/berlitz2/Bahamas-History.txt:Centuries before the arrival of Columbus, a peaceful Amerindian people who called themselves the Luccucairi had settled in the Bahamas. Originally from South America, they had traveled up through the Caribbean islands, surviving by cultivating modest crops and from what they caught from sea and shore. Nothing in the experience of these gentle people could have prepared them for the arrival of the Pinta, the Niña, and the Santa Maria at San Salvador on 12 October 1492. Columbus believed that he had reached the East Indies and mistakenly called these people Indians. We know them today as the Lucayans. Columbus claimed the island and others in the Bahamas for his royal Spanish patrons, but not finding the gold and other riches he was seeking, he stayed for only two weeks before sailing towards Cuba.
written_2/travel_guides/berlitz2/Bahamas-History.txt:The Spaniards never bothered to settle in the Bahamas, but the number of shipwrecks attest that their galleons frequently passed through the archipelago en route to and from the Caribbean, Florida, Bermuda, and their home ports. On Eleuthera the explorers dug a fresh-water well — at a spot now known as “Spanish Wells” — which was used to replenish the supplies of water on their ships before they began the long journey back to Europe with their cargoes of South American gold. As for the Lucayans, within 25 years all of them, perhaps some 30,000 people, were removed from the Bahamas to work — and die — in Spanish gold mines and on farms and pearl fisheries on Hispaniola (Haiti), Cuba, and elsewhere in the Caribbean
```
Here, the output is exactly the same as the original commands we ran. The only difference is that we input a file as the String pattern.

## -r option
[Info from grep man page](https://linuxcommand.org/lc3_man_pages/grep1.html)

The -r option reads for the String pattern recursively through all the files in a directory
```
grep -r [String] [Directory]
```
In the following code, we use the -r option and remove the "\*.txt" from the end of the file path. This command uses a directory as input instead of a file, and it will look through the entire directory.
```
$ grep -r "Israel is a" written_2/travel_guides/berlitz1
written_2/travel_guides/berlitz1/WhatToIsrael.txt:        Shopping in Israel is as exotic or as straightforward as you
written_2/travel_guides/berlitz1/WhereToIsrael.txt:        Israel is a small country, measuring just 445 km (260 miles)

$ grep -r "Lucayans" written_2/travel_guides/berlitz2
written_2/travel_guides/berlitz2/Bahamas-History.txt:Centuries before the arrival of Columbus, a peaceful Amerindian people who called themselves the Luccucairi had settled in the Bahamas. Originally from South America, they had traveled up through the Caribbean islands, surviving by cultivating modest crops and from what they caught from sea and shore. Nothing in the experience of these gentle people could have prepared them for the arrival of the Pinta, the Niña, and the Santa Maria at San Salvador on 12 October 1492. Columbus believed that he had reached the East Indies and mistakenly called these people Indians. We know them today as the Lucayans. Columbus claimed the island and others in the Bahamas for his royal Spanish patrons, but not finding the gold and other riches he was seeking, he stayed for only two weeks before sailing towards Cuba.
written_2/travel_guides/berlitz2/Bahamas-History.txt:The Spaniards never bothered to settle in the Bahamas, but the number of shipwrecks attest that their galleons frequently passed through the archipelago en route to and from the Caribbean, Florida, Bermuda, and their home ports. On Eleuthera the explorers dug a fresh-water well — at a spot now known as “Spanish Wells” — which was used to replenish the supplies of water on their ships before they began the long journey back to Europe with their cargoes of South American gold. As for the Lucayans, within 25 years all of them, perhaps some 30,000 people, were removed from the Bahamas to work — and die — in Spanish gold mines and on farms and pearl fisheries on Hispaniola (Haiti), Cuba, and elsewhere in the Caribbean
```
As you can see, the output is exactly the same since we looked through the same directory.

## -i option
[Info from grep man page](https://linuxcommand.org/lc3_man_pages/grep1.html)

The -i option means that the command will ignore the case of the characters
```
grep -i [Non-Case-Sensitive String] [Filename]
```
In the following code, we ran the original commands with the -i option. In the String pattern, we input the same pattern but in all lowercase.
```
$ grep -i "Israel is a" written_2/travel_guides/berlitz1/*.txt

$ grep -i "israel is a" written_2/travel_guides/berlitz1/*.txt
written_2/travel_guides/berlitz1/WhatToIsrael.txt:        Shopping in Israel is as exotic or as straightforward as you
written_2/travel_guides/berlitz1/WhereToIsrael.txt:        Israel is a small country, measuring just 445 km (260 miles)

$ grep -i "lucayans" written_2/travel_guides/berlitz2/*.txt
written_2/travel_guides/berlitz2/Bahamas-History.txt:Centuries before the arrival of Columbus, a peaceful Amerindian people who called themselves the Luccucairi had settled in the Bahamas. Originally from South America, they had traveled up through the Caribbean islands, surviving by cultivating modest crops and from what they caught from sea and shore. Nothing in the experience of these gentle people could have prepared them for the arrival of the Pinta, the Niña, and the Santa Maria at San Salvador on 12 October 1492. Columbus believed that he had reached the East Indies and mistakenly called these people Indians. We know them today as the Lucayans. Columbus claimed the island and others in the Bahamas for his royal Spanish patrons, but not finding the gold and other riches he was seeking, he stayed for only two weeks before sailing towards Cuba.
written_2/travel_guides/berlitz2/Bahamas-History.txt:The Spaniards never bothered to settle in the Bahamas, but the number of shipwrecks attest that their galleons frequently passed through the archipelago en route to and from the Caribbean, Florida, Bermuda, and their home ports. On Eleuthera the explorers dug a fresh-water well — at a spot now known as “Spanish Wells” — which was used to replenish the supplies of water on their ships before they began the long journey back to Europe with their cargoes of South American gold. As for the Lucayans, within 25 years all of them, perhaps some 30,000 people, were removed from the Bahamas to work — and die — in Spanish gold mines and on farms and pearl fisheries on Hispaniola (Haiti), Cuba, and elsewhere in the Caribbean
```
As you can see, when we run the command without the -i option, nothing returns because the String pattern doesn't match. When we add the -i, the case doesn't matter and the pattern "lucayans" can match with "Lucayans."



