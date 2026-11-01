# EP01 — THE SPLITTER
**Concept:** queues · service time · throughput vs latency · utilisation
**Machine:** a log splitter fed by a chute, in the forest
**Runtime target:** ~2:10 · 1080×1920 · 30fps
**Mascot lines marked `[M]` — mascot undesigned, lines are swappable.**

**The one thing a viewer should leave with:**
> The machine never got slower. The *wait* got longer. "It's slow" is almost
> always a queue, not a slow machine.

---

| # | t | VO | Machine | HUD | Mascot |
|---|---|---|---|---|---|
| 1 | 0:00 | **SPARKS:** Nothing here is broken. | Logs piled over the frame, chute jammed, splitter grinding | `QUEUE 1,482` · `WAIT 24m` | OVERLOADED, whistling |
| 2 | 0:05 | Everything is working exactly as designed. That's the problem. | Hold. Pile still growing | `QUEUE 1,509` | still blowing |
| 3 | 0:10 | *(title card)* | Hard cut to empty bench. Splitter alone | — | idle |
| 4 | 0:14 | One splitter. One log at a time. | Single log slides in | `IN 1` · `OUT 0` | idle |
| 5 | 0:19 | Two seconds to split a log. That's your service time. | Log splits, halves drop out. Timer ticks 2s | `SERVICE 2s` | idle |
| 6 | 0:25 | Two seconds each means thirty logs a minute. That's your ceiling. | Counter rolls to 30 | `MAX 30/min` | thin steam |
| 7 | 0:31 | It never moves. You can shout at it. It is still thirty. | Sparks shouts at splitter. Counter unmoved | `MAX 30/min` | amused |
| 8 | 0:36 | Send twenty a minute, and the chute stays empty. | Logs flow through smoothly, nothing accumulates | `IN 20/min` · `QUEUE 0` · `WAIT 2s` | calm |
| 9 | 0:43 | **[M]:** SO SEND THIRTY. IT FITS. | Mascot shoves the feed lever up | `IN 30/min` | eager |
| 10 | 0:47 | **SPARKS:** It fits. Watch the pile. | Logs arrive exactly as fast as they leave | `IN 30/min` · `QUEUE 0→3` | confident |
| 11 | 0:53 | Nothing is late. Then one log arrives a half-second early. | One log arrives early. Pile: 4 | `QUEUE 4` · `WAIT 8s` | flicker of doubt |
| 12 | 0:59 | And the pile never goes back down. | Pile climbs steadily. Splitter rhythm unchanged | `QUEUE 11` · `WAIT 22s` | rattling |
| 13 | 1:06 | At a hundred percent, you have no slack. Every hiccup is permanent. | Utilisation bar pinned at 100%, pile climbing behind | `UTIL 100%` · `QUEUE 40` | rattling hard |
| 14 | 1:13 | **[M]:** IT'S SLOWING DOWN! | Mascot points frantically at splitter | `WAIT 1m 20s` | panicking |
| 15 | 1:17 | **SPARKS:** It isn't. | Close on splitter: still 2s, metronomic | `SERVICE 2s` · `SERVICE 2s` | confused |
| 16 | 1:22 | It has split a log every two seconds all day. It will do it tomorrow. | Timer locked at 2s. Pile towers behind it | `SERVICE 2s` · `QUEUE 212` | small |
| 17 | 1:29 | The machine is not slow. The **line** is long. | Split screen: splitter steady / pile enormous | `WAIT 7m` | quiet |
| 18 | 1:36 | That's the part people get wrong. They go buy a faster splitter. | Shiny new splitter wheeled in, 1.5s | `SERVICE 1.5s` · `MAX 40/min` | hopeful |
| 19 | 1:43 | It buys you ten logs a minute. The forest sends sixty. | Pile resumes climbing, slower, still climbing | `IN 60/min` · `QUEUE 180↑` | sagging |
| 20 | 1:50 | You cannot out-build arrival. You can only refuse it. | Sparks drops a gate across the chute. Logs stop | `GATE CLOSED` · `QUEUE 180→` | relieved |
| 21 | 1:57 | **[M]:** ...so where do the refused logs go? | Mascot peers up the chute. Beat of silence | `REJECTED 1,402` | dawning horror |
| 22 | 2:03 | **SPARKS:** *(delighted)* They come back. | Hard cut to black. Distant rumble building | `INBOUND ???` | — |

---

## Notes
- **Beat 15 is the episode.** Everything before sets up the reveal that service
  time never changed. Don't rush 13→17; that's the turn.
- **The splitter's rhythm is a metronome** — the same 2s clack from beat 5 to
  the end, never varying. The audio is the argument: the viewer *hears* that
  the machine didn't slow down while watching the pile explode.
- **Beat 7 is the only joke.** Keep it dry. Sparks is amused, not zany.
- Cover frame: **beat 16** — tiny steady splitter, enormous pile.
- Caption the terms exactly once each, on screen, when first said: *service
  time* (5), *throughput* (6), *utilisation* (13), *backpressure* (20).
