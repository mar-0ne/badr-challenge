# badr-challenge
### A friend of mine wrote a challenge for me. I'm solving it here :)

1 **first step**</br> He asked me to generate a pair of GPG keys and send the public key to him. </br>

`$ gpg --full-generate-key` </br>

2 **second step**</br> He sent to me an Image: ![The San Juan Mountains are beautiful!](black.hole "black hole")</br>
Well, that image was containing a text inside of it, he wrote int the instructions that I should get that text: </br>

`$ cat black.hole` </br>

3 **third step**</br>
The text is: *Follow the txt in the* [marone.pythops.com](https://marone.pythops.com) </br>
if you go to that URL in the browser it's not going to work! that's the trick cause he meant by *follow the txt* to check the value of the TXT DNS record !!! </br>

`$ dig -t txt marone.pythops.com` </br>

the value of the TXT record is: *"aHR0cDovL3hscWlxenlid2FxN3NlbWliNXRxNGlkejc0bGdzcGx5czI1Mmdlb3ozdTdnZ3M3a3Z1bWV1NXFkLm9uaW9uL2NoYWxsZW5nZQ=="* </br>

4 **fourth step**</br>
well, this is a base64 string so I need to convert it to text: </br>

`$ echo aHR0cDovL3hscWlxenlid2FxN3NlbWliNXRxNGlkejc0bGdzcGx5czI1Mmdlb3ozdTdnZ3M3a3Z1bWV1NXFkLm9uaW9uL2NoYWxsZW5nZQ== | base64 --decode` </br>

5 **fifth step**</br>
once again the output is a URL: [it a .onion link !](http://xlqiqzybwaq7semib5tq4idz74lgsplys252geoz3u7ggs7kvumeu5qd.onion/challenge) which means I should install [Tor browser](https://www.torproject.org/download/) in order to open that link. </br> By going to that link I got a file to downlod, after downloading it, I figured out that it is encrypted, that's why he asked me to generate the GPG key. </br>I decrypted the file: </br>

`$ gpg --output doc --decrypt challenge` </br>

the text in the file i: *Build an API that returns the public IPv4 or IPv6. So people can know easily their public IPs* which is the final step.

6 **sixth step**</br> building the API


