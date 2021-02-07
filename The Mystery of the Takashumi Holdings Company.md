# The Mystery of the Takashumi Holdings Company

## The setup
Valentin Molina noticed on his google slide account that there were several shared slides that appeared to be compromised.

<img src="https://github.com/fordepowers/tales-from-the-pandemic/blob/master/images/slides.png" alt="Google Slides" />

He didn't have ownership over these slide sets, and at first glance they appeared to either be spam or outright malicious.
Immediately, we assumed his google account had been compromised. I got on a Discord call with him to try and do some incident response, see if we couldn't contain and assess the damage, and pinpoint the entry point and attacker.
Val was using Chrome while on his Mac, and was sharing his screen to me as I talked him through steps and took notes.
More than anything, we were intrigued. This looked like nothing else I'd seen.

## The evidence
So, we began gathering evidence and discovered some facts.
1. Google listed the slide decks as being created in 2019.
2. Val did not own the slides, they were being shared with him.
3. Google said the last time Val had looked at these slides was November 13th, 2020.
4. Val said he couldn't remember the last time he'd actually checked his google slides - he didn't use it often.
5. The slides were an absolute cluster of information. Different languages, nonsense words and phrases, popular meme slogans and sayings, random images and videos made up the content of them.
6. However, nothing within the slides was outright malicious, spam, or illicit. Everything pointed back to a company by the name of "Takashumi Holdings Company".
7. The slides also linked exclusively to a google sites website, displaying the same company name.
8. This website was massive and sprawling, with the worst UX I've ever seen. It contained thousands of hyperlinks, external pages, and was composed primarily of linked google docs and google slides (like the ones that brought Val here) 
9. By far the website was one of the largest I've ever seen. The content appeared to be more chaos than anything else, but there was a lot of content.
10. The google site appeared to be one of many satellite sites. In the top left, the site was described as "T61 PreSite Free", and via hyperlinks more sites were discovered (T1 and so on).

<img src="https://github.com/fordepowers/tales-from-the-pandemic/blob/master/images/google-site.png" alt="Google Site" />

11. Site manager email appeared to be "015cameoavenue@gmail.com". Searching this email yielded nothing new.
12. Buried within the site a name was found, "David Evans" and a picture of a middle aged man. Reverse-image searching, we found that this man is on the board of Education at a Missouri school (same photo).

<img src="https://github.com/fordepowers/tales-from-the-pandemic/blob/master/images/david.png" alt="Google Site" />

13. Searching for the company name yielded the same google site, a Facebook page, Twitter account, Youtube account, and Instagram among other accounts also by the same name.
14. These additional social media accounts also appeared to follow the same nonsense format - posting completely random photos and comments across each other's accounts.

<img src="https://github.com/fordepowers/tales-from-the-pandemic/blob/master/images/youtube.png" alt="Google Site" />

15. On twitter, a user "Andy Baio" tweeted out a link to the google site on November 13th, 2020. Andy is a prolific developer, who has many followers, and appeared to be in control of his account after that random tweet.

<img src="https://github.com/fordepowers/tales-from-the-pandemic/blob/master/images/tweet.png" alt="Google Site" />

16. Performing steganography scans on some of the website images yielded no hidden data.
17. At some point in the maze of google slides and sub-sites, the name "Cicada 3301" was referenced. This is a famous internet cyrptography/stegonography puzzle that started in 2012.

## The theories
As we collected evidence and dug deeper into this rabbit hole of a story, I worked under the assumption of a few possible theories as to what was happening:

### Theory One
Val's google account could have been compromised by a malicious actor. This actor then created these slides, either as a prank or for illicit purposes, and then left them with Val so that way they would show up in his google slides. This had happened months ago, and Val never checked his slides until now.
There was a few issues with this first theory:
1. Val had Multi-Factor Authentication (MFA) enabled. This would have made it difficult/impossible to breach his account.
2. Val had no unauthorized logins since google security started recording them.
3. Val had no outstanding sessions. Every device that he was signed in on was authorized.
4. Val had not had a breach since he had last changed passwords (haveibeenpwned.com)
5. Val didn't actually even have ownership of the slides in question.
6. No other Indicators of Compromise (IOCs) existed on his account. The slides appeared as the lone anomaly.

### Theory Two
Val was working with another individual that owned these google slides. This could have been sometime in the last year, and the collaboration was from school. Long after they had stopped using the slides for the original purpose, that other individual had their account compromised, and the slides were changed to instead server a more malicious or illicit purpose.
There was a few issues with this as well:
1. Val claimed he had not been using Google slides back in November of 2020 for any school related project.
2. In total, there were 11 'compromised' slides we could see. Val did not have that number of shared slides with any one individual.

### Theory Three
At some point, Val clicked on either a Google slide link out in the wild, or a google site link that led them to be associated to his account and therefore show up underneath his slides page. These slides may have been normal content at one point, but then had eventually gotten changed to the phenomenon we had seen.
The lone issue with this theory:
1. All of the last access dates for the slides was the same, November 13th 2020. Val stated he did not access 11 different slides on that day, or any day near it.

## The revelation
It was at this point we hit a huge piece of information. Up to now, I was personally convinced Val had stumbled upon either a botnet facilitation website, a hidden command and control relay network, or perhaps some front for a secretive darkweb hidden service. I had several reasons for this, primarily the obfuscated text content, random design of the website, and the sprawling list of bogus accounts connected to this obviously fake company. It's not uncommon for a 'hidden in plain site' communication relay like this to occur- bots would connect to the site, scan some encrypted or encoded text content, and then deduce commands based on the hidden message the webmaster had prescribed. Moreover, most of the content appeared to have been scraped from other sites on the internet, including that really random reference to a Missouri public school.
> However, after some more research, we stumbled across a machine curated Twitter API page that contained this google site URL. Next to it, was a linked article on a little-known blog that listed this google site.

It was written by a design blogsite, and it was titled 'Exploring the World's Worst Website'. In it, the author explained a reddit post on the r/web_design subreddit.
This reddit post tells the story of a user who spent 3 years creating the world's worst website as a proof-of-concept and a practical joke. They went into detail about the design philosophy, structure of the page, content and easter eggs, and origin. It seems we had found our 'hacker', just a practical prank site created by a user.

## The conclusion
But a few questions remained unanswered.
- How did Val get those slides on his account?
- Why was the actual text content of the site so odd?

To the first one, we concluded that since it works via google docs and slides that are linked to the site, when navigating to the page google automatically shares that with the user (should they be signed in) and it then shows up on your account. Val, probably back around the time this article was created, navigated to the site and forgot about it, then didn't check his google slides until months later.

As to the second, we think that the author of the site employed extensive use of botting and scripting to scrape enough random web content to add to his behemoth of a page. This would also explain the random comments throughout the site.
> Some questions still remain...

Shockingly, that reddit post (the supposed origin of all this info) was posted sometime in [December of 2020]. The article itself was written in November 15th, 2020, and it directly references the post! How could it come after? And, how could Andy Baio know about and tweet about it before then?

Further, Val states that the only place he could have seen it was hacker-news.com. Upon searching, that site did not have any articles about Takashumi within that time frame for Val to visit it.