IETF Last Call Comments

This file compiles the main comments from the IETF Last Call.



# Comment

Section 2, paragraph 1, refers to "best way to detect ..."  Please reword to remove "best" 
[High reliability might also utilize traceable time, authenticated time exchanges, local stratum ones, etc.]

## Who
- Steven Sommars

## Resolution 
agree

Changing "Best Way.... is" to "Important ways ... are"

# Comment

Section 4.1.  The first section in this section asserts that all NTP implementation perform intersection, clustering, and combining..
According to https://chrony.tuxfamily.org/comparison.html, Chrony does not do clustering.
Suggest changing to "... sophisticated algorithms such as intersection, clustering and combining".

Maybe use "all conforming NTP implementations", so chrony would be non-conforming. I think the clustering algorithm is part of the NTP specification.

## Who 
- Steven Sommars
- Ulrich Windl

## Resolution
agree

replace "An NTP implementation (as opposed to an SNTP implementation) takes" with 

"An NTP implementation that supports the selection algorithms in RFC5905 "

-- found typo: "combing" should be "combining"
 
-- TBD: Change the wording in this paragraph to emphasize the usefulness of multiple sources of time up front?


# Comment

Section 4.1, next to last paragraph.  Change "During the leap second of June of 2015, " to "For several hours before and after the June 2015 leap second,"

## Who 
- Steven Sommars

## Resolution
agree as-is


# Comment

Section 4.2. Comment.  It may be difficult to put this into practice if the stratum 1 servers reside in other organizations

## Who 
- Steven Sommars

## Resolution
agree 
add to the end of 1st paragraph: 

"Operators need to be aware of this, even if the stratum 1 servers they use are not under their direct control."


# Comment

Section 4.3,  Most NTP servers (90%+ in my tests) block remote mode 6 messages.
Important NTP implementations (e.g., chrony) do not implement the mode 6 commands.  
Please mention these limitations of mode 6.

## Who 
- Steven Sommars

## Resolution
agree
We feel that the text is specific in saying that "some" NTP implementation use these messages, and that we state why they are not fit for use everyehere. 
But we should explicitly state the reality that publically accessible servers block them.

Add after "Abuse Vector"

"For this reason, it is recommended that publicly-facing NTP servers should block mode 6 queries from outside their organization."

# Comment

Section 4.4   The paragraph mentioning ntp-4.2.8p6 and ntp.keys is too implementation specific.  Please remove it.

## Who 
- Steven Sommars

## Resolution
agree -- was copied to appendix A.1.3 but never removed here

# Comment

Section 4.6.1   There are traps aplenty when leap smearing is in effect.  E.g., how does a client determine whether an upstream source is, or is not smeared?
The best current practice for leap smearing is to not use it.

## Who 
- Steven Sommars

## Resolution
Disagree, but will clarify
Not everyone agrees that leap smearing should not be used, but we are specific in saying it should now be used on public servers, where operators expect UTC.

perhaps more explanation is required. After the sentence that begins "Leap Smearing MUST NOT", add:
At this time, there is no standardized way for a client to detect if a server is using leap smearing or if it is not.

# Comment

section 6.1,   The protections should be done by the individual client software(e.g., ntpd) not by the host.  

## Who 
- Steven Sommars

## Resolution

agree

TBD -- check this -- The intention of the text here is that "hosts" means "ntp clients and/or servers" in general. Text will be updated accordingly.

# Comment

Overall: 
- Language to vague. 
- Lack of Requirements Language. /TP
- Security Considerations weak. /TP
- The text is too colloquial and imprecise /JT
- Tom Petch's suggestions are useful - there are several areas where the language could be tightened up and tidied, and it would help to have an -08 version with not just this taken on board, but also a general stylistic edit because the language is genuinely too colloquial if not a bit sloppy in places. /NH
- I found the tone a little unusual (as other reviewers have commented on) as did one of the people who operates large systems but doesn't regularly participate in the IETF that I asked to skim this. That said, I didn't find it's lack of precision in places to be dangerous. If there's appetite to improve it, please do, but I think the world would be better with this document published as is than with no document published at all. /RS

## Who 
- Tom Petch
- Joe Touch
- Nick Hilliard
- Robert Sparks

## Resolution

TBD

# Comment

Section 5 references RFC7384,
'profound threat analysis for time synchronization protocols '.  Yes,
but it is ironic that that RFC, detailed, thorough, useful, is only
Informational; and it is not mentioned in this, the section on Security
Considerations.

## Who 
- Tom Petch

## Resolution

Agreed

Add to Section 11 between paragraphs 1 and 2:

There are several general threats to time synchrnoization protocols which are discussed in RFC7384.


# Comment

Abstract
RFC 5905 [RFC5905].
looks like a reference which is not ok for an Abstract which needs to be
plain text.

## Who 
- Tom Petch

## Resolution

Agreed -- remove the reference from the abstract

# Comment


1.1.  Requirements Language out of date no RFC8174

## Who 
- Tom Petch

## Resolution

Agreed -- We will update Section 1.1 according to the proper boilerplate language.

# Comment

3.1
BCP38 Info page [1] .
I did not immediately recognise [1] as a reference to a URL.

## Who 
- Tom Petch

## Resolution
Agreed

Change to "More information is available at the BCP38 Info Web page" to make clear that it is a URL.


# Comment

4.1
opposed to an SNTP implementation
expansion would be helpful

this section in general lacks any detail of 'how'.  What is agreement,
between two sources?  How do I converge three sources?  I look to a BCP for advice
on such matters.

Many of the recommendations lack rationale - e.g., simply choosing 4 time servers isn’t sufficient to help ensure reliable, accurate results unless they are chosen to reduce the number of shared “ancestor” servers. 

## Who 
- Tom Petch
- Joe Touch 

## Resolution
Agree in part, will make changes

The "how" is defined in RFC 5905. The operator has to decide how many time sources he/she is using.

The point about "ancestor" servers is well taken. Add:
"These sources must be truly redundant and derive their time from separate sources."



# Commment

4.2
There is a general principle behind this that I would like to see
stated, namely to ensure that multiple sources are really independent.
I learnt this when I read about Apollo moon shots, but have seen it
ignored many times since.  You have to work hard to track back to the
details of the technology in use to find out if there is really more
than one code base, or chip set, or... in use.  Where security
depends on such matters, you really need to do that to ensure you have
independence. Appendix A suggests that there is but one code base.

## Who 
- Tom Petch

## Resolution
Agree. Change "diversity of sources" to "diversity of sources with independant implementations".

After "may have the same bugs", add "Even devices from different vendors may not be truly independant if they share common elements." 
Then, we can strike "regardless of whether ... different vendors", because that will be redundant.

Denis likes that last line in the comment. After "application software bugs", add 
"When having the correct time is of critical importance, it's ultimately up to operators to ensure that their sources are sufficiently independant."

Also, the original intention of this BCP was that we would get subnissions relating to multiple implementations, but in the end we only received information relating to the NTF implementation.


# Comment

4.4
its syslog shows 
Is this a recommendation to use the 'syslog' protocol as opposed to
YANG:-)  Elsewhere, you use system logs which I think better.

I think too that there is a general point that is missing that these
systems need error logging, need (remote) monitoring, else ... well, what is the
threat?  what is the mitigation?

broadcast client sounds like a client that broadcasts rather than one that receives
broadcasts.

## Who 
- Tom Petch

## Resolution
Agree
change "syslog" to "system logs" globally

change "NTP Implementation's" to "NTP Servers" to emphasize that you may use remote monitoring capabilities outside of the NTP implementation.

TBD mitigation for each scenario presented

"broadcast client" to "client in broadcast mode"



# Comment

4.6.1
using a leap-smear can cause your reported time to be "legally
indefensible sounds like a SHOULD NOT if this is a BCP /TP

The section on leap smearing fails to underscore the key issue - that NTP is intended to provide a UTC time scale, and leap smeared-time is NOT UTC time, which then undermines the ability to compare NTP time values in a single time scale - which then can impact security protocols, financial transactions, etc. The issue is more than whether public servers should smear; the issue is whether smearing defeats the very definition of NTP as a protocol. BCP should indicate that smearing MUST NOT be used in an NTP server using the assigned NTP port number, period. Frankly, it was a mistake that its support was ever added to the NTP codebase. The only alternative would be for NTP to be extended to report “smeared time” as a *distinct* time scale, which it currently does not. The issue if multiple time scales is discussed in a draft I have been working on, FWIW (draft-touch-time). /JT

On the leap smearing issue, some people are going to do it, and most people won't.  It's not useful for the IETF to pretend it doesn't happen or castigate people for using it; we don't run other people's systems and don't have to deal with their arrays of embedded devices which are locked to a specific kernel version which crashes every time ntp jumps forward by one second.  Also, we have no real visibility into what would happen to any specific organisation if a negative leap second were declared, but I suspect a lot of trouble, and a lot more trouble than if leap smearing were implemented within specific admin domains. Anyway, rant over - it's fine to say "SHOULD NOT" within your own admin domain, and "MUST NOT" for interfaces to others, and have a discussion about the mechanism in general (which is mostly there). /NH

## Who 
- Tom Petch
- Joe Touch

## Resolution

Disagree, but we still make clarifications.

there are organizations that will use this , and so the BCP should reflect that reality. We discourage its use on public servers.

We can add "Any use of leap-smearing servers should be limited to within a single well-controlled local environment." to the begging of the paragraph that starts "Leap Smearing MUST NOT be used"


# Comment

5.1
the MAC may always be based on an MD5 hash,
MD5 is regarded as too weak in many contexts; does that apply here?

## Who 
- Tom Petch

## Resolution
agree

update based on mac-for-NTP document, add the right reference that will be changed before publication

MD5 is in the process of being deprecated, but current implementations still provide it. Use AES when implementations support it.

# Comment

Generally, is there any difference between IPv4 and IPv6 here?  IP
addresses are
often mentioned but no mention of different versions.  RFC4786, e.g., is
explicit that it covers both.

## Who 
- Tom Petch

## Resolution
agree

TBD -- Make sure that language regarding IPV4 vs IPV6 in Anycast agrees with RFC.

# Comment

Appendix A

/specific to various implementation of RFC 5905./
specific to various implementations of RFC 5905./
except that the advice seems to be specific to ntpd and not
apply to any other implementation

## Who 
- Tom Petch

## Resolution
agree

Since there are no other implementations currently with appendixes, we will refactor to make Appendix A devoted solely to the NTF implementation. In the event this BCP is updated with information from different implementations, they can have their own appendix.

# Comment

IANA Requirements

## Who 
- Sabrina Tanamal

## Resolution


# Comment

The questions that Joe raises about its suitability for purpose comes down to the document's intended audience.  There is no doubt that the document is of questionable suitability for organisations or people who have a hard requirement for high precision, guaranteed quality timekeeping, e.g. reference or legal timekeeping.  However, there is equally little doubt that if most people who ran NTP services adhered to most of the recommendations listed in the draft, that NTP quality in the world would increase overall, probably dramatically.  My understanding is that the term "BCP" refers to the latter category of people rather than to the former, i.e. "best common practice" rather than "practice which which is provably consistent with a carefully defined and very specific set of inputs with consequently expected output results".
...
Conversely, what would be useful would be a clear statement in the document about its intended audience, i.e. where the recommendations in this draft are relevant, and more importantly, where they are not suitable for purpose.

## Resolution
agree
modify the abstract

NTP has been widely used since its initial publication, and is currently on its fourth version.  This documentation is a collection of Best Practices for general operation of time servers on the Internet from across the NTP community.

Add to the introduction a statement about the intended audience -- operators and maintainers of NTP servers and clients on the Internet.



# Comment

The write-up states that type of RFC being requested is 
"Informational".  However, the request received (please see above) 
states that the document is intended to be a BCP.  Section 1 states 
that this documentation is a collection of best practices from the 
NTP community.  As a comment about overall document quality, the 
draft needs some work as it looks like a collection of informal 
advice which a person might give instead of advice which has been 
formalized.  It is unclear whether some of the URLs in the draft are 
acknowledgments of past work or advertisements.

## Who
- S. Moonesamy

## Resolution
agree -- general changes need to be made to make the language stronger.

# Comment

Section 3 is about general network security best practices.  The 
section mentions BCP 38 and explains that it has been approved in 
2000.  There is a document from 2008 [1, https://www.ripe.net/publications/docs/ripe-432 ] about it.  Is BCP 38 
well-deployed nowadays?

## Who
- S. Moonesamy

## Resolution
TBD

# Comment

In Section 4.1:

   "Interested readers should read"

Have the authors read the IETF RFC about uncapitalized letters?  Does 
it apply for the above?

## Who
- S. Moonesamy

## Resolution
Agreed
"Those interested are advised to read"


# Comment

Section 4.1 provides some examples of use of time sources.  It sounds 
like the draft is trying to explain different "use cases" instead of 
specifying a best practice.

## Who
- S. Moonesamy

## Resolution
TBD

# Comment

Section 4.2 contains some questions about diversity.  It attempts to 
highlight the issues in terms of "are you doing this" and points out 
to a possible issue.

## Who
- S. Moonesamy

## Resolution
TBD

# Comment

Section 4.6 states that "The IETF maintains a leap second list".  How 
is that list updated by the IETF?

## Resolution
reference RFC for timezone database



# Comment

Section 6 has the following: "but these concepts may (or may not) 
have been mitigate".  How are concepts mitigated?

## Who
- S. Moonesamy

## Resolution

agree
change "concepts" to "issues"


# Comment

Section 5 describes available NTP security mechanisms, and then section 6 describes "NTP Security Best Practices". I went back and forth several times, confused by the fact that section 5 includes recommendations as well as brief descriptions of the mechanisms. I think giving a separate overview of the existing security mechanisms is a good idea, but I'd suggest using this section for defining what's available, and moving the recommendations into new subsections of section 6. 

The current draft says, 

   ... The calculation of                                       
   the MAC may always be based on an MD5 hash, and an AES-128-CMAC hash
   is expected to soon be allowed as well.  If the NTP daemon is built
   against an OpenSSL library, NTP can also base the calculation of the
   MAC upon any other digest algorithm supported by each side's OpenSSL
   library. 

Shouldn't this doc be recommending use of something stronger than the (non-HMAC) MD5 hash-based solutions given that stronger solutions are available? If both sides can choose from whatever is supported by OpenSSL, then HMAC and/or CMAC algorithms seem like much better choices.

## Who
- Scott G. Kelly

## Resolution

TBD

# Comment

Another remark on "The NTP Control Messages responses are much larger than the
   corresponding queries.  Thus, they can be abused in high-bandwidth
   DDoS attacks.  To provide protection for such abuse NTP server
   operators should deploy ingress filtering BCP 38 [RFC2827].": If I understood it correctly, the ingress filtering has to be done by the attacker's ISP (where the bad packet enters the net). At the destination you possibly cannot do ingress filtering unless you want to disallow any packets outside the current subnet or the company's nets. If I misunderstood the advice, others may do as well, so please elaborate what operators should actually do.

## Who
- Ulrich Windl

## Resolution
We note that BCP38 advises that corporate network administrators should implement filtering to make sure that their network cannot be the source of spoofed packets. So while you are correct that it is most useful at the ISP, it does offer benefits for corporate networks. We can clarify that "all large corporate networks" can benefit from this to reduce the scope a bit. 

# Comment

On "If a system is a broadcast client and its syslog shows that it is
   receiving "early" time messages from its server, that is an
   indication that somebody may be forging packets from a broadcast
   server.":
Maybe elaborate on use of authentication for broadcast clients: Should use of (strong) authentication keys be recommended?

## Who
- Ulrich Windl

## Resolution
This section recommends to use broadcast in trusted networks only, so we make no recommendation on encryption here.

# Comment

On "If a system is using broadcast mode and is running ntp-4.2.8p6 or
   later, use the 4th field of the ntp.keys file to specify the IPs of
   machines that are allowed to serve time to the group.":
I think it's too specific: Why not state "If your NTP client (it's describing a client, right?) allows to filter valid time sources, please use it (for eaxmple ntp-4.2.8p6 allows to put valid IP... in the 4th field of ..."

## Who
- Ulrich Windl

## Resolution
This text has been moved to the ntpd appendix, where the specificity is more appropriate.


# Comment

Maybe rename "Using Pool Servers" to "Selecting Servers to use", because it's more general than just pool servers.
I would prefix the paragraph starting with "The NTP pool project is a group ..." with a general explanation that some NTP software is able to process a DNS response for a server name containing multiple IP addresses of different servers to pick some of those servers as time sources. THEN proceed explaining the NTP pool server project. Maybe also emphasize that "ingress filtering should not block pool servers" if they are intended to be used.

## Who
- Ulrich Windl

## Resolution
We would prefer to keep the original title, because we feel the pool project is an important service for the community to know about. The link to the pool project has a good explanation of the DNS activity that does not need to be duplicated here.  


# Comment

I would combine these two paragraphs: "If you are a vendor who wishes to provide time service to your
   customers or clients, consider joining the pool and providing a
   "vendor zone" through the pool project." and "If you would like to contribute a server with a static IP address and
   a permanent Internet connection to the pool, please consult the
   instructions at http://www.pool.ntp.org/en/join.html [3] .".

   ## Who
- Ulrich Windl

## Resolution
We eliminated the second paragraph.

# Comment

You could add "up to twice a year" at the end of: "UTC is kept in agreement with the astronomical time UT1 [4] to within
   +/- 0.9 seconds by the insertion (or possibly a deletion) of a leap
   second."

## Who
- Ulrich Windl

## Resolution
We don't think that change is necessary.

# Comment 

I would change "and the protocol has the capability to broadcast leap second information" to "and the protocol has the capability to broadcast and process leap second information".

## Who
- Ulrich Windl

## Resolution
I personally think that the protocol will broadcast the leap second information, and the clients receiving the protocol messages would process the information. So I don't think the change is necessary.

# Comment

Change "Note well that NTPv4 allows a maximum poll interval of 17, or 131,072 seconds, which is longer than a day." to "Note well that NTPv4's longest polling interval exceeds one day and thus a leap second announcement may be missed."

## Who
- Ulrich Windl

## Resolution

Agreed

# Comment

Change "keys have to be exchanged securely by external
   means." to "keys have to be exchanged securely by external
   means, and they have to be protected from disclosure."

## Who
- Ulrich Windl

## Resolution

Agreed


# Comment

I would swap the two sentences "NTP does not provide a mechanism to automatically
   refresh the applied keys.  It is therefore recommended that the
   participants periodically agree on a fresh key.". (Its recommended to refresh keys periodically, but (unfortunately) NTP dies not assist you in doing so (excpet from "readkeys").

## Who
- Ulrich Windl

## Resolution

Personally I like how that language flows a bit better, we changed to:
"It is recommended that participants agree to refresh keys periodically. 
However, NTP does not provide a mechanism to assist in doing so."

# Comment

On "Some implementations store the key in clear text.": Which do not?
## Who
- Ulrich Windl

## Resolution
I don't know of any, but we can't guarantee that future implementation won't. In any case, we don't think the text needs to change. 

# Comment
I would re-word "An NTP client establishes a protected association by appending the
   key to the server statement in its configuration file." as "Authentication is requested by the client by specifying a key and adding a valid MAC to the request. This happens when a key number is specified with the server configuration (value and type of the key are read from a secret key file)."

I'd replace "Autokey was designed in 2003 to provide a means for clients to
   authenticate servers." with "Autokey was designed in 2003 to provide automatic key selection and updates for clients to
   authenticate servers."

## Who
- Ulrich Windl

## Resolution
Dieter recommends "Autokey was specified in 2010 to provide automated key management and authentication of NTP servers”. 

# Comment

The sentence "As such, access control should be used to limit the exposure of this
   information to inappropriate third parties." is quite confusing, because when a server serves a client, it will provide such information. Despite from updating the software, the operator can do little about that.

## Who
- Ulrich Windl

## Resolution

We will reword to match language that was changed for the "control messages" section:
"As such, mechanisms outside of the NTP protocol, such as Access Control Lists, should be used to limit the exposure of this information to allowed IP addresses, and keep it from remote attackers not on the list.

# Comment


On "Prevent the NTP daemon from taking time steps that set the clock
      to a time earlier than the compile date of the NTP daemon.": This would be a recommendation to an implementer, right? The operator cannot do much about it, I guess.

## Who
- Ulrich Windl

## Resolution

We will clarify this for implementors.


# Comment

Before the paragraph on "Kiss-o'-Death (KoD)" the concept should be explained in one sentence. (Like "KoD is a mechanism for a server to tell a client to stop polling it (that fast).)
And: The heading "KISS Packets" should be "Kiss-of-Death Packets". Generally I would remove some of the details that describe the implementation and are not related to actual recommendations.

## Who
- Ulrich Windl

## Resolution
We feel that the introductory sentence "The "Kiss-o'-Death" (KoD) packet is a rate limiting mechanism where a server can tell a misbehaving client to "back off" its query rate." is a clear enough explanation. But we agree that the heading can be changed.

# Comment

In 6.6 explain that a passive peer receives time messages from a server that has not been configured at the client.

## Who
- Ulrich Windl

## Resolution
DR: Can he explain this further?

# Comment

For 7. maybe note that embedded devices sometimes do not have a battery-buffered clock, so using NTP successfully to set the time may be critical for proper operation.

## Who
- Ulrich Windl

## Resolution
Excellent point, thanks!

# Comment

Maybe add: "Avoid devices that use a fixed built-in configuration for NTP" (meaning: YOu cannot configure its servers or security).

Maybe also differ between embedded clients and embedded servers...

## Who
- Ulrich Windl

## Resolution
We feel this advice can be difficult for some of these new small IoT devices, we prefer to put the onus on vendors to be responsible.

# Comment

For 8.: Maybe clarify the difference between "manycast", "anycast" and "multicast" (not to talk abut broadcast).

## Who
- Ulrich Windl

## Resolution

We feel that Manycast and Multicast are already covered in RFC 5905. 

