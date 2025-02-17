### nostr misconceptions and FAQ
The purpose of these questions is to anticipate dev and non-dev questions & pushback, as they are in the early stages of discovering nostr. The questions have been distributed to nostr devs, and non-devs, so that we have a sampling of answers that may help assuage nostr newcomer uncertainty and uneasiness. These questions and the provided answers will be hosted on a website somewhere by @fiatjaf. Maybe nostr github repo will link to this website.

### questions

<details>

<summary>1. Do I have to paste my key everywhere?, isn't that unsafe? </summary>

`No, you should only enter your key into a few trusted applications or devices. however most newer clients only support pasting your key in because its the easiest way for the developer to build the client.` -[hzrd149](https://github.com/hzrd149/)

`No, you don't have to, but many clients allow you to do so out of ease of use. If the client supports using something called Amber, or a Remote Signer, or a browser extension, I would recommend you to use those instead as they are more secure and help keep your private key safe. It's not recommended to paste your key into unknown or new applications. It is okay to generate burner or new keys to try things out.` -[Derek Ross](https://njump.me/npub18ams6ewn5aj2n3wt2qawzglx9mr4nzksxhvrdc4gzrecw7n5tvjqctp424)

`No, but it depends on the platform and app used. Most mobile apps default to key pasting, and some offer to back them up in the user's cloud storage. On desktop it's recommended to use a browser extension that stores the private key allowing the user to sign events. Pasting a private key into a malicious app, or accidentally pasting it publicly will compromise the key permanently. There are also remote signing methods, but there is a steeper learning curve for users who are only accustomed to traditional login methods.` -[The: Daniel](https://njump.me/npub1aeh2zw4elewy5682lxc6xnlqzjnxksq303gwu2npfaxd49vmde6qcq4nwx)

`You can paste your nsec into various applications, but if you're concerned about security, you probably shouldn't. Alternatively, you can use a bunker, which is an application that holds your nsec and signs events with it (e.g. Amber).` -[pip](https://njump.me/npub176p7sup477k5738qhxx0hk2n0cty2k5je5uvalzvkvwmw4tltmeqw7vgup)

`Use a browser extension. Some remote signer apps like Amber also work but some others are hard to use, do not give you full control over access policies and have subpar code quality` -[semisol](https://njump.me/npub12262qa4uhw7u8gdwlgmntqtv7aye8vdcmvszkqwgs0zchel6mz7s6cgrkj)

`Mostly, and yes. Giving an app your key gives them the ability to publish things on your behalf, and it's impossible to know after you've removed a key from an app that it's really gone. So only put your important keys in apps you really trust.` -[Matt Lorentz](https://njump.me/npub16zsllwrkrwt5emz2805vhjewj6nsjrw0ge0latyrn2jv5gxf5k0q5l92l7)


</details>

<details>

<summary>2. Why can't I create subkeys or rotate my key? </summary>

`Complexity. Creating subkeys is easy, but supporting subkeys and by extension permissions and key rotation in all clients is almost impossible.` -[hzrd149](https://github.com/hzrd149/)

`People smarter than me have said that this is too hard to implement. I wish that we had this feature. It would make things easier for the inevitable happens for most people.` -[Derek Ross](https://njump.me/npub18ams6ewn5aj2n3wt2qawzglx9mr4nzksxhvrdc4gzrecw7n5tvjqctp424)

`You can generate subkeys from your master key (see NIP 6). Rotating a key means communicating to the world in a non-ambiguous way what your next key will be. In the case of a hack, this can lead to race conditions (e.g. the hacker and you try to rotate the key at the same time). Today, there are no good ways to solve such race conditions other than anchoring on a blockchain. However, in the future, with Frost and the like (I think), you'll be able to have a threshold of keys. If at least m out of n keys sign, then the signature is valid (say 2 out of 3). If you lose one of the keys, you can create a new set of keys corresponding to the old public key, so rotating keys is not necessary.` -[pip](https://njump.me/npub176p7sup477k5738qhxx0hk2n0cty2k5je5uvalzvkvwmw4tltmeqw7vgup)

`There is no reason except that no one wants to start implementing it because it’s “too complex”, and the amount of NIP bikeshedding.` -[semisol](https://njump.me/npub12262qa4uhw7u8gdwlgmntqtv7aye8vdcmvszkqwgs0zchel6mz7s6cgrkj)

`Nostr is designed to be the simplest protocol that works, so one key = one account. Subkeys and rotation would mean that every app needs a significant amount of code to tie multiple keys to a single identity.` -[Matt Lorentz](https://njump.me/npub16zsllwrkrwt5emz2805vhjewj6nsjrw0ge0latyrn2jv5gxf5k0q5l92l7)


</details>

<details>

<summary>3. How do I lend my key so others can sign with it on my behalf? </summary>

`Remote signers seem to be the best method to allow apps and other users sign on your behalf. they allow you to give out a unique API endpoint of sorts that lets the other user or client ask you to sign something` -[hzrd149](https://github.com/hzrd149/)

`You utilize something called a Remote Signer or an nsecbunker application with policies and key management features. These include tools such as Amber, NAK, Keycast, or Knox.`
-[Derek Ross](https://njump.me/npub18ams6ewn5aj2n3wt2qawzglx9mr4nzksxhvrdc4gzrecw7n5tvjqctp424)

`with bunkers (currently many work like shit)` -[pip](https://njump.me/npub176p7sup477k5738qhxx0hk2n0cty2k5je5uvalzvkvwmw4tltmeqw7vgup)

`Remote signers. Most do not allow fine grained access policies though.` -[semisol](https://njump.me/npub12262qa4uhw7u8gdwlgmntqtv7aye8vdcmvszkqwgs0zchel6mz7s6cgrkj)

`You should never lend someone you don't trust your key. You can look for a "signer" app you trust that has a good permissions system and will sign requests from other apps if they meet the criteria you specify.` -[Matt Lorentz](https://njump.me/npub16zsllwrkrwt5emz2805vhjewj6nsjrw0ge0latyrn2jv5gxf5k0q5l92l7)

</details>

<details>

<summary>4. Nostr is centralized because everybody will just use the same big relays! </summary>

`Yes, large data and connection speeds tend to cause centralization. however the data itself (events) is cryptographically signed so its possible for it to live on multiple servers and still be verifiable. This does not prevent centralization it only ensures that the authenticity of the data is no longer tied to the server it came from` -[hzrd149](https://github.com/hzrd149/)

`This is a common misconception. The Outbox and Inbox model fixes this, enabling users from all around the world to all run their very own relays and still be able to communicate together. For this to happen, all clients need to upgrade to NIP-65 to enable Outbox/Inbox models. I feel that we'll end up having a plethora of family relays, community relays, making nostr much more decentralized and sustainable.`-[Derek Ross](https://njump.me/npub18ams6ewn5aj2n3wt2qawzglx9mr4nzksxhvrdc4gzrecw7n5tvjqctp424)

`The fiatjaf analogy holds: relays are like websites, and not everyone visits the same websites. If anything, direct monetization with bitcoin allows smaller relays to thrive.` --[pip](https://njump.me/npub176p7sup477k5738qhxx0hk2n0cty2k5je5uvalzvkvwmw4tltmeqw7vgup)

`Doesn’t matter because people can switch relays and migrate their data easily` -[semisol](https://njump.me/npub12262qa4uhw7u8gdwlgmntqtv7aye8vdcmvszkqwgs0zchel6mz7s6cgrkj)

</details>

<details>

<summary>5. If there is no Blockchain, no DHT, no central directory then how do I find out in which relay a given key is publishing their events to?</summary>

` every relay is a local directory similar to a phone book (yellow pages), the relays tend to be topic or location specific so you only need to find the general topic or area where the key publishes to be able to find their home relays` -[hzrd149](https://github.com/hzrd149/)

`I would look at a user's profile and see which relays they're using, but this also can be a bit confusing, because clients don't always surface this information easily, confusing profile relays and Outbox relays. Plus, anyone can broadcast an event to any public relay.` -[Derek Ross](https://njump.me/npub18ams6ewn5aj2n3wt2qawzglx9mr4nzksxhvrdc4gzrecw7n5tvjqctp424)

`You can ask some specialized relays, but the question is backwards. If you want to find the events of an npub, it's because you have have already seen some of the contents of the npub, and already know the npub, which means you have had contact with it before. Why else would you want to find the events of a random string?` -[pip](https://njump.me/npub176p7sup477k5738qhxx0hk2n0cty2k5je5uvalzvkvwmw4tltmeqw7vgup)

`Large directories and from existing relays.` -[semisol](https://njump.me/npub12262qa4uhw7u8gdwlgmntqtv7aye8vdcmvszkqwgs0zchel6mz7s6cgrkj)

`You try as hard as you can, and it turns out that's generally enough.` -[Matt Lorentz](https://njump.me/npub16zsllwrkrwt5emz2805vhjewj6nsjrw0ge0latyrn2jv5gxf5k0q5l92l7)

</details>

<details>

<summary>6. Nostr doesn't have discovery! </summary>

` Follow random people, ask more questions. nostr isn't curated like other platforms and wont automatically serve you the content you want to see, you have to go find it` -[hzrd149](https://github.com/hzrd149/)

`At the protocol level, Nostr does not have discovery, that is correct. However, many clients are working on various forms of user discovery such as trending topics, trending users, trending notes, Web of Trust, various feed algorithms, and more. If your client doesn't have user and content discovery, then you should check out one of the clients that do.`-[Derek Ross](https://njump.me/npub18ams6ewn5aj2n3wt2qawzglx9mr4nzksxhvrdc4gzrecw7n5tvjqctp424)

`It does.` -[pip](https://njump.me/npub176p7sup477k5738qhxx0hk2n0cty2k5je5uvalzvkvwmw4tltmeqw7vgup)

`Discovery is a not very hard to solve problem that most devs do not prioritize, because it isn’t a problem for them.` -[semisol](https://njump.me/npub12262qa4uhw7u8gdwlgmntqtv7aye8vdcmvszkqwgs0zchel6mz7s6cgrkj)

`Not true! Nostr has search engines and recommendation algorithms just like other networks. However the amount of time and money spent optimizing Nostr apps for "engagement" is nothing compared to Big Tech platforms, so you likely find less personalized entertainment being served to you on silver platter here.` -[Matt Lorentz](https://njump.me/npub16zsllwrkrwt5emz2805vhjewj6nsjrw0ge0latyrn2jv5gxf5k0q5l92l7)

</details>

<details>

<summary>7. Nostr is a nazi bar because we can't censor bad actors, criminals, spammers, scammers, stalkers, harassers! </summary>

` nostr shares a lot of similarities with the internet in this way. communities and smaller public spaces will have moderation but there is no way to prevent the distasteful people from creating their own communities` -[hzrd149](https://github.com/hzrd149/)

`There is the potential for this, but I feel that user controls, user tools, and community moderations via Web of Trust and reporting can resolve a lot of these issues. `-[Derek Ross](https://njump.me/npub18ams6ewn5aj2n3wt2qawzglx9mr4nzksxhvrdc4gzrecw7n5tvjqctp424)

`Nostr is different than centralized networks because the user is entirely in control of the content they choose to see. By using whitelisted relays and mute lists, users can avoid interacting with spammers and other users who post content they object to. It's true that anyone with a valid key can use the network, but this also provides censorship resistance for everyone. In addition, the difficulty of permanently deleting content may also decrease the likelihood of Nostr being used by bad actors.` -[The: Daniel](https://njump.me/npub1aeh2zw4elewy5682lxc6xnlqzjnxksq303gwu2npfaxd49vmde6qcq4nwx)

`Relays are responsible for moderation, and most relays don’t care until they are forced to act` -[semisol](https://njump.me/npub12262qa4uhw7u8gdwlgmntqtv7aye8vdcmvszkqwgs0zchel6mz7s6cgrkj)

`I haven't seen many Nazis but It's true that the public space on Nostr has attracted a lot of folks who aren't welcomed on the big platforms. But Nostr isn't just the global feed you find in a Twitter-like app. It's full of private spaces like groups, audio chats, and private DMs. So if your people aren't the type to be shouting in the town square you might need to look a little harder for them.` -[Matt Lorentz](https://njump.me/npub16zsllwrkrwt5emz2805vhjewj6nsjrw0ge0latyrn2jv5gxf5k0q5l92l7)

</details>

<details>

<summary>8. Nostr is for crypto-bros only </summary>

`crypto bros like experimental technology so they are the first adopters, but there are smaller communities talking about other topics and as they continue to grow things will get a lot more interesting` -[hzrd149](https://github.com/hzrd149/)

`Nope. Nostr is for Bitcoin bros only! Joking... Don't publish that. Nostr is for everyone, because everyone deserves the freedom to communicate. At this time, the portion of the population that recognizes the need for freedom of communication is also the same crowd that recognizes the need for freedom to transact. Someone has to be first to the social media revolution and right now, it's those that recognize the need for decentralization and censorship resistant communication such as freedom fighters and Bitcoiners. Nostr doesn't need Bitcoin and Bitcoin doesn't need Nostr, but they do do have a beautiful symbiotic relationship together. `-[Derek Ross](https://njump.me/npub18ams6ewn5aj2n3wt2qawzglx9mr4nzksxhvrdc4gzrecw7n5tvjqctp424)

`There is a significant overlap between a want for decentralization and bitcoiners` -[semisol](https://njump.me/npub12262qa4uhw7u8gdwlgmntqtv7aye8vdcmvszkqwgs0zchel6mz7s6cgrkj)

`Keep your voice down. The Bitcoiners will be really mad if they hear you calling them crypto-bros.` -[Matt Lorentz](https://njump.me/npub16zsllwrkrwt5emz2805vhjewj6nsjrw0ge0latyrn2jv5gxf5k0q5l92l7)


</details>

<details>

<summary>9. Is there a nostr wiki? </summary>

` There are some getting started guides, but I don't know of any nostr wiki yet` -[hzrd149](https://github.com/hzrd149/)

`There is a client called Wikifreedia, but there is no official Wiki. I've honestly thought about trying to create a Wiki for every client, then each client could link to the Wiki to have their users find help and support. I still think someone should build this. I don't have time. It's needed.`-[Derek Ross](https://njump.me/npub18ams6ewn5aj2n3wt2qawzglx9mr4nzksxhvrdc4gzrecw7n5tvjqctp424)

`No` -[semisol](https://njump.me/npub12262qa4uhw7u8gdwlgmntqtv7aye8vdcmvszkqwgs0zchel6mz7s6cgrkj)

`Yes! There is a decentralized wiki woven across the network with many ways to access it.
` -[Matt Lorentz](https://njump.me/npub16zsllwrkrwt5emz2805vhjewj6nsjrw0ge0latyrn2jv5gxf5k0q5l92l7)


</details>

<details>

<summary>10. Is there a SDK with some easy to customize demos? </summary>

` There are a ton of great SDKs and simple apps on https://github.com/aljazceru/awesome-nostr` -[hzrd149](https://github.com/hzrd149/)

`There is the Nostr Development Kit and other SDKs, but I am not aware of buildable demos.`-[Derek Ross](https://njump.me/npub18ams6ewn5aj2n3wt2qawzglx9mr4nzksxhvrdc4gzrecw7n5tvjqctp424)

`Yes, there are Nostr SDKs for most programming languages, and Nostr is famously easy to get started with.
` -[Matt Lorentz](https://njump.me/npub16zsllwrkrwt5emz2805vhjewj6nsjrw0ge0latyrn2jv5gxf5k0q5l92l7)



</details>

<details>

<summary>11. How can my community/website/product join nostr? </summary>

`There aren't many good community on boarding tools or guides yet but the best option currently would be to look into setting up a group relay` -[hzrd149](https://github.com/hzrd149/)

`Joining is easy. Where we're failing at is on-boarding. Only two applications have good onboarding - Damus and Primal. However, these applications are not good for businesses who often need to designate social media tasks to employees. They do not support Remote Signers or nsecbunkers. That aside, I would tell all of your community members to join nostr, follow one another, and start building your community by utilizing community tools such as Chachi, Flotilla, Zap.stream, or Nostr Nests.`-[Derek Ross](https://njump.me/npub18ams6ewn5aj2n3wt2qawzglx9mr4nzksxhvrdc4gzrecw7n5tvjqctp424)

`No one is focusing on onboarding, so tough luck` -[semisol](https://njump.me/npub12262qa4uhw7u8gdwlgmntqtv7aye8vdcmvszkqwgs0zchel6mz7s6cgrkj)

`It depends on what you are looking for. You could try downloading a client from nostr.com or nostr.net and asking there, but the best way would be to find a friend who knows the network. Feel free to tag me! You can search for my ID in pretty much any app: npub16zsllwrkrwt5emz2805vhjewj6nsjrw0ge0latyrn2jv5gxf5k0q5l92l7` -[Matt Lorentz](https://njump.me/npub16zsllwrkrwt5emz2805vhjewj6nsjrw0ge0latyrn2jv5gxf5k0q5l92l7)



</details>

<details>

<summary>12. This sounds like another VC funded "protocol" in Bluesky, or Farcaster. How does nostr protect from the ensuing enshittification? </summary>

` There is no nostr development team, so there is no one to say what can or cant be done on the protocol. developers are free to build and experiment however they like` -[hzrd149](https://github.com/hzrd149/)

`Nostr is not VC funded and is completely open. There is no central company. There is no central organization. There is no central development team. While some companies that utilize nostr may be VC funded, the protocol itself is not.`-[Derek Ross](https://njump.me/npub18ams6ewn5aj2n3wt2qawzglx9mr4nzksxhvrdc4gzrecw7n5tvjqctp424)

`12 and 13. It doesn’t unless the users care, which doesn’t seem to be true, as we are already seeing happening with several Nostr apps` -[semisol](https://njump.me/npub12262qa4uhw7u8gdwlgmntqtv7aye8vdcmvszkqwgs0zchel6mz7s6cgrkj)

`Unlike Bluesky and Forecaster there is no for-profit company behind the protocol, and it didn't originate from Silicon Valley. In fact there is no formal organization, foundation, non-profit, or anything controlling the protocol. It's formed and run by the people using it.` -[Matt Lorentz](https://njump.me/npub16zsllwrkrwt5emz2805vhjewj6nsjrw0ge0latyrn2jv5gxf5k0q5l92l7)


</details>

<details>

<summary>13. How does nostr elude capture by a well funded VC company? </summary>

`I don't know, I guess we will see when the time comes` -[hzrd149](https://github.com/hzrd149/)

`User choice. If a large company decides to build upon nostr, that is fine. Users will have to choice to migrate to another application with ese if they don't like the direction that said company is going or features that they're implementing.`-[Derek Ross](https://njump.me/npub18ams6ewn5aj2n3wt2qawzglx9mr4nzksxhvrdc4gzrecw7n5tvjqctp424)

`Help humanity organize well-enough to overthrow capitalism? Just kidding, sort of. I think the right way to protect Nostr is to treat it as a public commons, Elinor Ostrom-style. Her eight principles for a healthy commons do a great job explaining what it takes, but a diverse set of apps, business, and users is a good start.` -[Matt Lorentz](https://njump.me/npub16zsllwrkrwt5emz2805vhjewj6nsjrw0ge0latyrn2jv5gxf5k0q5l92l7)



</details>

<details>

<summary>14. What is the difference between nostr and ActivityPub, Mastodon, Fediverse (via FOSDEM)? </summary>

`ActivityPub, Mastodon, Fediverse social identity registration is tied to a server, and is considered an account. That is, the AP server admin can rugpull, ban, or censor said identity. On nostr, relay operators cannot singularly ban or rugpull an identity. While a relay admin can ban an npub from publishing on a relay, there are many other relays to choose from and write to. Collusion between all (hundreds or thousands) of relay admins is extremely unlikely, if at all possible.` -[elsat](https://njump.me/npub1zafcms4xya5ap9zr7xxr0jlrtrattwlesytn2s42030lzu0dwlzqpd26k5)




</details>

<details>

<summary>15. How can IOT developers add nostr to MQTT & Meshtastic integrations (via FOSDEM)? </summary>

`See @ksedgwic work on noshtastic https://github.com/ksedgwic/noshtastic` -[elsat](https://njump.me/npub1zafcms4xya5ap9zr7xxr0jlrtrattwlesytn2s42030lzu0dwlzqpd26k5)





</details>


   <details>

<summary>16. What is the current state of MLS on Nostr (via FOSDEM)? </summary>

`It works! As far as I'm aware, Nostr is the first truly decentralized implementation of MLS. I've been working to bring MLS messaging to Nostr for the last 9 months and have built a messaging client (called White Noise - https://github.com/erskingardner/whitenoise) and several libraries that will make it easier for other developers to implement MLS messaging into their own clients. Feel free to hit me up on Nostr to ask any questions.` -[JeffG](https://njump.me/npub1zuuajd7u3sx8xu92yav9jwxpr839cs0kc3q6t56vd5u9q033xmhsk6c2uc)

</details>

  <details>

<summary>17. Where can I listen to a nostr for devs talk? </summary>

`FOSDEM talk by Constant` https://njump.me/nevent1qqspj60z02pr2suafcsdc6dqf4vsvxkg9pmg59x8sgu3v0z6t0ztftgpp4mhxue69uhkummn9ekx7mqpzamhxue69uhhyetvv9ujuurvv438xarj9e3k7mgpzfmhxue69uhk7enxvd5xz6tw9ec82cspr9mhxue69uhkummnw3ezu7n9vfjkget99e3kcmm4vst8au8y -[elsat](https://njump.me/npub1zafcms4xya5ap9zr7xxr0jlrtrattwlesytn2s42030lzu0dwlzqpd26k5)

</details>
