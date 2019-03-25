These comments were sent by Eric Rescorla in response to the first round of IESG comment responses,
and need further responses:

# Comment
DETAIL
S 2.1.
>      response to a small query, which makes it more attractive as a vector
>      for distributed denial-of-service attacks.  (NTP Control messages are
>      discussed further in Section 3.4).  One documented instance of such
>      an attack can be found here [1], and further discussion in [IMC14]
>      and [NDSS14].  Mitigating source address spoofing attacks should be a
>      priority of anyone administering NTP.

what does this text mean? What practices can I engage in as an NTP server that mitigate source spoofing attacks? The next paragraph seems to largely talk about traffic *sources*. Is the assumption that the NTP server is supposed to do BCP 38 filtering? That seems not that effective.

As a smaller point, I see that this text says "should", not SHOULD. Is that a mistake or is this intended not to have any normative force?

Response:
As part of another comment, we've moved the "mitigating source address spoofing attacks" sentence to the next paragraph, to further highlight
it's relation to BCP38. 

BCP38 would provide some level of protection against spoofing attacks, but as you note it's not really effective when applied at the server 
level. This is why we give the guidance for large ISP's and networks.

We do have normative language later in that paragraph now saying that "It is RECOMMENDED that ISP's and large corporate networks implement ingress and egress filtering", and we feel that's enough.

--

But these aren't things that the *server* can do, really. So, I don't understand how it's meaningful to say that it should be a priority to mitigate these attacks for "anyone administering NTP"

## Response

TBD

# Comment

S 3.2.
>      See Section 3.7.1 for more information.
>
>      Operators SHOULD monitor all of the time sources that are in use.  If
>      time sources do not generally agree, find out the cause and either
>      correct the problems or stop using defective servers.  See
>      Section 3.5 for more information.

It's not really possible to evaluate this advice without any description of the threat model, which is pretty sketchily covered below. In particular, if an attacker controls my network, then it's basically like having one NTP server, no matter how many people I am talking to, and even an inaccurate but secure server (e.g., tlsdate) is superior.

Response:
In Sec. 3.2 we give advice on the number of time sources so that NTP's  inherent selection mechanisms are enabled to protect against unintentionally false time sources. We don't consider the case in which adversaries are able to manipulate NTP packets. This is done in Sec. 4.

--

Then you need to state that this isn't intended to deal with this threat model.

## Response

TBD

# Comment

S 3.2.
>
>      o  If there are 2 sources of time and they agree well enough, then
>         the best time can be calculated easily.  But if one source fails,
>         then the solution degrades to the single-source solution outlined
>         above.  And if the two sources don't agree, then it's impossible
>         to know which one is correct by simply looking at the time.

This isn't strictly true. Consider the case where I have an iPhone and the onboard clock reads 2018-12-19 and the NTP server reads 2001. I know the NTP server is wrong because iPhones didn't exist in 2001.

Response:
Only if the iPhone is smart enough to disqualify the rogue source, in which case you're still back to 1 source. I think the advice here still stands.

--

The problem here is the statement that it is "impossible". That is clearly false.


## Response
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

Response:
We've rewritten this for clarity:
If a system starts to receive NTP Reply packets from a time server
that do not correspond to any requests sent by the system, that can be
an indication that an attacker is forging that system's IP address in
requests to the remote time server. The goal of this attack would be to
convince the time server to stop serving time to the
system whose address is being forged.

--

I think you need to state that the time server will potentially throttle in response to this.

## Response

TBD

# Comment

S 7.
>      anycast servers may arbitrarily enter and leave the network, the
>      server a particular client is connected to may change.  This may
>      cause a small shift in time from the perspective of the client when
>      the server it is connected to changes.  It is RECOMMENDED that
>      anycast only be deployed in environments where these small shifts can
>      be tolerated.

Who is this guidance to? It seems like the clients might well not know, but they are the ones who tolerate the shift (or not).

Response:
The guidance is to the network operators, and ultimately to the users of the  NTP service. Utilizing Anycast in this manner may affect the quality of the 
recovered time. But in some applications, this is preferable to potentially  having to change the configuration of a large number of clients whenever a server is added or removed.

--

How do the clients know whether anycast is in use?

## Response

TBD
