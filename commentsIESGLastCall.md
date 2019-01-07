IESG Comments

This file compiles comments from the IESG Telechat.

# Comment

One of the changes was to be more specific with actors - many uses of "you" or
"your" were replaced with "the operator" for example. But this wasn't done
throughout the document ("you" and "your" still appear frequently), and in at
least one place the change caused a sentence to stop making sense: "If the time
on your network has to be correct close to 100% of the time, then even if you
are using a satellite-based system, operators need to plan for those rare
instances when the system is unavailable (or wrong!)."


## Who
Robert Sparks

## Resolution
We're revisiting the text one more time to clarify these. 

# Comment
2119 references
The changes also included using 2119 keywords much more often. Unfortunately
many of the new uses are not appropriate. "Vendors MUST" and several instances
of "It is RECOMMENDED" are particularly jarring. Moving 2119 to be an
Informational reference is also incorrect if you are going to use those terms
in this document.

## Who
Robert Sparks

## Resolution
We're revisiting this also for the consistency of application.

###

# Comment (Discuss)

RFC 2119 and RFC 8174 need to be normative references.

## Who
Alissa Cooper

## Resolution
Agree
DS: ok


# Comment

Section 2.1:

s/BCP 38 [RFC2827] was approved/BCP 38 [RFC2827] was published/ (presumably the
approval was not the seminal thing)

## Who
Alissa Cooper

## Resolution
Agree

# Comment
Section 3.2:

"If time sources do not generally agree, find out the cause and either
  correct the problems or stop using defective servers."

It seems odd to frame this as a directive, especially in a paragraph where the
subject is made explicit ("operators"). I think this would make more sense if
it said "operators should find out" or "operators ought to find out."


## Who
Alissa Cooper

## Resolution
How about “operators are encouraged to find out why”


# Comment
Section 3.3:

Please fix the sentence highlighted by the Gen-ART reviewer.


## Who
Alissa Cooper

## Resolution
Change to:
Depending on the application requirements, operators may need to consider backup scenarios in the rare circumstance when the satellite system is faulty or unavailable.

# Comment
Section 3.4:

"To provide protection for such abuse NTP server
  operators on large networks SHOULD deploy ingress filtering in
  accordance with BCP 38 [RFC2827]."

Why is this recommendation limited to large networks, whereas the normative
recommendation to do ingress and egress filtering in Section 2.1 applies to
ISPs of any size?


## Who
Alissa Cooper

## Resolution
Simply because we are using the works “networks” here more broadly than ISP’s. We considered ISP’s to be large networks by definition. We can use the same language here as in Section 2.1: ISPs and large corporate networks.

# Comment

Section 3.6:

I agree with the Gen-ART reviewer that the use of "you" is inappropriate here
and should be replaced by a noun (e.g., "operators").


## Who
Alissa Cooper

## Resolution
We’re revisiting the text one more time to clarify these. 

# Comment
Section 4.1:

"Therefore, for each association, keys SHOULD be exchanged securely by external
  means, and they SHOULD be protected from disclosure."

I recognize that this is outside the bounds of the protocol, but if this
document is a BCP that is going to make these normative recommendations for
what they're worth, shouldn't they be MUSTs? If not, what are the exceptional
cases where the exchange of these keys shouldn't be secure and confidential?

Section 4.2:

Same question as Section 4.1.


## Who
Alissa Cooper

## Resolution

We did discuss this, and decided that since there is no formally defined approach to share these keys outside the protocol, that it might be unreasonable to make this a MUST, while leaving the process of how to do this undefined


# Comment
Section 5:

Same comment as Section 3.2. The subject to which the directive is being given
should be named.


## Who
Alissa Cooper

## Resolution
Change to “Contact the maintainers of the relevant implementation for more information.”

# Comment
Section 5.2:

"It is likely to become the default behavior in other
      systems as they migrate legacy init scripts to process
      supervisors such as systemd."

For posterity it may be better to say, "At the time of this writing, it appears
likely to ..."


## Who
Alissa Cooper

## Resolution
Agree


# Comment

"Operators SHOULD be aware that when operating with the above two
  conditions, the panic threshold offers no protection from attacks."

I don't think it's appropriate to use normative language about being aware.


## Who
Alissa Cooper

## Resolution
DR: I remember thinking about this one in particular. I thought that it as needed to keep this normative to balance the second normative statement in the document. Perhaps I was wrong, though. I can change it to “Operators need to be aware” and keep the second statement of  “operators SHOULD NOT ignore the panic threshold” intact.

# Comment
Section 6.1:

"Vendors of embedded devices MUST pay attention to the current state
  of protocol security issues and bugs in their chosen implementation."

Same comment as 5.2, it's inappropriate to normatively require paying attention.


## Who
Alissa Cooper

## Resolution
Will use “are advised to”

# Comment
Section 6.2.1:

"For more information, visit ..."

Same comment as 3.2 and 5 -- this sentence needs a subject.


## Who
Alissa Cooper

## Resolution
Will use "Details are available at...."

###

# Comment
§1:

This document also contains information for protocol implementors who
want to develop their own RFC 5905 compliant implementations.

Nit: "RFC-5909-compliant" or "[RFC5909]-compliant".


## Who
Adam Roach

## Resolution
Agree


# Comment
§2.1:

UDP-based protocols such as NTP are generally more
susceptible to spoofing attacks then other connection-oriented
protocols.

Nit: "...than..."

The use of "other" implies that NTP is a connection-oriented protocol, which
doesn't match my understanding. I think you want to simply remove "other".


## Who
Adam Roach

## Resolution
Agree on both points

# Comment
§3:

This section provides Best Practices for NTP configuration and
operation.  Best Practices that are specific to the NTF
implementation are compiled in Appendix A.

Please expand "NTF" on first use.


## Who
Adam Roach

## Resolution
Agree


# Comment
§4.2:

Maybe cite RFC 5906 here?


## Who
Adam Roach

## Resolution
We specifically did not want to cite RFC 5906 here as we are advising that people not use it. In retrospect, we will add it as an informative reference.

# Comment
§5.2:

Some of the mitigations in here seem specific to one implementation of an NTP
daemon (e.g., reference to "minsane" and "minclock" parameters and to the
"ntp.conf" file). As the remainder of the advice in the document to this point
appears to be generic, I propose that these practices either be described in an
implementation-neutral way; or, if that is not possible, moved to Appendix A.


## Who
Adam Roach

## Resolution
“Increase the minimum number of servers required before the NTP client adjusts the system clock. This will make the NTP client wait until enough trusted sources of time agree before declaring the time to be correct.”


# Comment
§7:

With anycast, a single IP address is assigned to multiple interfaces,
and routers direct packets to the closest active interface.

This is kind of a confusing use of the word "interface" -- a simple reading of
this sentence is that you have a single server with, say, multiple network
cards, and the router is deciding which of those cards to send a packet to.
If I didn't already know the meaning of "anycast," this description would
leave me scratching my head.  Perhaps use the term "node" or "server" instead.


## Who
Adam Roach

## Resolution
Agree -- use "Servers"

# Comment
§7:

As
anycast servers may arbitrarily enter and leave the network, the
server a particular client is connected to may change.

It might be worth noting in the document that these changes can happen due to
factors other than NTP servers coming online and offline, such as changes in
routing tables.  In more extreme cases -- e.g., flapping routes --  this could
result in clients switching between two different servers rapidly.


## Who
Adam Roach

## Resolution
Change to:
As anycast servers enter and leave the network, or the network topology changes, the server a particular client is connected to may change. This may cause a small shift in time from the perspective of the client when the server it is connected to changes.  In extreme cases where the network topology is changing rapidly, this could cause the server connection with a client to rapidly change as well, which can lead to larger time inaccuracies. It is RECOMMENDED that anycast only be deployed in environments where this behavior can be tolerated.


# Comment
§A.7:

(This is easy to do
because the origin timestamp on broadcast mode packets is not
validated by the client.  By contrast, client/server and symmetric
modes do require origin timestamp validation, making it more
difficult to spoof packets [CCR16].

Nit: This is missing a closing parenthesis.


## Who
Adam Roach

## Resolution
Agreed

# Comment
I understand every sentence in this text

 Many network security mechanisms rely on time as part of their
  operation.  If attackers can spoof the time, they may be able to
  bypass or neutralize other security elements.  For example, incorrect
  time can disrupt the ability to reconcile logfile entries on the
  affected system with events on other systems.  An application which
  is secure today could be insecure tomorrow once an unknown bug (or a
  known behavior) is exploited in the right way.  Even our definition
  of what is secure has evolved over the years, so code which was
  considered secure when it was written may turn out to be insecure
  after some time.

but don't understand how

  An application which
  is secure today could be insecure tomorrow once an unknown bug (or a
  known behavior) is exploited in the right way.  Even our definition
  of what is secure has evolved over the years, so code which was
  considered secure when it was written may turn out to be insecure
  after some time.

relates to an attack on NTP-provided time. Could you help me understand how
this is tied together?

###


## Who
Spencer Dawkins

## Resolution
After reviewing it, we now think the second part isn’t necessary anymore and we’ll take it out.

# Comment
Is "users" the right term in

3.6.  Using Pool Servers

  It only takes a small amount of bandwidth and system resources to
  synchronize one NTP client, but NTP servers that can service tens of
  thousands of clients take more resources to run.  Users who want to
  synchronize their computers SHOULD only synchronize to servers that
  they have permission to use.

? If I'm a user, I'm not thinking I've ever consciously chosen an NTP server.

You might consider moving that paragraph lower in 3.6 - the section is about
using pool servers, but the explanation about pool servers is in the second
paragraph.


## Who
Spencer Dawkins

## Resolution
We will clarify that “Network operators and advanced users who want to synchronize the computers on their networks” really need to pay attention.

# Comment
Is the choice of lower case "should" in

3.7.1.  Leap Smearing

  Some NTP installations make use of a technique called Leap Smearing.
  With this method, instead of introducing an extra second (or
  eliminating a second) on a leap second event, NTP time will be slewed
  in small increments over a comparably large window of time (called
  the smear interval) around the leap second event.  The smear interval
  should be large enough to make the rate that the time is slewed
  small,

intentional? It seemed close enough to some of the SHOULDs in this document
that I wanted to ask ...


## Who
Spencer Dawkins

## Resolution
Yes, it’s intentional. Leap smearing is a bit controversial, and the only guidance we wanted to offer is when it should not be used. 

# Comment
Is it obvious how a system administrator would detect a mixture of smeared and
non-smeared servers, as in

 System Administrators are advised to be aware of impending leap
  seconds and how the servers (inside and outside their organization)
  they are using deal with them.  Individual clients MUST NOT be
  configured to use a mixture of smeared and non-smeared servers.  If a
  client uses smeared servers, the servers it uses must all have the
  same leap smear configuration.

? I'm asking for the case where you carefully choose your servers so they
aren't mixed, but you are using servers you don't control, and the server
administrator changes the server behavior.


## Who
Spencer Dawkins

## Resolution
We struggled with this a bit, as there’s no standard way to detect a leap smear. There is some work being done on this, but nothing is far enough along to make a formal recommendation. We recommend not to use leap smear on public facing servers, but we know that people do it anyway. We are taking the point of view that if we inform operators that this may happen, they can ask the questions they need to ask ahead of time (or have a better clue what might be going on if one of their upstream servers disagrees with the others over the leap second.)


# Comment
I don't think

 Operators SHOULD be aware that when operating with the above two
  conditions, the panic threshold offers no protection from attacks.

needs BCP14 requirements language. When would operators make an informed
decision to be unaware?


## Who
Spencer Dawkins

## Resolution
Changed to "need to be aware"

# Comment
In this text,

 In addition, implementations SHOULD prevent the NTP daemon from
  taking time steps that set the clock to a time earlier than the
  compile date of the NTP daemon.

it would be helpful to me, to explain why this requirement is included. I can
imagine a couple of reasons, but I'm guessing.


## Who
Spencer Dawkins

## Resolution
We included it as a simple check against setting the time way too early that probably shouldn’t impact users. But as you state, there may be other reasons.



# Comment

I wonder if the SUIT working group has any drafts that are stable enough to be
used as an informative reference in Section 6.1, "Updating Embedded Devices".


## Who
Spencer Dawkins

## Resolution

I don't think anything there looks stable right now, but that looks like a good group to follow. Thanks for the tip!

###

# Comment (Discuss)
I see that Ben has already asked about the SHOULDs (vs. MUSTS) for secure
key exchange and prevention from disclosure, in Section 4.1, but I will
make that a Discuss point.  If these are to remain SHOULD, we should say 
something about in what case(s) MUST would not be appropriate.

## Who
Benjamin Kaduk 

## Resolution

DR: Our original motivation for keeping these as "SHOULD" was that there was no
formal recommendation we could point users to on how to secure these keys. But we have
received enough feedback from the reviewers here that we will change these to "MUST"s.
DS: OK. Adjusted the draft accordingly.


# Comment (Discuss)

I'm also concerned that there is too much intermingling of general
BCP-worthy advice with implementation-specific knowledge for publication as
BCP in the current form.  I've tried to note instances of this in the
comment section, but for example this includes talking about the "key file"
and the format of the configuration file.  In a similar vein, it's unclear
that the guidance in Appendix A will age well, at least without a more
explicit disclaimer (including disclaimer of normativity) -- e.g,. are the
-4 and -6 modifiers to restrict still needed or best practice?  IIRC a
recent update on my FreeBSD machine updated ntp.conf to just use basic
restrict stanzas without an IP version.

## Who
Benjamin Kaduk 

## Resolution
TBD
DR: We could address the two instances that Benjamin makes note of here. 
First, there is the reference to the "key file". It sounds implementation-specific, 
because ntpd uses a key file. But so do many other implementations. Perhaps we could
clarify by calling this "local key storage" in that section only.

Then, perhaps we can add a more specific disclaimer to the Appendix section, but what 
would it read? 


# Comment (Discuss)

I'm also surprised to see no discussion of the (non-)applicability of IPsec
for NTP traffic, when authenticity or access control is required.  (E.g.,
where IP acls are discussed in Section 5.1)

## Who
Benjamin Kaduk 

## Resolution
DS: This is a good point. We included an addional subsection to Sec. 4.; "4.4 External Security 
Protocols". 

# Comment

In general the writing could be tightened up some more, especially to
remove duplication and improve transitions.  I've noted several instances
in the comments (mostly tagged with "nit"), as well as some more
substantive comments.

Section 2.1

                   UDP-based protocols such as NTP are generally more
   susceptible to spoofing attacks then other connection-oriented
   protocols.  [...]

nit: was this intended to be "other, connection-oriented, protocols"?

## Who
Benjamin Kaduk

## Resolution
Changed in -11 to "UDP-based protocols such as NTP are generally more
        susceptible to spoofing attacks than connection-oriented
        protocols."


# Comement

               NTP control messages can generate a lot of data in
   response to a small query, which makes it more attractive as a vector
   for distributed denial-of-service attacks.  [...]

nit: more attractive than what?  (I.e., maybe just "makes it attractive")

## Who
Benjamin Kaduk

## Resolution

Agree, fixed in -11

# Comment

   BCP 38 [RFC2827] was approved in 2000 to address this.  [...]

nit: maybe, "BCP 38 was published in 2000 to provide some level of
remediation against address-spoofing attacks"?

## Who
Benjamin Kaduk

## Resolution
Agree

# Comment

                                               It is RECOMMENDED that
   large corporate networks (and ISP's of any size) implement ingress
   and egress filtering.  More information is available at the BCP38
   Info Web page [BCP38INFO] .

BCP 38 already makes this recommendation, and the current document is
supposedly scoped to just NTP, so I would have expected wording more like
"It is recommended that [...] that use NTP implement ingress and egress
filtering.", if we can even be clear about who this directive is supposed
to apply to.

## Who
Benjamin Kaduk

## Resolution
DR: Personally, I like the broader recommendation here, as it seems like
a good idea to emphasize the importance of the BCP. But we can
move the sentence "Mitigating source address spoofing attacks 
should be a priority of anyone administering NTP." to appear at the start
of the next paragraph. This will better clarify why the recommendation is there.

# Comment

Section 3.1

   Many network security mechanisms rely on time as part of their
   operation.  If attackers can spoof the time, they may be able to
   bypass or neutralize other security elements.  For example, incorrect
   time can disrupt the ability to reconcile logfile entries on the
   affected system with events on other systems.  An application which
   is secure today could be insecure tomorrow once an unknown bug (or a
   known behavior) is exploited in the right way.  Even our definition
   of what is secure has evolved over the years, so code which was
   considered secure when it was written may turn out to be insecure
   after some time.

The first three sentences seem related, but the last two sentences seem to
be talking about something qualitatively different (namely, "more
vulnerabilities being discovered over time", compared to the original's
"accurate time is important for secure and correct operation").  I would
suggest a paragraph break and some transitional language.

## Who
Benjamin Kaduk

## Resolution
We've removed the last two sentences in -11, becuase we think 
the first three stand on their own now.

# Comment

Section 3.2

   But even with 4 or more sources of time, systemic problems can
   happen.  For several hours before and after the June 2015 leap
   second, several operators implemented leap smearing while others did
   not, and many NTP end nodes could not determine an accurate time
   source because 2 of their 4 sources of time gave them consistent UTC/
   POSIX time, while the other 2 gave them consistent leap-smeared time.
   See Section 3.7.1 for more information.

   Operators SHOULD monitor all of the time sources that are in use.  If
   time sources do not generally agree, find out the cause and either
   correct the problems or stop using defective servers.  See
   Section 3.5 for more information.

nit: the transition here is a bit odd.  I would suggest either introducing
leap second smearing as a separate concept first (e.g., by
forward-reference to Section 3.7), or making the second quoted paragraph
mention that leap second smearing is one of many potential causes for
disagreement amongst time sources.

## Who
Benjamin Kaduk

## Resolution
rewrote that first paragraph to make it flow a bit better:
    But even with 4 or more sources of time, systemic problems can
	happen. One example involves the leap smearing concept detailed in 
	Section 3.7. For several hours before and after the 
	June 2015 leap second, several operators
	implemented leap smearing while others did not, and many NTP end
	nodes could not determine an accurate time source because 2 of their
	4 sources of time gave them consistent UTC/POSIX time, while the
	other 2 gave them consistent leap-smeared time. This is just one of 
	many potential causes of disagreement among time sources.
	

# Comment

Section 3.3

nit: the Q&A style in the second paragraph is not something I usually
expect to read in a BCP.

## Who
Benjamin Kaduk

## Resolution
DR: Meybe it's just a reflection of our writing style, but these do refelct
questions that we think operators should ask when determining whether their 
implementations are diverse enough.

# Comment

Section 3.4

                             Used improperly, these facilities can be an
   abuse vector.  [...]

I think (but am not 100% sure) that it's an attack vector on the server
itself, as well as an abuse vector.

## Who
Benjamin Kaduk

## Resolution
TBD
DR: In my primitive mind, and abuse vector and attack vector are the same. 
Is it worth differentiating here?

# Comment

Section 3.4

The BCP 38 recommendation was already made above; do we really need to
duplicate it here?

## Who
Benjamin Kaduk

## Resolution
DR: I think it's important to link the two, as this shows additional rationale for
implementing BCP38. But we do mention NTP Control messages in the BCP38 section; maybe it's better to just reference that section so we don't repeat the recommendation.

# Comment 

Section 3.5

   If a system starts getting unexpected time replies from its time
   servers, that can be an indication that the IP address of the system
   is being forged in requests to its time server.  The goal of this
   attack is to convince the time server to stop serving time to the
   system whose address is being forged.

nit: the writing here could probably be tightened up.  E.g., things like
"NTP reply packets that do not correspond requests it sent", "an attacker
is forging its IP address in requests to the time server", and "one reason
an attacker would do so could be to convince the time server to".

## Who
Benjamin Kaduk

## Resolution
How about:
If a system starts to recieve NTP Reply packets from a time server
that do not correspond to any requests sent by the system, that can be
an indication that an attacker is forging that system's IP address in
requests to the remote time server. The goal of this attack would be to
convince the time server to stop serving time to the
system whose address is being forged.

# Comment

   If a server's system log shows messages that indicates it is
   receiving timestamps that are earlier than the current system time,
   then either the system clock is unusually fast or somebody is trying
   to launch a replay attack against that server.

Is "receiving timestamps" supposed to be for NTP messages in particular, or
all general syslog traffic?

## Who
Benjamin Kaduk

## Resolution
NTP timestamps, fixed in -11

# Comment

Section 4.1

   [RFC5905] specifies a hash which must be supported for calculation of
   the MAC, but other algorithms may be supported as well.  The MD5 hash
   is now considered to be too weak.  [...]

nit: "too weak" for what?  (Maybe "considered to be weak and unsuitable for
cryptographic usage" would be better, with a reference to RFC 6151 or
similar.

## Who
Benjamin Kaduk

## Resolution
Agreed:
The MD5 hash is now considered to be too weak and unsuitable for cryptgraphic
usage.  [RFC6151] has more information on the algorithm's weaknesses.

# Comment

   To use this approach the communication partners have to exchange the
   key, which consists of a keyid with a value between 1 and 65534,
   inclusive, and a label which indicates the chosen digest algorithm.

Surely there is also the actual cryptographic key material itself!

   Each communication partner adds this information to its own key file.

Does the reader know what a "key file" is at this point in the document?
(Alternately, is "key file" an implementation detail and not a protocol
concept?)

## Who
Benjamin Kaduk

## Resolution

Replace "key file" with "local key storage"?

# Comment

   Some implementations store the key in clear text.  Therefore it
   SHOULD only be readable by the NTP process.  Different keys are added
   line by line to the key file.

Similarly here; the "key file" is only vaguely and implicitly described
(and the line-by-line format is clearly implementation-specific); the main
actionable point here is just to ensure that it is only readable to the NTP
process and the rest could, I think, be safely omitted.

## Who
Benjamin Kaduk

## Resolution

Replace "key file" with "local key storage"?

# Comment

   An NTP client establishes a protected association by appending the
   key to the server statement in its configuration file.  Note that the
   NTP process has to trust the applied key.

If the configuration file format is not standardized, there's not much
useful for us to say here about its contents.  Also, what does "has to
trust" mean?

## Who
Benjamin Kaduk

## Resolution
By "has to trust", we mean that once the key is applied, it will be be used 
under all circumstanes and trust can't be revoked unless it is done manually. 
 
We can rewrite to be clearer:

An NTP client must be able to link a key to a particular server
in order to establish a protected association. This linkage is
implementation specific. Once applied, a key will be trusted until
the link is removed.



# Comment

Section 4.2

The reference is provided only for the attack on autokey but not for
autokey itself.  Is there a stable reference for the autokey protocol (so
that people know what to not use)?

## Who
Benjamin Kaduk

## Resolution
We've added RFC 5906 as an informative reference.

# Comment

Section 5.1

                                                         NTP control
   queries also leak important information (including reference ID,
   expected origin timestamp, etc.) that may be used in attacks
   [CVE-2015-8139].  A remote attacker can learn this information by
   sending control queries to a target system and inspecting the
   response.

Er, so is it the control *query* that leaks information, or the response to
that query?

## Who
Benjamin Kaduk

## Resolution
"and inspecting the leaked information in the response."

# Comment

           It is recommended that operators SHOULD filter mode 3 queries
   at the edge, or make sure mode 3 queries are allowed only from
   trusted systems or networks.

nit: "at the edge" is not a well-defined concept here.

## Who
Benjamin Kaduk

## Resolution
changed to "from outside their networks"

# Comment

   Note well that proper monitoring of an NTP server instance includes
   checking the time of that NTP server instance.

Perhaps more explicitly state that the above recommendations for leaf hosts
preclude such monitoring [of leaf hosts]?

## Who
Benjamin Kaduk

## Resolution
"An exception to this can be made if a leaf-node host is being actively monitored, in which case incoming packets from the monitoring server can be allowed."

# Comment

Section 5.3

Do we want to say anything about what to do when a (potential) attack is
detected (e.g., make an entry in the system log)?

## Who
Benjamin Kaduk

## Resolution
I don't think so, becasue the monitoring in this section may not be done
by the NTP implementation itself. If an operator uses an external tool to performance this monitoring, we don't want to impose any requirements on that.


# Comment

Section 5.4

It seems worth reiterating that these KoD packets will be accepted in
common usage even when not cryptographically authenticated, which makes the
DoS risk more severe.

I am not sure whether the note about KoD packets indicating potential
attacks is better here or in the previous subsection.

## Who
Benjamin Kaduk

## Resolution
TBD

# Comment

Section 6.1

This is entirely editorial (and thus your preferences outweigh mine), but
if I were writing this I would say something like "an up-to-date and secure
NTP implementation" rather than "the latest NTP updates applied".

## Who
Benjamin Kaduk

## Resolution
Agree

# Comment

Section 7

Would it ever make sense to have multiple (disjoint?) anycast pools so that
clients could still benefit from having multiple servers concurrently
available to compare?

## Who
Benjamin Kaduk

## Resolution
A good point, we will add it.

# Comment
Appendix A.*

It would be helpful to distinguish which strings are literal syntax
that must be used unchanged and which strings are supposed to be
user-replaceable.

## Who
Benjamin Kaduk

## Resolution
TBD

###

# Comment (Discuss)

I notice that a number of the recommendations here differ from those
in NDSS16. In particular the following recommendations from that paper
do not seem to appear:

- Do not put INIT in the reference ID on restart
- Do not send KoD
- Disable fragmentation
- Randomize source ports

I'm not saying that all of these recommendations need to be in this
document, but I am curious why they are not and would tend to think
that one should document why they are not.

## Who
Eric Rescorla

## Resolution
DPR: We worked closely with Sharon Goldberg, one of the authors on the
referenced paper, when writing this section. While the paper makes the
recommendations you list, we simply didn't want to include everything, but 
rather include the things that would have the most immediate impact.

- The advice for not putting INIT in the reference ID on restart might be 
useful to include after all, as we do give other advice for implementors 
at the end of the "Avoiding Daemon Restart Attacks" section.

- The paper lists "eliminate NTP's KoD" as one recommendation, but then
immediately acknowledges that it eliminates a server's ability to deal with
heavy volumes of traffic. We elected to not recommend the elimination of KoDs,
in part because there will be many servers deployed who still use them. 
Perhaps that is a topic for NTP v5, someday.

- The paper suggests that the attack surface for the NTP fragmentation attack 
is "small but non-negligible". We felt the attack surface was not large enough
to include directly in this BCP. Since the paper is referenced in multiple 
places, though, interested readers (such as yourself) would be able to find it.

- The paper mentions Source Port Randomization as a possibility to mitigate the
fragmentation attack, but then goes on to say that it is not a "sufficient defense".

DS: Denis, I think your answers are appropriate. The advice for implementors not
to send he INIT code is from my point of view ok.

# Comment (Discuss)

DETAIL
S 2.1.
>      response to a small query, which makes it more attractive as a vector
>      for distributed denial-of-service attacks.  (NTP Control messages are
>      discussed further in Section 3.4).  One documented instance of such
>      an attack can be found here [1], and further discussion in [IMC14]
>      and [NDSS14].  Mitigating source address spoofing attacks should be a
>      priority of anyone administering NTP.

what does this text mean? What practices can I engage in as an NTP
server that mitigate source spoofing attacks? The next paragraph seems
to largely talk about traffic *sources*. Is the assumption that the
NTP server is supposed to do BCP 38 filtering? That seems not that
effective.

As a smaller point, I see that this text says "should", not SHOULD. Is
that a mistake or is this intended not to have any normative force?

## Who
Eric Rescorla

## Resolution
As part of another comment, we've moved the "mitigating source address 
spoofing attacks" sentence to the next paragraph, to further highlight
it's relation to BCP38. 

BCP38 would provide some level of protection against spoofing attacks,
but as you note it's not really effective when applied at the server 
level. This is why we give the guidance for large ISP's and networks. 

DS: I agree. Only one point. Should we add a sentence why we not using normative
language in this sections?

DPR: We do have normative language later in that paragraph now saying that "It is 
RECOMMENDED that ISP's and large corporate networks implement ingress and egress 
filtering. Isn't that enough?

# Comment (Discuss)


S 3.2.
>      [RFC5905].  It is RECOMMENDED that that NTP users select an
>      implementation that is actively maintained.  Users should keep up to
>      date on any known attacks on their selected implementation, and
>      deploy updates containing security fixes as soon as practical.
>   
>   3.2.  Use enough time sources

I note that you don't seem to be recommending that people use Chronos
(http://wp.internetsociety.org/ndss/wp-
content/uploads/sites/25/2018/02/ndss2018_02A-2_Deutsch_paper.pdf),
which, as I understand it, is compatible with existing NTP servers but
far more resistant to spoofing. Is there a reason why? Assuming that
there is a good reason, that seems like it should be covered here.

## Who
Eric Rescorla

## Resolution
TBD
DS: The primary goal of Chronos is to provide a NTP client that prevents from
time shifting (delay) attacks. Chronos applies a very interesting approach to mitigate
such attacks. However, it is not yet a stable product that can be applied out of the
box. Currently, there is a draft draft-schiff-ntp-chronos-01 that 
is considered for adoption in the ntp working group. This draft aims to standardize 
the main concepts of Chronos so that NTP implementations may benefit from them. 
But currently usage of Chronos cannot be recommended. 

# Comment (Discuss)

S 3.2.
>      See Section 3.7.1 for more information.
>   
>      Operators SHOULD monitor all of the time sources that are in use.  If
>      time sources do not generally agree, find out the cause and either
>      correct the problems or stop using defective servers.  See
>      Section 3.5 for more information.

It's not really possible to evaluate this advice without any
description of the threat model, which is pretty sketchily covered
below. In particular, if an attacker controls my network, then it's
basically like having one NTP server, no matter how many people I am
talking to, and even an inaccurate but secure server (e.g., tlsdate)
is superior.

## Who
Eric Rescorla

## Resolution
TBD
DS: In Sec. 3.2 we give advice on the number of time sources so that NTP's 
inherent selection mechanisms are enabled to protect against unintentionally 
false time sources. We don't consider the case in which 
adversaries are able to manipulte NTP packets. This is done in Sec. 4. 

# Comment (Discuss)


S 11.3.
>      [10] https://support.ntp.org/bin/view/Support/ConfiguringNTP
>   
>   Appendix A.  NTP Implementation by the Network Time Foundation
>   
>      The Network Time Foundation (NTF) provides the reference
>      implementation of NTP, well-known under the name "ntpd".  It is

What makes this the reference implementation? Generally, the IETF does
not bless specific implementations as reference implementations unless
they themselves appear in the RFC (as with Opus).

## Who
Eric Rescorla

## Resolution
RFC 5905 directly states that the reference implementation 
is maintained at ntp.org, and right now that is maintained with the 
NTF. But we understand the point that ntpd has made some improvements
that deviate from 5905 as written. 

We've removed "reference implementation" from the description and tweaked it a bit further. 

# Comment

S 3.1.
>      implementations, on many different platforms.  The practices in this
>      document are meant to apply generally to any implementation of
>      [RFC5905].  It is RECOMMENDED that that NTP users select an
>      implementation that is actively maintained.  Users should keep up to
>      date on any known attacks on their selected implementation, and
>      deploy updates containing security fixes as soon as practical.

This text is kind of hard to follow. It seems like it is making two
entirely separate points:

1. It is important to have accurate time.
2. It is important to have an up-to-date implementation of NTP.

I agree with both these claims, but they don't seem that closely
connected. It's true that an out-of-date version of NTP might lead to
inaccurate time, but it might also lead to (for instance) arbitrary
code execution on the client. For this reason, I would suggest that it
would be wise to separate these two paragraphs.

## Who
Eric Rescorla

## Resolution
I think there is some old text here. With the recently improved Security Considerations section, I think we can remove the first paragraph entirely.

# Comment 


S 3.2.
>   
>      o  If there are 2 sources of time and they agree well enough, then
>         the best time can be calculated easily.  But if one source fails,
>         then the solution degrades to the single-source solution outlined
>         above.  And if the two sources don't agree, then it's impossible
>         to know which one is correct by simply looking at the time.

This isn't strictly true. Consider the case where I have an iPhone and
the onboard clock reads 2018-12-19 and the NTP server reads 2001. I
know the NTP server is wrong because iPhones didn't exist in 2001.

## Who
Eric Rescorla

## Resolution
Only if the iPhone is smart enough to disqualify the rogue source, in which case
you're still back to 1 source. I think the advice here still stands.

# Comment 


S 3.4.
>      optionally authenticated control of NTP and its configuration.  Used
>      properly, these facilities provide vital debugging and performance
>      information and control.  Used improperly, these facilities can be an
>      abuse vector.  For this reason, it is RECOMMENDED that publicly-
>      facing NTP servers should block mode 6 queries from outside their
>      organization.

Why are these facilites an abuse vector

## Who
Eric Rescorla

## Resolution
TBD

# Comment 


S 3.5.
>   
>      If a system starts getting unexpected time replies from its time
>      servers, that can be an indication that the IP address of the system
>      is being forged in requests to its time server.  The goal of this
>      attack is to convince the time server to stop serving time to the
>      system whose address is being forged.

Why would this work? Some sort of rate limit on the server.

## Who
Eric Rescorla

## Resolution
We've reworded this in the latest draft to make this clearer.

# Comment 


S 3.5.
>      attack is to convince the time server to stop serving time to the
>      system whose address is being forged.
>   
>      If a system is a broadcast client and its system log shows that it is
>      receiving early time messages from its server, that is an indication
>      that somebody may be forging packets from a broadcast server.

You need to provide citations for broadcast client and broadcast
server, even if they are just to some section of the NTP spec.

## Who
Eric Rescorla

## Resolution
OK

# Comment 


S 3.5.
>      receiving early time messages from its server, that is an indication
>      that somebody may be forging packets from a broadcast server.
>   
>      If a server's system log shows messages that indicates it is
>      receiving timestamps that are earlier than the current system time,
>      then either the system clock is unusually fast or somebody is trying

Why do you say "unusually fast". My understanding is that it's
actually quite common to be seconds off.

## Who
Eric Rescorla

## Resolution
changed to "much earlier".

# Comment 


S 4.1.
>      periodically.  However, NTP does not provide a mechanism to assist in
>      doing so.
>   
>      [RFC5905] specifies a hash which must be supported for calculation of
>      the MAC, but other algorithms may be supported as well.  The MD5 hash
>      is now considered to be too weak.  Implementations will soon be

This comment about MD5 kind of comes out of nowhere. some context for
why I would think I should use MD5 would help.

## Who
Eric Rescorla

## Resolution
Modified the text to clarify that MD5 is specifically called out in RFC 5905.

# Comment 


S 4.1.
>   
>      [RFC5905] specifies a hash which must be supported for calculation of
>      the MAC, but other algorithms may be supported as well.  The MD5 hash
>      is now considered to be too weak.  Implementations will soon be
>      available based on AES-128-CMAC [I-D.ietf-ntp-mac], and users are
>      encouraged to use that when it is available.

Do you want to use 8174 language here? Also, I-D.ietf-ntp-mac has
already been approved, so it seems like given the long latency between
here and the RFC, we should write this in the present tense rather
than the future tense.

## Who
Eric Rescorla

## Resolution
We have no problem makign these changes. We did this at first because we weren't sure which would get through the gauntlet first, but it looks like ntp-mac will. I will update the 8174 language, and if ietf-ntp-mac gets published before this we'll include it as an RFC.

# Comment 



S 4.1.
>      inclusive, and a label which indicates the chosen digest algorithm.
>      Each communication partner adds this information to its own key file.
>   
>      Some implementations store the key in clear text.  Therefore it
>      SHOULD only be readable by the NTP process.  Different keys are added
>      line by line to the key file.

Does *every* implementation have a key file like this? I'm not sure
what the point of this sentence is.

## Who
Eric Rescorla

## Resolution
Benjamin Kaduk made a similar comment: we will change this to "local key storage". All implementations I am familiar with use a key file, but of course that's not exhaustive.

# Comment 


S 5.2.
>      o  Configure the ntp client to only ignore the panic threshold in a
>         cold start situation.
>   
>      o  Add 'minsane' and 'minclock' parameters to the ntp.conf file so
>         ntpd waits until enough trusted sources of time agree on the
>         correct time.

This seems pretty implementation specific.

## Who
Eric Rescorla

## Resolution
We're comfortable with the first point, as the panic threshold is specified in RFC 5905. But the next draft will have language that makes the second point more general:

Increase the minimum number of servers required before the NTP 
client adjusts the system clock. This will make the NTP client wait 
until enough trusted sources of time agree before declaring the 
time to be correct.

# Comment 


S 5.4.
>      when asked to do so by a server.  It is even more important for an
>      embedded device, which may not have an exposed control interface for
>      NTP.
>   
>      That said, a client MUST only accept a KoD packet if it has a valid
>      origin timestamp.  Once a RATE packet is accepted, the client should

What's a RATE packet? It's not defined here or cited.

## Who
Eric Rescorla

## Resolution
We now include a reference to Section 7.4 of RFC 5905.

# Comment 


S 6.2.
>      Vendors are encouraged to invest resources into providing their own
>      time servers for their devices to connect to.
>   
>      Vendors should read [RFC4085], which advises against embedding
>      globally-routable IP addresses in products, and offers several better
>      alternatives.

This seems to kind of duplicate S 4.5.

## Who
Eric Rescorla

## Resolution
They are different, as the advice in this section is applicable to embedded
device vendors specifically. The advice in RFC 4085 is specifically applicable
to embedded devices.

# Comment 



S 6.2.1.
>      The NTP Pool Project offers a program where vendors can obtain their
>      own subdomain that is part of the NTP Pool.  This offers vendors the
>      ability to safely make use of the time distributed by the Pool for
>      their devices.  Vendors are encouraged to support the pool if they
>      participate.  For more information, visit http://www.pool.ntp.org/en/
>      vendors.html [8] .

This too, duplicates 4.5.

## Who
Eric Rescorla

## Resolution
This does look like it can be cleaned up a bit: we can move this more 
descriptive text tp the Pool Servers section, and then reference that section
from this one.

# Comment 


S 7.
>      own potential issues.  It means each client will likely use a single
>      time server source.  A key element of a robust NTP deployment is each
>      client using multiple sources of time.  With multiple time sources, a
>      client will analyze the various time sources, selecting good ones,
>      and disregarding poor ones.  If a single Anycast address is used,
>      this analysis will not happen.

I'm not sure I'm following this. The idea here seems to be that a
client would ordinarily be configured with N addresses, but with
anycast it will be configured with 1? Or that all the anycast
addresses will go to the same place? Presumably all the servers in an
anycast group are run by the same entity, in which case is there a
good reason to believe that whatever errors they have will be
independent? In this case, having unicast addresses would seem not to
help.

Separately, how many clients *actually* use >1 server.

## Who
Eric Rescorla

## Resolution
The idea is that all clients can be configured with 1 NTP server IP
address, but there can be multiple servers servicing those requests, and 
the network operator can add or remove servers from the Anycast group 
without having to touch the configuration of each client. 

Even if all servers are managed by the same entity, they can have their
own errors: there may be servers with redundant GNSS connections, and only
one antenna is faulty, for instance. The separate unicast addresses are useful
to have a side-channel way to get to the individual time servers to monitor them.

# Comment 


S 7.
>      anycast servers may arbitrarily enter and leave the network, the
>      server a particular client is connected to may change.  This may
>      cause a small shift in time from the perspective of the client when
>      the server it is connected to changes.  It is RECOMMENDED that
>      anycast only be deployed in environments where these small shifts can
>      be tolerated.

Who is this guidance to? It seems like the clients might well not
know, but they are the ones who tolerate the shift (or not).

## Who
Eric Rescorla

## Resolution
The guidance is to the network operators, and ultimately to the users of the 
NTP service. Utilizing Anycast in this manner may affect the quality of the 
recovered time. But in some applications, this is prefereble to potentially 
having to change the configuration of a large number of clients whenever a 
server is added or removed.

# Comment 


S 11.3.
>   
>      The Network Time Foundation (NTF) provides the reference
>      implementation of NTP, well-known under the name "ntpd".  It is
>      actively maintained and developed by NTF's NTP Project, with help
>      from volunteers and NTF's supporters.  This NTP software can be
>      downloaded from <http://www.ntp.org/downloads.html>

You probably want to explain why the rest of this section follows. For
instance "The remainder of this section describes how to implement
many of the recommendations in this document using that software"

## Who
Eric Rescorla

## Resolution
	   This Appendix gives additional information on how to 
	   implement many of the recommendations in this document using 
	   ntpd.

# Comment 


S 11.3.
>      downloaded from <http://www.ntp.org/downloads.html>
>   
>   A.1.  Use enough time sources
>   
>      In addition to the recommendation given in Section Section 3.2 the
>      ntpd implementation provides the 'pool' directive.  Starting with

Where does this directive go? Some conf file, one assumes.

## Who
Eric Rescorla

## Resolution
they go in the ntp.conf file, of course. It would be a good thing to mention that.

# Comment 


S 11.3.
>      ntp-4.2.6, this directive will spin up enough associations to provide
>      robust time service, and will disconnect poor servers and add in new
>      servers as-needed.  If you have good reason, you may use the
>      'minclock' and 'maxclock' options of the 'tos' command to override
>      the default values of how many servers are discovered through the
>      'pool' directive.

What would those good reasons be?

## Who
Eric Rescorla

## Resolution
That can probably be removed. If a user is using 'minclock' or 'maxclock', 
they already have their own good reasons.

# Comment 


S 11.3.
>   
>      restrict default -4 nomodify notrap nopeer noquery
>      restrict default -6 nomodify notrap nopeer noquery
>   
>      restrict source nomodify notrap noquery
>      # nopeer is OK if you don't use the 'pool' directive

I assume this is a comment? What is it doing right below a line that
doesn't mention "nopeer"

## Who
Eric Rescorla

## Resolution
We've removed the comment.

###


# Comment

General observation: I was surprised to find that that a lot of the recommendations 
here don't seem especially specific to NTP. (E.g. keeping implementations up to date.) 
But I don't suppose that's really an problem, so I don't expect action here.

## Who
Ben Campbell 

## Resolution
N/A

# Comment

§2.1, last paragraph: "It is RECOMMENDED that
large corporate networks (and ISP’s of any size) implement ingress
and egress filtering."

Is that a new normative requirement, or an existing requirement from BCP38? 
If the latter, please consider using description language rather than normative keywords.

## Who
Ben Campbell 

## Resolution
BCP38 / RFC 2827 doesn't use the normative language, so I suppose it's a new 
normative recommendation from this BCP.

# Comment

§3.3: This section recommends that operators choose time servers with different implementations/technology. 
Are time sources expected to publicize that sort of information?

## Who
Ben Campbell 

## Resolution
We're calling attention to the fact that having a diversity of timing sources
is not as simple as having two boxes. 

# Comment

§3.4: Am I correct to assume that "control messages" and "mode 6 messages" are the same thing? Please use consistent terminology.

## Who
Ben Campbell 

## Resolution
Will stick with "NTP Control Messages"

# Comment

§3.6:
- First Paragraph: "Users who want to
synchronize their computers SHOULD only synchronize to servers that
they have permission to use."
Why not MUST?

## Who
Ben Campbell 

## Resolution
I think you're right, in the context of embedded devices we should really 
forcefully advise vendors to play nice.

# Comment

- 2nd paragraph: Is the NTP Pool stabile enough for a plug like this in an RFC? Remember, RFCs live "forever". (see also §6.2.1)
## Who
Ben Campbell 

## Resolution
It's been around for quite a while and the members of the working group think it's stable enough to include.

# Comment

§3.7: "Note well that NTPv4’s longest polling
interval exceeds one day and thus a leap second announcement may be
missed."
Is that okay? Is there any action recommended due to this?

## Who
Ben Campbell 

## Resolution
Changed that to bea bit mroe active:
When implemeting this recommendation, 
operators should ensure that clients are not configured to use polling intervals
greater than 24 hours, so the leap second notification is not missed.

# Comment

§3.7.1, last paragraph: How does a client know if the server does leap second smearing?
## Who
Ben Campbell 

## Resolution
There is no standard way to detect this at this time. Someone has to ask the
server administrator.

# Comment

§4.1: 
- "Therefore, for each association, keys SHOULD be exchanged securely by external means, and they SHOULD be protected from disclosure."
Why not MUST (both times)?
## Who
Ben Campbell 

## Resolution
We're changing these to MUSTs.

# Comment

- "Implementations will soon be available based on AES-128-CMAC [I-D.ietf-ntp-mac], and users are encouraged to use that when it is available."
Is that worth a normative requirement?

## Who
Ben Campbell 

## Resolution
Yes, especially since it seems that draft will emerge first.

# Comment
- "Some implementations store the key in clear text"
Wouldn't the better practice to be not to do that?

## Who
Ben Campbell 

## Resolution
Yes, but we need to address the current state of things. 

# Comment

§5.1: 
- 3rd paragrap: "A host that is not supposed to act as an NTP server that provides
timing information to other hosts MAY additionally log and drop
incoming mode 3 timing queries from unexpected sources."

 i don't understand the point. Also, is the upper-case "MAY''intended as permission to do that?

## Who
Ben Campbell 

## Resolution
we changed this to non-normative in the latest draft.
This section is about minimizing information leakage. One way to do this
is simply to not respond to packets that it doesn't have to.

# Comment

- last paragraph: "Note well that proper monitoring of an NTP server instance includes
checking the time of that NTP server instance."
Should there be normative guidance here? (Also, the sentence seems out of place.)

## Who
Ben Campbell 

## Resolution
The normative guidance is at the end now. 

We are pointing out here that while you might want to drop all Mode 3 packets,
they do have some use for monitoring within your organization.

# Comment

§6.1: "Vendors of embedded devices MUST pay attention"
Can you recommend something more concrete (and verifiable) than "pay attention"?

## Who
Ben Campbell 

## Resolution
We've made this non-normative in response to another comment.

# Comment

§2.1: "more susceptible to spoofing attacks then other connection-oriented protocols":
s/then/than
Also, it seems like "other" is not descriptive here, since UDP is not a connection-oriented protocol.

## Who
Ben Campbell 

## Resolution
We removed the "other" in the latest draft.

# Comment

§3.4:
-  first paragraph: The last sentence will not hold up well to the passage of time. Please consider adding something to the effect of "At the time of this writing..."
- Last paragraph: The last sentence seems redundant to the section on BCP38.

## Who
Ben Campbell 

## Resolution
Agree on both points. The last paragraph not directly references the BCP38 section.

# Comment

§5.1, 3rd paragraph: It is recommended that operators SHOULD filter mode 3 queries
at the edge
"recommended that...SHOULD" is redundant. Please consider just saying "Operators SHOULD..."
## Who
Ben Campbell 

## Resolution
Agreed

# Comment

§5.4: Is a KoD packet and a RATE packet the same thing? (Please use consistent terminology)
## Who
Ben Campbell 

## Resolution
We've clarified this in the latest draft.

# Comment

§11.2: Is there a reason [BCP38INFO] is here and not in the URL references?

## Who
Ben Campbell

## Resolution
Actually, this was an attempt to fix how that URL is rendered on the HTML
view of the document. (See https://tools.ietf.org/html/draft-ietf-ntp-bcp-10 ) I guess since this URL has the text "BCP" in it, it
doesn't render properly. I will revert it back to a URL reference, but then I
will need to get some professional help on this.


###
# Comment 

Firstly, thanks for mentioning BCP-38 -- it feels like you are tilting at windmills here, but I appreciate your optimism :-)

## Who
Warren Kumari  

## Resolution
N/A

# Comment
'NTF' should be expanded on first use. 

## Who
Warren Kumari  

## Resolution
agree

# Comment

I don't have any test to suggest, but "For several hours before and after the June 2015 leap second, 
several operators implemented leap smearing while others did not, ..." sounds like, in June 2015 a w
hole bunch of operators sat down at their workstations and wrote code to implement leap smearing 
(the word  "implemented" makes this less than clear). Perhaps "performed leap smearing" would be 
clearer? 

## Who
Warren Kumari  

## Resolution
"Several operators configured their servers with leap smearing while others 
did not"

# Comment

Section 4.1.  Pre-Shared Key Approach
"The MD5 hash is now considered to be too weak." -- too weak for what? 
(I agree, but you seem to be missing words).

## Who
Warren Kumari  

## Resolution
We've included a reference to RFC 6151 with more information.

# Comment

Much of the test of the document seems to be "motherhood and apple pie" type advice 
(e.g: "Users should keep up to date on any known attacks on their selected implementation, 
and deploy updates containing security fixes as soon as practical."), but this is a BCP, this doesn't seem unreasonable :-)

## Who
Warren Kumari  

## Resolution
N/A


