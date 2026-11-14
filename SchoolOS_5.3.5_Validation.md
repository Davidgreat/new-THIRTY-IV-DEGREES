# School OS 5.3.5 validation

Local validation completed on 14 November 2026 using synthetic school accounts and test media.

## Waiting Server

- Passed: Initial student Join returns a waiting state with no media token, peer key or participant slot
- Passed: Repeated waiting checks do not consume the admission retry budget
- Passed: Waiting access remains restricted by class, role, lifecycle and joining window
- Passed: direct: host admission stays starting until media-ready, then waiting students can join
- Passed: central: host admission stays starting until media-ready, then waiting students can join

## Waiting Browser

- Passed: central: learner sees a real waiting prompt without camera, microphone or media connection
- Passed: central: leaving cancels an in-flight waiting check
- Passed: Waiting beyond the old retry budget keeps one admission request and continues checks
- Passed: central: teacher media setup does not prematurely admit waiting learners
- Passed: central: learner connects automatically to actual teacher audio/video without clicking Join again
- Passed: central: a late ready response does not reconnect a student who left
- Passed: central: ending a lesson while a student waits stops automatic checking with a clear message
- Passed: direct: learner sees a real waiting prompt without camera, microphone or media connection
- Passed: direct: leaving cancels an in-flight waiting check
- Passed: Waiting recovers automatically after temporary loss of internet
- Passed: direct: teacher media setup does not prematurely admit waiting learners
- Passed: direct: learner connects automatically to actual teacher audio/video without clicking Join again
- Passed: direct: a late ready response does not reconnect a student who left
- Passed: direct: ending a lesson while a student waits stops automatic checking with a clear message

## Studio

- Passed: Duration selector offers 30-minute increments and countdown renders
- Passed: Teacher and learner controls have distinct role visibility
- Passed: A joined student cannot change the speaking policy or create a test
- Passed: Learners initially receive real teacher video/audio without requesting microphones
- Passed: Classroom chat and questions stay inside the running class
- Passed: Reactions reach classmates within the room
- Passed: Raised hands appear and teacher can grant one speaking invitation
- Passed: Selecting another speaker revokes the first learner at the media server
- Passed: Open discussion enables everyone; listen mode locks publishing again
- Passed: Quick checks accept answers, show teacher totals, hide correctness until closed
- Passed: Screen sharing has a distinct stop control and returns to the camera
- Passed: Room stays within mobile viewport
- Passed: Pause disconnects learners and resume permits the same class to restart
- Passed: Ended lesson moves into Past lessons and remains reactivatable in its window
- Passed: Permanent close hides a lesson from current lists and refuses reactivation

## Updater

- Passed: Existing 5.3.4 updater recovers every changed file after an injected mid-update failure
- Passed: Original updater installs the complete 5.3.5 package with matching hashes and journal
- Passed: Installing the same version again is refused
- Passed: Explicit rollback restores all original files and 5.3.4 metadata
- Passed: Traversal entries are refused before file changes

Actual teacher video frames and audio RTP were received automatically by an early-arriving learner in both local LiveKit and direct TCP-TURN modes. A delayed teacher capture permission was held during the test to verify that admission waits until media is ready. Waiting continued through more than ten status checks without repeatedly consuming the Join limit.

The operating-system screen picker, production LiveKit project, actual school internet networks and provider-scale capacity were not tested in this local validation. Browser autoplay policies can still require pressing Play for sound.

Changed PHP/JavaScript syntax and the final ZIP manifest/payload hashes were verified. No private credentials, configuration file, encryption keys, real account data or live database are packaged.
