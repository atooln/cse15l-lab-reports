# Lab Report 5 (Lab Report 3 Redo)
In lab 3, I explored the ``find`` command. This time I will be exploring the ``grep`` command. 

## Option 1: -r (recursive search)
This option allows you to search for patterns recursively in all subdirectories of a directory. This can be useful when you have a large directory tree with many subdirectories.

#### Example 1: Search for the word "computer" in all files and subdirectories under ./written_2
```
> grep -r "computer" ./written_2

./written_2/non-fiction/OUP/Berk/CH4.txt:Of course, preschoolers—even those as young as age 3—beneﬁt from experience with computers as long as activities are constructive, adults are available to support them, and children are not diverted from other worthwhile activities. But in homes in which family members are preoccupied with the computer, especially the Internet, time spent communicating and enjoying joint leisure activities declines.95 Therefore, the computer’s value for acquiring new skills and information must be weighed against its potential for detracting from adult–child dialogues and other family activities.
...
```
#### Example 2: Search for lines that match the regular expression "^[A-Z]" (lines that start with a capital letter) in all files and subdirectories under ./written_2
 
``` 
> grep -r "^[A-Z]" ./written_2

./written_2/travel_guides/berlitz2/Portugal-WhatToDo.txt:September
./written_2/travel_guides/berlitz2/Portugal-WhatToDo.txt:Lamego: Festivities honoring Nossa Senhora dos Remédios (annual pilgrimage to famous Baroque shrine, along with torchlight procession, folklore festival, fairs, and fireworks, culminating with triumphal procession). (6–9 Sept)
./written_2/travel_guides/berlitz2/Portugal-WhatToDo.txt:Nazaré: Our Lady of Nazaré (Nossa Senhora da Nazaré): fishermen carry an image of the town’s patron saint on their shoulders in festive processions; also bullfights, fairs, concerts, folk dancing, and singing. (2nd week Sept).
./written_2/travel_guides/berlitz2/Portugal-WhatToDo.txt:October
./written_2/travel_guides/berlitz2/Portugal-WhatToDo.txt:Fátima: Last Pilgrimage of year to shrine (pilgrims celebrate the last apparition of the Virgin to shepherds on 12 October 1917) (12–13 October)
./written_2/travel_guides/berlitz2/Portugal-WhatToDo.txt:Vila Franca de Xira: October Fair: ancient fair that includes bull running, fair, and bullfights (first two weeks).
...
```
Source: [Linux grep command](https://www.computerhope.com/unix/ugrep.htm)

## Option 2: -n (line numbers)
This option displays the line numbers of the matching lines in the output.

#### Example 1: Search for the word "the" in ch2.txt in the directory ./written_2/non-fiction/OUP/Abernathy and display the line numbers
 
```
> grep -n "the" ./written_2/non-fiction/OUP/Abernathy/ch2.txt

5:The emergence of textile, apparel, and retail enterprises in the United States is full of fascinating twists. In 1790, for instance, an act of industrial espionage is said to have launched the domestic textile industry, if not American manufacturing in general. At that time, Samuel Slater, a skilled mechanic, built the first successful water-powered yarn spinning mill in Pawtucket, Rhode Island. Yarn was in short supply in the new country and much in demand in households that did hand weaving as well as in workplaces with looms that produced sheeting, shirting, and stockings for commerce. Some of the American states and improvement societies had even offered generous rewards for the establishment of water-powered combing and spinning, especially those based on state-of-the-art English Arkwright operations. But British law strictly prohibited the export of drawings, plans, or models of these new technologies. It took somebody like Slater—an indentured apprentice for over six years at the Arkwright and Strut’s plant in Milford, England—to ferry the plans to America.1
6:Slater was interested in the financial rewards to be had in the new world while still in England. Mindful of British prohibitions, he
...
```

#### Example 2: Search for lines that match the regular expression "^Chapter" (lines that start with the word "Chapter") in all files under ./written_2
 
``` 
> grep -nr "^Chapter" ./written_2

./written_2/non-fiction/OUP/Kauffman/ch3.txt:5:Chapter 3
./written_2/non-fiction/OUP/Kauffman/ch4.txt:5:Chapter 4
./written_2/non-fiction/OUP/Kauffman/ch5.txt:5:Chapter 5
./written_2/non-fiction/OUP/Kauffman/ch7.txt:5:Chapter 7
./written_2/non-fiction/OUP/Kauffman/ch6.txt:5:Chapter 6
./written_2/non-fiction/OUP/Kauffman/ch8.txt:5:Chapter 8
./written_2/non-fiction/OUP/Kauffman/ch9.txt:5:Chapter 9
./written_2/non-fiction/OUP/Kauffman/ch10.txt:5:Chapter 10
```

Source: [The GNU grep manual](https://www.gnu.org/software/grep/manual/grep.html)

## Option 3: -v (invert match)
This option displays all lines that do not match the pattern. It can be useful when you want to exclude certain lines from the output.

#### Example 1: Search for lines that do not contain the word "textile" in ch2.txt in the directory ./written_2/non-fiction/OUP/Abernathy
 
``` 
> grep -v "textile" ./written_2/non-fiction/OUP/Abernathy/ch2.txt

Slater was interested in the financial rewards to be had in the new world while still in England. Mindful of British prohibitions, he committed to memory the design and construction of the spinning mill where he worked. Arriving in New York in late 1789, he was referred to Moses Brown in Providence, a prominent merchant who had established a company, Almy and Brown, to develop “frame or water spinning.” Brown responded on December 10, 1789, to Slater’s initial inquiry, saying Almy and Brown certainly wanted the assistance of a person with Slater’s skills because an experimental mill had failed, “no persons being acquainted with the business, and the frames imperfect.”2
Once in Almy and Brown’s Pawtucket plant, Slater found the existing machinery totally unsatisfactory. He entered into a partnership with Almy and Brown to erect “perpetual card and spinning” machines, otherwise known as the Arkwright patents. By 1793, the firm of Almy, Brown and Slater was operating a seventy-two-spindle mill, producing high-quality yarn. From the Pawtucket mill, the American cotton-spinning industry was launched.
...
```

#### Example 2: Search for lines that do not match the regular expression "^Chapter" (lines that do not start with the word "Chapter") in all files under ./written_2
 
```
> grep -vnr "^Chapter" ./written_2

./written_2/travel_guides/berlitz2/Bahamas-WhatToDo.txt:8:Crafts. Bahamians have always had to fend for themselves, and this resourcefulness has led them to become proficient at a number of practical handicrafts, many of which make beautiful souvenirs. Straw goods are the most ubiquitous. The Seminole Indians of Red Bay on Andros are said to produce the finest work on the Bahamas, though each island has its own individual patterns and differences in style. It is still possible to watch the women at work on the islands of Andros and at George Town on Exuma. Straw work can be bought from small workshops in people’s homes or from the better quality straw vendors in Nassau. Prices can be high, but even small bowls make beautiful and practical reminders of your trip. The handmade pieces are likely to become rare within a couple of generations, because so few young Bahamian women are now taking up the craft. Be aware that much of the straw work, particularly the mass-market goods like hats and bags, is not made in the Bahamas but in Taiwan and China. If you want to be sure of getting genuine Bahamian straw work, buy from places such as The Plait Lady, who has a shop on Bay Street in Nassau; you’ll have to pay a little more but you’ll be sure you’re getting an authentic handmade work of art.
...
```

Source: [Linux grep command](https://www.computerhope.com/unix/ugrep.htm)

## Option 4: -i (case-insensitive search)
This option allows you to search for patterns regardless of case. It can be useful when you are not sure about the case of the pattern.

#### Example 1: Search for the word "textile" in ch2.txt in the directory ./written_2/non-fiction/OUP/Abernathy, ignoring case
 
``` 
> grep -i "textile" ./written_2/non-fiction/OUP/Abernathy/ch2.txt

The emergence of textile, apparel, and retail enterprises in the United States is full of fascinating twists. In 1790, for instance, an act of industrial espionage is said to have launched the domestic textile industry, if not American manufacturing in general. At that time, Samuel Slater, a skilled mechanic, built the first successful water-powered yarn spinning mill in Pawtucket, Rhode Island. Yarn was in short supply in the new country and much in demand in households that did hand weaving as well as in workplaces with looms that produced sheeting, shirting, and stockings for commerce. Some of the American states and improvement societies had even offered generous rewards for the establishment of water-powered combing and spinning, especially those based on state-of-the-art English Arkwright operations. But British law strictly prohibited the export of drawings, plans, or models of these new technologies. It took somebody like Slater—an indentured apprentice for over six years at the Arkwright and Strut’s plant in Milford, England—to ferry the plans to America.1
...
```

#### Example 2: Search for lines that match the regular expression "^[aeiou]" (lines that start with a vowel) in all files under ./written_2, ignoring case
 
``` 
> grep -inr "^[aeiou]" ./written_2

ould economic theory proceed?
./written_2/non-fiction/OUP/Kauffman/ch9.txt:47:I suspect that there may be a natural extension to rational expectations applicable to human and any strategic agents, and I report a body of work suggested by me but largely carried out by Vince Darley at Harvard for his doctoral thesis. Two virtues of our eorts are to find a natural bound to infinite rationality and a natural sense of satisficing.
...
```
Source: [Linux grep command](https://www.computerhope.com/unix/ugrep.htm)