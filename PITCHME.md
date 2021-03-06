# fe-dev-catchup-20170707

---

## Agenda

* Akamai training review
* Calibrating our estimations
* Upcoming Projects
* Testing handover refresher
* Functional Test / Integration Test Philosophy
* InitialLaterOr
* Hours
* General Feedback

---

## Akamai Training Review

1. Image Manager
2. Adaptive Acceleration
3. Akamai Instant (prefetching)
4. SureRoute

---

## Estimates

What is a `1` ticket

---

## 1 - Trivial
* Trivial Dev+QA Effort
* No Unknowns
* Examples
    * Updating a small amount of styles
    * Changing copy for a template which already exists
    * Updating a config file
    * Spike with well defined parameters

---

## Upcoming Projects

* Habitual Patterning
* Personalisation
* Resource CMS: Stage 1

---

## Development Process Refresher

---

#### TODO
When:
    * Dev picks ticket from TODO and takes ownership

DEV move to **In Progress**

---

#### IN PROGRESS
When
    * Feature complete
    * QA build created
    * PR created

DEV move to **Peer Review** and _ping PO & UXD_

---

#### PEER REVIEW
When
    * Tests written
    * 2x DEV approvals of PR (including tests code)
    * PO approval of QA build
    * UXD approval of QA build (where appropriate)

DEV move to **QA ready** and _ping QA_

---

#### QA READY
When:
    * QA has tested feature successfully

QA move to **Ready For Release**

When:
    * QA has found bugs & confirmed with DEV

QA move to **In Progress** and _ping dev_

---

#### Ready For Release
When:
    * DEV has squashed PR commits
    * DEV has merged PR to develop branch
    * DEV has created version

DEV move to **QA regression** and _ping QA with version_

---

#### QA Regression
When:
    * QA has regression tested version

QA move to **Awaiting deployment** and _ping DEV_

---

#### Awaiting Deployment
When:
    * DEV has released version on production
    * DEV has updated release calendar
    * DEV has sent release notes to stakeholders

DEV move to **DONE**

---

#### Done
    * Get a ticket from TODO
    * Help others with finishing their ticket
    * Pick up a ticket from developer playground

---

#### Functional Tests

Test Coverage / overlap

---

Using sinon.fakeServer

```
this.sandbox = sinon.sandbox.create({ useFakeServer: true });
this.sandbox.server.respondWith(
    /scoreboard.json/,
    [
        200,
        { 'Content-Type': 'application/json' },
        JSON.stringify(scoreboardData)
    ]
);

this.sandbox.server.respond();
```

---

Using sinon.stub

```
import * as getScoreboard from '../../../../src/js/streams/endpoints/scoreboard';

this.scoreboardResponseBus = new bacon.Bus();
this.sandbox
    .stub(getScoreboard, 'default')
    .callsFake(() {
        return this.scoreboardResponseBus;
    });

this.scoreboardResponseBus.push(scoreboardData);
```

---

### initial Later Or

---

    (initial, stream) => initial ? bacon.later(initial, 0) : stream

    (initial, getStream) => initial ? bacon.later(initial, 0) : getStream()

    just roll your own

---

### Darren 2.0
Meet & greet
Start date: 5 weeks from monday

---

## Gentle reminder about hours:
* Everyone in the office: **between 10am-5pm**
* Running late/leaving early: **let the team know**
* If you do less hours, **make it up another day**
* If you do extra hours, **do less hours another day**

---

# Open / feedback
