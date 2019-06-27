# RFC Editor Comments

# Comment

1) <!-- [rfced] FYI, the following section titles have been modified for
consistency with the other section titles. Please let us know if you
prefer otherwise.

Original:
3.2.  Use enough time sources
3.3.  Use a diversity of Reference Clocks
5.5.  Broadcast Mode Should Only Be Used On Trusted Networks
5.6.  Symmetric Mode Should Only Be Used With Trusted Peers

Current:
3.2.  Using Enough Time Sources
3.3.  Using a Diversity of Reference Clocks
5.5.  Broadcast Mode Only on Trusted Networks
5.6.  Symmetric Mode Only with Trusted Peers
-->

### Response
DR -- this is OK


# Comment
2) <!-- [rfced] RFC 1305 has been obsoleted by RFC 5905.  We recommend stating
this in the text; please let us know if the following text is acceptable.

Original:
   Some implementations of NTPv4 provide the NTP Control Messages (also
   known as Mode 6 messages) that were originally specified in
   Appendix B of [RFC1305], which defined NTPv3.

Perhaps:
   Some implementations of NTPv4 provide the NTP Control Messages (also
   known as Mode 6 messages) that were originally specified in
   Appendix B of [RFC1305], which defined NTPv3.  (Note that RFC 1305 was
   obsoleted by RFC 5905.)
-->

### Response
DR -- The point we are trying to get across here is that the Mode 6 messages were specified in 
RFC1305, and were never formally included in RFC5905, but are still used. 

How about:

   Some implementations of NTPv4 continue to support the NTP Control Messages (also
   known as Mode 6 messages). Thes messages were originally specified in
   Appendix B of [RFC1305], which defined NTPv3, but were not included in 
   [RFC 5905], which obsoleted [RFC1305].

## RFCEd Response:
   These messages do
   not appear in the NTPv4 specification [RFC5905], which obsoletes the
   NTPv3 specification [RFC1305], but they are still used.



# Comment
3) <!-- [rfced] Should UT1 be expanded to "Universal Time" or left as is?

Original:
   UTC is kept in agreement with the astronomical time UT1 [5] to within ...

Perhaps:
   UTC is kept in agreement with Universal Time (UT1) [SOLAR] to within ...
-->

### Response
DR -- This is OK


# Comment
4) <!-- [rfced] FYI, we changed "slewed" be "slowed" here (2 instances).
Please let us know if that is not your intention. Also, please review
how "slewed small" was updated.

Original:
  NTP time will be slewed
  in small increments over a comparably large window of time ...

Current:
  NTP time will be slowed
  in small increments over a comparably large window of time ...


Original:
   The smear interval
   should be large enough to make the rate that the time is slewed
   small, so that clients will follow the smeared time without
   objecting.

Current:
   The smear interval
   should be large enough for the time to be slowed at a low rate,
   so that clients will follow the smeared time without
   objecting.
-->

### Response
DR -- I like the original "Slewed" better, because it allows for the unlikely 
possibility that a negative leap second might happen in the future, in which 
case time would have to be sped up.

However, I like the change from "slewed small" to "slewed at a low rate".

## RFCEd Response:

For our understanding, would you please point to the definition of "slew" that is in use? We see that "slewed" is used in RFC 1305 and a few other RFCs, but we aren't finding a relevant definition.

### Response
DR -- I've heard the term many times in the control systems and network timing industry, with the meaning "to adjust" or "to change". "slew rate" is a common term in control theory meaning rate of change. Our intent behind using "slew" here is to make small adjustments to a property (like the time) in order to eventually bring it in line with what is expected.

Our main objection to "slowed" vs. "slewed" is that "slowed" implies adjustment in a single direction, and we don't want that restriction. Perhaps "adjusted" is less ambiguous than "slewed":

   Some NTP installations make use of a technique called leap smearing.
   With this method, instead of introducing an extra second (or
   eliminating a second) in a leap-second event, NTP time is adjusted in
   small increments over a comparably large window of time (called the
   smear interval) around the leap-second event.  The smear interval
   should be large enough for the time to be adjusted at a low rate, so
   that clients will follow the smeared time without objecting.






# Comment
5) <!-- [rfced] Will the relation between "invalid cryptographic MAC"
and the reference [CCR16] be clear to the reader?
In looking at that document, there are zero instances
of "invalid".

Original:
   3.  A packet with an invalid cryptographic MAC [CCR16].
-->

### Response
DR -- I think this is OK, checking the integrity of MACs is well understood.


# Comment
6)  <!-- [rfced] There were various comments in the submitted XML file.
Please review them and let us know if they need to be addressed or if we can
delete them.

For example:
  <!- - Cite the "Leap-Smear REFID" in the ntp-refid update?  - ->
-->

### Response
DR -- all comments can be deleted as necessary


# Comment
7) <!-- [rfced] Terminology
We have noted inconsistencies in the capitalization of some terms in this
document. Should these be uniform? If so, please let us know which form is
preferred.

Control Message vs. control message
Leap Smearing vs. leap smearing
Message Authentication Code vs. message authentication code
Anycast vs. anycast
Mode vs. mode
INIT vs. init
-->

### Response
DR -- I think in general the changes to capitalization are OK. 
It is correct to leave "INIT" capitalized in:

Prevent the NTP daemon from putting 'INIT' in the reference ID

because there, INIT is the actual text in the packet.


# Comment from Denis Reilly
I have noticed that the RFC editor has added hyphens in several places:
leap-smearing

leap-second

time-synchronization

rate-management

denial-of-service

Is there a style guide that details why these changes are made? 
In particular, I note that "time synchronization" appears several 
times in RFC7384 with no hyphen.

This is not a big deal, I just want to make sure we are consistent with other RFC's.

6/24: I talked with our Tech Writer, she said that the hyphenation should appear
the word combination is used as an adjective. (For instance, "leap second" vs. 
"leap-second file".) I now think it is OK, and not worth mentioning.


# Comment from Denis Reilly
I see that the NTPMAC document has been released as RFC8573 -- 
Would it be possible to replace this reference 
with RFC8573 before publishing this document?


