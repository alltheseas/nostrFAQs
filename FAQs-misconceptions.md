### nostr misconceptions and FAQ
The purpose of these questions is to anticipate dev and non-dev questions & pushback, as they are in the early stages of discovering nostr. The questions have been distributed to nostr devs, and non-devs, so that we have a sampling of answers that may help assuage nostr newcomer uncertainty and uneasiness. These questions and the provided answers will be hosted on a website somewhere by @fiatjaf. Maybe nostr github repo will link to this website.

### questions

<details>

<summary>1. Do I have to paste my key everywhere?, isn't that unsafe? </summary>

`No, you should only enter your key into a few trusted applications or devices. however most newer clients only support pasting your key in because its the easiest way for the developer to build the client.` -[hzrd149](https://github.com/hzrd149/)

</details>

<details>

<summary>2. Why can't I create subkeys or rotate my key? </summary>

`Complexity. Creating subkeys is easy, but supporting subkeys and by extension permissions and key rotation in all clients is almost impossible.` -[hzrd149](https://github.com/hzrd149/)

</details>

<details>

<summary>3. How do I lend my key so others can sign with it on my behalf? </summary>

`Remote signers seem to be the best method to allow apps and other users sign on your behalf. they allow you to give out a unique API endpoint of sorts that lets the other user or client ask you to sign something` -[hzrd149](https://github.com/hzrd149/)

</details>

<details>

<summary>4. Nostr is centralized because everybody will just use the same big relays! </summary>

`Yes, large data and connection speeds tend to cause centralization. however the data itself (events) is cryptographically signed so its possible for it to live on multiple servers and still be verifiable. This does not prevent centralization it only ensures that the authenticity of the data is no longer tied to the server it came from` -[hzrd149](https://github.com/hzrd149/)

</details>

<details>

<summary>5. If there is no Blockchain, no DHT, no central directory then how do I find out in which relay a given key is publishing their events to? </summary>

` every relay is a local directory similar to a phone book (yellow pages), the relays tend to be topic or location specific so you only need to find the general topic or area where the key publishes to be able to find their home relays` -[hzrd149](https://github.com/hzrd149/)

</details>

<details>

<summary>6. Nostr doesn't have discovery! </summary>

` Follow random people, ask more questions. nostr isn't curated like other platforms and wont automatically serve you the content you want to see, you have to go find it` -[hzrd149](https://github.com/hzrd149/)

</details>

<details>

<summary>7. Nostr is a nazi bar because we can't censor bad actors, criminals, spammers, scammers, stalkers, harassers! </summary>

` nostr shares a lot of similarities with the internet in this way. communities and smaller public spaces will have moderation but there is no way to prevent the distasteful people from creating their own communities` -[hzrd149](https://github.com/hzrd149/)

</details>

<details>

<summary>8. Nostr is for crypto-bros only </summary>

` crypto bros like experimental technology so they are the first adopters, but there are smaller communities talking about other topics and as they continue to grow things will get a lot more interesting` -[hzrd149](https://github.com/hzrd149/)

</details>

<details>

<summary>9. Is there a nostr wiki? </summary>

` There are some getting started guides, but I don't know of any nostr wiki yet` -[hzrd149](https://github.com/hzrd149/)

</details>

<details>

<summary>10. Is there a SDK with some easy to customize demos? </summary>

` There are a ton of great SDKs and simple apps on https://github.com/aljazceru/awesome-nostr` -[hzrd149](https://github.com/hzrd149/)

</details>

<details>

<summary>11. How can my community/website/product join nostr? </summary>

`There aren't many good community on boarding tools or guides yet but the best option currently would be to look into setting up a group relay` -[hzrd149](https://github.com/hzrd149/)

</details>

<details>

<summary>12. This sounds like another VC funded "protocol" in Bluesky, or Farcaster. How does nostr protect from the ensuing enshittification? </summary>

` There is no nostr development team, so there is no one to say what can or cant be done on the protocol. developers are free to build and experiment however they like` -[hzrd149](https://github.com/hzrd149/)

</details>
   
<details>

<summary>13. How does nostr elude capture by a well funded VC company? </summary>

`I don't know, I guess we will see when the time comes` -[hzrd149](https://github.com/hzrd149/)

</details>
    
