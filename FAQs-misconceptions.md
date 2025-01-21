### nostr misconceptions and FAQ
The purpose of these questions is to anticipate dev and non-dev questions & pushback, as they are in the early stages of discovering nostr. The questions have been distributed to nostr devs, and non-devs, so that we have a sampling of answers that may help assuage nostr newcomer uncertainty and uneasiness. These questions and the provided answers will be hosted on a website somewhere by @fiatjaf. Maybe nostr github repo will link to this website.

### questions

<details>

<summary>1. Do I have to paste my key everywhere?, isn't that unsafe? </summary>

`No, you should only enter your key into a few trusted applications or devices. however most newer clients only support pasting your key in because its the easiest way for the developer to build the client.` -[hzrd149](https://github.com/hzrd149/)

`No, you don't have to, but many clients allow you to do so out of ease of use. If the client supports using something called Amber, or a Remote Signer, or a browser extension, I would recommend you to use those instead as they are more secure and help keep your private key safe. It's not recommended to paste your key into unkown or new applications. It is okay to generate burner or new keys to try things out.` -[Derek Ross](https://njump.me/npub18ams6ewn5aj2n3wt2qawzglx9mr4nzksxhvrdc4gzrecw7n5tvjqctp424)

`No, but it depends on the platform and app used. Most mobile apps default to key pasting, and some offer to back them up in the user's cloud storage. On desktop it's recommended to use a browser extension that stores the private key allowing the user to sign events. Pasting a private key into a malicious app, or accidentally pasting it publicly will compromise the key permanently. There are also remote signing methods, but there is a steeper learning curve for users who are only accustomed to traditional login methods.` -[The: Daniel](https://njump.me/npub1aeh2zw4elewy5682lxc6xnlqzjnxksq303gwu2npfaxd49vmde6qcq4nwx) 

</details>

<details>

<summary>2. Why can't I create subkeys or rotate my key? </summary>

`Complexity. Creating subkeys is easy, but supporting subkeys and by extension permissions and key rotation in all clients is almost impossible.` -[hzrd149](https://github.com/hzrd149/)

`People smarter than me have said that this is too hard to implement. I wish that we had this feature. It would make things easier for the inevitable happens for most people.` -[Derek Ross](https://njump.me/npub18ams6ewn5aj2n3wt2qawzglx9mr4nzksxhvrdc4gzrecw7n5tvjqctp424)

</details>

<details>

<summary>3. How do I lend my key so others can sign with it on my behalf? </summary>

`Remote signers seem to be the best method to allow apps and other users sign on your behalf. they allow you to give out a unique API endpoint of sorts that lets the other user or client ask you to sign something` -[hzrd149](https://github.com/hzrd149/)
`You utilize something called a Remote Signer or an nsecbunker application with poligicies and key management features. These include tools such as Amber, NAK, Keycast, or Knox. `
-[Derek Ross](https://njump.me/npub18ams6ewn5aj2n3wt2qawzglx9mr4nzksxhvrdc4gzrecw7n5tvjqctp424)

</details>

<details>

<summary>4. Nostr is centralized because everybody will just use the same big relays! </summary>

`Yes, large data and connection speeds tend to cause centralization. however the data itself (events) is cryptographically signed so its possible for it to live on multiple servers and still be verifiable. This does not prevent centralization it only ensures that the authenticity of the data is no longer tied to the server it came from` -[hzrd149](https://github.com/hzrd149/)

`This is a common misconception. The Outbox and Inbox model fixes this, enabling users from all around the world to all run their very own relays and still be able to communicate toghether. For this to happen, all clients need to upgrade to NIP-65 to enable Outbox/Inbox models. I feel that we'll end up having a plethora of family relays, community relays, making nostr much more decentralized and sustainable.`-[Derek Ross](https://njump.me/npub18ams6ewn5aj2n3wt2qawzglx9mr4nzksxhvrdc4gzrecw7n5tvjqctp424)

</details>

<details>

<summary>5. If there is no Blockchain, no DHT, no central directory then how do I find out in which relay a given key is publishing their events to? </summary>

` every relay is a local directory similar to a phone book (yellow pages), the relays tend to be topic or location specific so you only need to find the general topic or area where the key publishes to be able to find their home relays` -[hzrd149](https://github.com/hzrd149/)

`I would look at a user's profile and see which relays they're using, but this also can be a bit confusing, because clients don't always surface this information easily, confusing profile relays and Outbox relays. Plus, anyone can broadcast an event to any public relay.` -[Derek Ross](https://njump.me/npub18ams6ewn5aj2n3wt2qawzglx9mr4nzksxhvrdc4gzrecw7n5tvjqctp424)

</details>

<details>

<summary>6. Nostr doesn't have discovery! </summary>

` Follow random people, ask more questions. nostr isn't curated like other platforms and wont automatically serve you the content you want to see, you have to go find it` -[hzrd149](https://github.com/hzrd149/)

`At the protocol level, Nostr does not have discovery, that is correct. However, many clients are working on various forms of user discovery such as trending topics, trending users, trending notes, Web of Trust, various feed algorithms, and more. If your client doesn't have user and content discovery, then you should check out one of the clients that do.`-[Derek Ross](https://njump.me/npub18ams6ewn5aj2n3wt2qawzglx9mr4nzksxhvrdc4gzrecw7n5tvjqctp424)

</details>

<details>

<summary>7. Nostr is a nazi bar because we can't censor bad actors, criminals, spammers, scammers, stalkers, harassers! </summary>

` nostr shares a lot of similarities with the internet in this way. communities and smaller public spaces will have moderation but there is no way to prevent the distasteful people from creating their own communities` -[hzrd149](https://github.com/hzrd149/)

`There is the potential for this, but I feel that user controls, user tools, and community moderations via Web of Trust and reporting can resole a lot of these issues. `-[Derek Ross](https://njump.me/npub18ams6ewn5aj2n3wt2qawzglx9mr4nzksxhvrdc4gzrecw7n5tvjqctp424)

`Nostr is different than centralized networks because the user is entirely in control of the content they choose to see. By using whitelisted relays and mute lists, users can avoid interacting with spammers and other users who post content they object to. It's true that anyone with a valid key can use the network, but this also provides censorship resistance for everyone. In addition, the difficulty of permanently deleting content may also decrease the likelihood of Nostr being used by bad actors.` -[The: Daniel](https://njump.me/npub1aeh2zw4elewy5682lxc6xnlqzjnxksq303gwu2npfaxd49vmde6qcq4nwx) 

</details>

<details>

<summary>8. Nostr is for crypto-bros only </summary>

` crypto bros like experimental technology so they are the first adopters, but there are smaller communities talking about other topics and as they continue to grow things will get a lot more interesting` -[hzrd149](https://github.com/hzrd149/)

`Nope. Nostr is for Bitcoin bros only! Joking... Don't publish that. Nostr is for everyone, because everyone deserves the freedom to communicate. At this time, the portion of the population that recognizes the need for freedom of communication is also the same crowd that recognizes the need for freedom to transact. Someone has to be first to the socila media revolution and right now, it's those that recognize the need for decentralization and censorship resistant communication such as freedom fighters and Bitcoiners. Nostr doesn't need Bitcoin and Bitcoin doesn't need Nostr, but they do do have a beautiful symbiotic relationship together. `-[Derek Ross](https://njump.me/npub18ams6ewn5aj2n3wt2qawzglx9mr4nzksxhvrdc4gzrecw7n5tvjqctp424)

</details>

<details>

<summary>9. Is there a nostr wiki? </summary>

` There are some getting started guides, but I don't know of any nostr wiki yet` -[hzrd149](https://github.com/hzrd149/)

`There is a client called Wikifreedia, but there is no official Wiki. I've honestly thought about trying to create a Wiki for every client, then each client could link to the Wiki to have their users find help and support. I still think someone should build this. I don't have time. It's needed.`-[Derek Ross](https://njump.me/npub18ams6ewn5aj2n3wt2qawzglx9mr4nzksxhvrdc4gzrecw7n5tvjqctp424)

</details>

<details>

<summary>10. Is there a SDK with some easy to customize demos? </summary>

` There are a ton of great SDKs and simple apps on https://github.com/aljazceru/awesome-nostr` -[hzrd149](https://github.com/hzrd149/)

`There is the Nostr Development Kit and other SDKs, but I am not aware of buildable demos.`-[Derek Ross](https://njump.me/npub18ams6ewn5aj2n3wt2qawzglx9mr4nzksxhvrdc4gzrecw7n5tvjqctp424)

</details>

<details>

<summary>11. How can my community/website/product join nostr? </summary>

`There aren't many good community on boarding tools or guides yet but the best option currently would be to look into setting up a group relay` -[hzrd149](https://github.com/hzrd149/)

`Joining is easy. Where we're failing at is on-boarding. Only two applicaitons have good onboarding - Damus and Primal. However, these applications are not good for businesses who often need to designate social media tasks to employees. They do not support Remote Signers or nsecbunkers. That aside, I would tell all of your community members to join nostr, follow one another, and start building your community by utilizing community tools such as Chachi, Flotilla, Zap.stream, or Nostr Nests.`-[Derek Ross](https://njump.me/npub18ams6ewn5aj2n3wt2qawzglx9mr4nzksxhvrdc4gzrecw7n5tvjqctp424)

</details>

<details>

<summary>12. This sounds like another VC funded "protocol" in Bluesky, or Farcaster. How does nostr protect from the ensuing enshittification? </summary>

` There is no nostr development team, so there is no one to say what can or cant be done on the protocol. developers are free to build and experiment however they like` -[hzrd149](https://github.com/hzrd149/)

`Nostr is not VC funded and is completely open. There is no central company. There is no central organization. There is no central development team. While some companies that utilize nostr may be VC funded, the protocol itself is not.`-[Derek Ross](https://njump.me/npub18ams6ewn5aj2n3wt2qawzglx9mr4nzksxhvrdc4gzrecw7n5tvjqctp424)

</details>
   
<details>

<summary>13. How does nostr elude capture by a well funded VC company? </summary>

`I don't know, I guess we will see when the time comes` -[hzrd149](https://github.com/hzrd149/)

`User choice. If a large company decides to build upon nostr, that is fine. Users will have to choice to migrate to another application with ese if they don't like the direction that said company is going or features that they're implementing.
`-[Derek Ross](https://njump.me/npub18ams6ewn5aj2n3wt2qawzglx9mr4nzksxhvrdc4gzrecw7n5tvjqctp424)

</details>
    
