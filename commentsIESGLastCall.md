IESG Comments

This filecompiles comments from the IESG Telechat.

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
We’re revisiting the text one more time to clarify these. 

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
We’re revisiting this also for the consistency of application.

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

I don’t think anything there looks stable right now, but that looks like a good group to follow. Thanks for the tip!

