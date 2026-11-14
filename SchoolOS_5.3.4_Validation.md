# School OS 5.3.4 validation

Local integration validation on 14 November 2026. Synthetic school accounts and test media; no production website changes.

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

## Contract

- Passed: Students cannot schedule a class or control teacher lifecycle
- Passed: Cross-school accounts cannot obtain a lesson or room state
- Passed: Expired or permanently archived lessons cannot be joined or reactivated
- Passed: Create validates 30-minute duration steps on the server
- Passed: Student SFU tokens only allow microphone publishing when the floor grants it
- Passed: Room epochs change across restarts to isolate previously issued join tokens
- Passed: Lesson interactions require a current scoped classroom session

## Sfu

- Passed: One teacher and nine learners join the built-in SFU classroom simultaneously
- Passed: All learner cameras/microphones remain unrequested
- Passed: Teacher uses SFU connections rather than one peer per learner
- Passed: Ending the lesson deletes the media room and disconnects every learner

## P2P

- Passed: Student blocked before teacher starts
- Passed: Student receives real teacher video and audio RTP
- Passed: Student camera/microphone never requested
- Passed: Teacher leaving stops viewer media
- Passed: Teacher restart and student rejoin establish media again
- Passed: Ending lesson stops student connections and teacher tracks on next poll

## Updater

- Passed: Existing 5.3.3 updater recovers every changed file after an injected mid-update failure
- Passed: Original updater installs the complete 5.3.4 package with matching hashes and journal
- Passed: Installing the same version again is refused
- Passed: Explicit rollback restores all original files and 5.3.3 metadata
- Passed: Traversal entries are refused before file changes

589 role-page requests passed without HTTP/PHP rendering errors. 40 PHP/JavaScript syntax checks passed.

Media tests used local LiveKit 1.13.11, TLS signalling and TCP TURN. One teacher and nine students received actual video/audio; a separate four-account scenario exercised floor permissions and classroom interaction. Screen sharing used a synthetic captured board to test publishing, stopping and camera restoration. The operating-system desktop picker, actual school networks, mobile browser capture support and production provider capacity still need acceptance tests.

The update installer was checked for deployment, same-version refusal, injected-failure recovery, explicit rollback and traversal rejection. No credentials, configuration file, private keys or live database are included in the release.
