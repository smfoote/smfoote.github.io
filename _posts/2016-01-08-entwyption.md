---
layout: post
title: "Entwyption"
tags: 52articles ideas technology cryptography
comments: true
---

![The Beale Ciphers]({{site.url}}/assets/Beale_Papers.png)

Around the time I started to learn how to program, I happened to read an excellent book about cryptography called [The Code Book](http://www.amazon.com/Code-Book-Science-Secrecy-Cryptography/dp/0385495323). I learned more about the history (and future) of computer science book than from any other single source I have come across, and yet the book is still a fascinating, entertaining read. Within its pages I discovered the stories of Charles Babbage, Alan Turing, and the creators of public/private key encryption. While all these stories about computers and their creators had a strong hold on my attention<sup><a href="#note-1">[1]</a></sup>, the story of the Beale Papers captured my imagination.

## The Beale Papers

A true<sup><a href="#note-2">[2]</a></sup> American story of hidden treasure, complete with an encrypted treasure map. In 1817, Thomas Beale and some of his companions went on a hunting expedition for buffalo in the wild west, near Santa Fe, New Mexico. In January 1820, Beale spent a few months at the Washington Hotel in Lynchburg, Virginia, where he met the hotel's owner, Robert Morriss. After his stay in Lynchburg, Beale returned to New Mexico for another 2 years. He returned to Lynchburg in 1822, where he delivered a locked iron box to Robert Morriss for safe keeping. A few months later Morriss received a letter from Beale explaining that the box contained encrypted "papers vitally affecting the fortunes of myself and many other engaged in business with me" and that the key to decrypt the papers had been left with "a friend in [St. Louis]." If Beale never returned, Morriss was to open the box 10 years later in 1832, at which time the key was supposed to be delivered from St. Louis.

Morriss waited until 1845 to open the box, and the key never arrived. Inside he found a letter addressed to him, explaining that Beale and his companions had discovered a large cache of gold and silver near Santa Fe, and they had spent several years mining the area. The purpose of Beale's stay in 1820 was to hide in Virginia the gold and silver they had already discovered. He returned in 1822 to hide what had been mined during the previous 2 years. During those 2 years, he and his companions decided that, in case anything should happen to them, they should prepare for their family to receive the treasure they had amassed. The other three papers in the box were encrypted. According to the letter addressed to Morriss, the first paper describes the exact location of the buried treasure. The second describes the vault the treasure is buried in, along with the contents of the vault. The third paper lists the "next of kin" to whom the treasure should be given.

Morriss spent much of the rest of his life trying to decrypt these papers, and he failed. He gave the papers to a friend (name unknown) who spent spent over 20 years in the same pursuit. Finally, in 1885 the anonymous friend gave up the search, and published the Beale Papers in a pamphlet, with all of the facts he had received from Morriss. He writes that the pursuit of the Beale treasure had ruined his life and his relationship with his family, and that he didn't want any part of it anymore. But, before he gave up, he managed to decrypt the second paper, the one that describes the treasure. He discovered that the second paper was enciphered with a [Book Cipher](https://en.wikipedia.org/wiki/Book_cipher), and the Declaration of Independence was the key.

Since that time, a large number of treasure hunters, adventurers, and cryptanalysts have tried to discover the key used to encipher the other two Beale papers, and to this day no one has succeeded. The lack of success has caused some to believe the whole thing is a hoax (see [note 2](#note-2)), but there are many clues that suggest that the Beale Papers are authentic, and treasure seekers continue to scour the Virginia countryside looking for the mysterious vault.

## Entwyption

One aspect of the Beale story that I find most intriguing, aside from the fact that it is a 200 year old, real life, buried treasure mystery that remains unsolved, is the strength of the Book Cipher. The Book Cipher works by numbering the words in a text, where each number represents the first letter of the word. The process of encoding and decoding with a Book Cipher is quite simple, especially when compared with many other ciphers, new and old. The strength of the Book Cipher is that without discovering the key, the encrypted text is almost impossible to decrypt. Beale Paper \#2 was successfully decrypted because the key happened to be a very famous and very public document. Simon Singh, author of The Code Book, offers this explanation for the impenetrability of the remaining two papers: what if they were encrypted using an essay about buffalo hunting written by Thomas Beale as a key? What if there was only one copy of the essay, and it was lost or destroyed by the friend in St. Louis? Decryption would be virtually impossible.

In the age of Twitter and Facebook, almost everything we write is public, but it is also obscure, lost in the torrent of the [stream](http://smfoote.com/blog/2015/12/11/feed-ux-anti-pattern/). If you follow enough people (or active enough people) on Twitter, a single day worth of tweets could fill a book.

So, the idea of "Entwyption" is to use the Twitter feed as the key for a book cipher. The "Twitter book" is so vast that any small subset of it is large enough to be the key for a book cipher, and small enough to obscure. The "Twitter book" key can also be dynamically composed. For example, it could be the tweets of all of the people I follow from Jan. 5 at 3:14 PM through Jan. 7 (in reverse order (excluding users with a Twitter handle staring with "R")). The key is virtually undiscoverable by a potential eavesdropper. But for the intended recipient, the key is quite easily attainable using the Twitter API. Indeed, the whole process could be fairly easily automated. It's not perfect privacy, but I think it's [pretty good](https://en.wikipedia.org/wiki/Pretty_Good_Privacy). At the very least, it's pretty fun privacy.

Thanks to [Jeremy Foote](http://jeremydfoote.com/) for discussing these ideas with me (years ago).

<aside id="note-1"><b>Note 1:</b> My wife gave me a day at the Computer History Museum in Mountain View as a Christmas present last year. I saw a _real_ enigma and a replica Babbage Difference Engine \#2 (and my daughter and I sat in a retired Google self-driving car)!</aside>

<aside id="note-2"><b>Note 2:</b> There is a pretty lively debate about whether the Beale Papers and treasure are not a big hoax, but I prefer to believe that they do exist. Like I said, the story has captured my imagination.</aside>