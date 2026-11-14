# Free live classes for School OS: research and practical recommendation

Reviewed against official provider documentation on **14 November 2026**. Your stated hosting is **shared cPanel only**. This comparison concerns media hosting and software; it does not change School OS subscription billing.

**There are free alternatives. A paid LiveKit Cloud subscription is not required.** Free software, a free hosted allowance, and a service promising unlimited capacity and guaranteed availability are different things. The sources reviewed do not establish a provider that guarantees unlimited private, embedded, multi-school video traffic indefinitely at zero cost.

## What I recommend for your situation

1. **No additional media-hosting spend today:** use the Google Meet invitation option already present in School OS when its meeting limits fit the timetable. School OS can schedule the lesson, notify the allocated class and provide its join link; the actual call opens in Meet. This avoids buying another server, but is an external meeting, not School OS's native player.
2. **Native School OS player, small free pilot:** centrally configure a LiveKit Cloud Build project. It is supported by the existing client and has a documented free allowance with a hard stop rather than paid-plan overages. Treat it as a pilot allowance, not a whole platform's monthly timetable.
3. **Native player without a software subscription or per-minute vendor licence:** centrally configure self-hosted LiveKit. An eligible free VM can make the infrastructure bill zero while you stay within its allowances, but availability, operational work and reliability still need validation. Your shared cPanel website can remain where it is; the media server runs separately.
4. **Most promising larger hosted free allowance found:** Cloudflare Realtime SFU. Its data allowance is generous for a one-teacher broadcast, but it requires a separate Cloudflare adapter. Its API is not LiveKit's API. **That adapter is not part of the 5.3.3 ZIP.** Do not paste Cloudflare credentials into the LiveKit form and expect it to work.

The 5.3.3 update centralises the configuration and preserves the already tested native media stack. It does not buy a hosting plan, create a provider account or automatically enrol you in a paid service.

## Comparison of viable options

| Option | What is free | Important practical limit | School OS fit |
|---|---|---|---|
| **Self-hosted LiveKit** | Open-source media server software; no mandatory LiveKit Cloud subscription | You supply a server, TLS, network access, bandwidth, monitoring and maintenance. Capacity follows the deployment | Native support in this update; one central configuration for all schools |
| **LiveKit Cloud Build** | Documented free transport allowance: 5,000 participant-minutes/month, 50 GB downstream and 100 concurrent participants across rooms | Allowances are not per school. Free usage stops at the cap; paid plans have different billing | Native support, suitable for a limited pilot |
| **Cloudflare Realtime SFU + TURN** | First 1,000 GB of shared monthly egress allowance | SFU/TURN share one allowance; excess is currently $0.05/GB. Other Cloudflare products have separate charges | Requires a new native adapter; promising for a larger free pilot |
| **Google Meet, personal account** | Up to 100 participants; group calls up to 60 minutes | A host account and invitation are required; meeting runs in Google's UI | Existing School OS invitation option; easiest immediate external alternative |
| **Public meet.jit.si** | A hosted public Jitsi meeting service | Official October 2026 announcement sets a 95-minute meeting limit. Official JaaS page says public meet.jit.si embedding is no longer supported | External meetings may be useful; not a dependable foundation for a new embedded portal integration |
| **Self-hosted Jitsi Meet** | Open-source conferencing software | Needs its own conferencing infrastructure and authentication/operations setup | A viable alternative stack, but not a drop-in replacement for the LiveKit client |
| **Jitsi as a Service (JaaS)** | Official Jitsi page advertises an allowance of up to 25 endpoints with unlimited minutes | Confirm the account's exact endpoint/usage definition and current terms; not unlimited school-wide capacity | Separate hosted integration, not implemented here |
| **BigBlueButton** | Open-source virtual-classroom software | Its installation guide calls for substantial server resources, including at least 16 GB RAM and 250 Mbps symmetric bandwidth | Strong classroom features; not something an ordinary shared cPanel account can host |
| **Daily Video SDK** | 10,000 participant-minutes/month | Official FAQ says usage continues into pay-as-you-go charges after the allowance, without a hard stop; listed initial overage is $0.004/participant-minute | Separate integration; not the best default when the priority is avoiding accidental overage |
| **mediasoup or Janus** | Open-source media-server components | You still build/host the service and its signalling, permissions and operations | Technically viable; substantially more integration work than reusing School OS's existing native stack |
| **YouTube Live** | Broadly available hosted broadcasting tools | Channel verification/eligibility and possible initial activation delay; unlisted links are not enrolment-based access control | Can suit public lectures, but is not equivalent to a private interactive School OS classroom; not integrated here |

Official sources for these rows:

- [LiveKit self-hosting and comparison with Cloud](https://docs.livekit.io/transport/self-hosting/) and [production deployment](https://docs.livekit.io/transport/self-hosting/deployment/).
- [LiveKit Cloud quotas, allowance definitions and free hard caps](https://docs.livekit.io/deploy/admin/quotas-and-limits/).
- [Cloudflare Realtime SFU/TURN pricing](https://developers.cloudflare.com/realtime/sfu/platform/pricing/) and [resource limits](https://developers.cloudflare.com/realtime/sfu/platform/limits/). This is the low-level Realtime SFU product, not a claim that all RealtimeKit usage is free.
- [Google Meet participant and meeting-duration limits](https://support.google.com/meet/answer/7317473?hl=en).
- [Jitsi's 9 October 2026 meeting-limit announcement](https://jitsi.org/blog/changes-coming/), [official JaaS/embedding guidance](https://jitsi.org/jaas/) and [public-service terms](https://jitsi.org/meet-jit-si-terms-of-service/).
- [BigBlueButton installation requirements](https://docs.bigbluebutton.org/administration/install/). Its separate [free Moodle hosting offer](https://bigbluebutton.org/moodle-integration/) is restricted and is not a general free-hosting entitlement for a custom PHP portal.
- [Daily pricing and FAQ](https://www.daily.co/pricing/video-sdk/).
- [mediasoup architecture](https://mediasoup.org/documentation/v3/mediasoup/design/) and [licence](https://mediasoup.org/license/); [Janus support/licensing](https://janus.conf.meetecho.com/support.html) and [VideoRoom documentation](https://janus.conf.meetecho.com/docs/videoroom).
- [YouTube Live eligibility](https://support.google.com/youtube/answer/2474026) and [encoder/webcam streaming setup](https://support.google.com/youtube/answer/2907883).

## A genuinely free server route: what to know

Oracle's current Always Free documentation lists an Ampere A1 allowance equivalent to **2 OCPUs and 12 GB RAM**, plus **10 TB/month outbound transfer**. The documentation also says capacity can be unavailable and idle instances may be reclaimed. Older guides quoting different CPU/RAM allowances should not be used as your account's current entitlement. Check the actual eligible resources in your home-region console. [Oracle Always Free documentation](https://docs.oracle.com/en-us/iaas/Content/FreeTier/freetier_topic-Always_Free_Resources.htm).

Self-hosted LiveKit on a correctly provisioned eligible VM is a plausible zero-infrastructure-charge pilot. This is an engineering recommendation, not a measured capacity result for that VM. I have not provisioned an Oracle account, validated regional availability, or load-tested that machine with your schools. The local tests used a different audit machine. Do not promise production uptime on the basis of a free-tier label alone.

For a self-hosted service, use a trusted TLS certificate, correct public media addresses and firewall rules, an appropriate relay for restrictive networks, monitored resource usage and recoverable configuration. LiveKit documents [production setup](https://docs.livekit.io/transport/self-hosting/deployment/) and [ports/firewalls](https://docs.livekit.io/transport/self-hosting/ports-firewall/). A plain PHP installation on shared cPanel does not itself provide these persistent media-server capabilities.

## Why the free allowance can disappear quickly

The following are **illustrative calculations**, not measured usage or a quotation for your account.

Assume one teacher and 30 students attend a 60-minute class:

- Participant-minute accounting: **31 × 60 = 1,860 participant-minutes per class**. One such class on each of 20 school days uses 37,200 participant-minutes.
- Data accounting for one teacher stream: assume each of 30 student receivers gets **0.6 Mbps combined media** for one hour. Egress is approximately **0.6 × 30 × 3,600 ÷ 8 ÷ 1,000 = 8.1 decimal GB** before overhead and extra traffic.
- At 0.3 Mbps the same illustrative class uses about 4.05 GB; at 1 Mbps about 13.5 GB. Actual quality, codec, adaptation, relay paths and usage differ.

Thus a 5,000 participant-minute allowance covers two complete example classes, and a 10,000 allowance covers five. A 1,000 GB allowance could cover roughly 123 of the 8.1 GB example classes **before** overhead, other account traffic and other costs. These are different billing units: a thousand gigabytes is not a thousand participant-minutes.

For scale, 20 schools each running one such class per day for 20 days means 400 class-hours: about 3,240 GB at that assumed bitrate. At the cited Cloudflare rate that illustrative excess over 1,000 GB would be about $112, excluding other services/taxes. This is why “free within an allowance” can be true for a pilot and false for a growing platform. [Cloudflare rate and allowance](https://developers.cloudflare.com/realtime/sfu/platform/pricing/).

## Why simply removing eight from the old code is insufficient

The direct mode sends separate peer-to-peer media connections from the teacher to the students. With a 0.6 Mbps stream and 30 receivers, teacher upload could approach 18 Mbps before overhead. An SFU lets the teacher send a stream to a server which forwards it. The teacher's upload improves; the forwarding traffic still has to be carried somewhere. [mediasoup's SFU overview](https://mediasoup.org/documentation/overview/).

Lower resolution/frame rate, audio-only lessons when appropriate, no automatic recording and a single teacher publisher reduce resource consumption. These can improve the number of classes supported by existing resources; they cannot establish a guarantee of literally unlimited free capacity. A provider/server limit remains separate from School OS's application admission rules.

## Stability: what was actually verified

School OS native video was tested with a local open-source LiveKit 1.13.11 server, a TLS signalling proxy and TCP TURN. One teacher and nine students received real media using the central credentials, with no school-specific media credentials and no learner camera requests. The teacher used one WebRTC connection, and ending the lesson disconnected the students. Separate-school access and room isolation were also tested.

Those tests establish that the central integration works. They do not establish uptime for Google, Jitsi, Oracle, Cloudflare, Daily or LiveKit Cloud, or capacity for your Nigerian internet connections. No provider account was created, no paid plan purchased and no live school data sent through those providers during this research.

## Decision

For immediate, no-extra-hosting-cost classes within the stated limits, use the existing Google Meet invitation flow. For native portal video without software subscription fees, use the new central configuration with self-hosted LiveKit on infrastructure you can obtain and operate within budget, including an eligible free VM if available. For a larger hosted free pilot without operating a media server, Cloudflare Realtime SFU is worth a separately tested adapter—not an assumption that it is already implemented or indefinitely free.

Provider allowances and terms can change. The comparison is dated above; verify the selected account's actual allowance and billing behaviour before enabling it for all schools.
