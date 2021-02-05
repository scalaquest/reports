# Sprints Historical Overview

In this document keep track of what we have done in the last Sprints (not the
current). It is an historical document linking the issues and pull request that
we opened or used in a given Sprints, so that we have an historical unique entry
point for the work we have done.

The typical Sprint in our organizaion should last a week, but the first ones
have a different duration as they are done into the holidays.

## Sprint 0 (21st December - 24th December)

This is not exactly a real Sprint, but a first basic footprint for the future
work (this is the reason for name "Sprint 0"). We made a lot of internal
meetings to define context bounds and do knowledge crunching.

Precisely, we started doing some vague knowledge chrunching sessions from the
submission of the project on the 6th of December, but we started making some
heavy effort from the 24th.

In addition, we set the foundations of the project, by giving the Gradle
Subproject Structure, setting up the test framework (ScalaTest) and starting
setting up the CI.

Useful links:

- [(Issue) Project skeleton, Gradle sub-projects and test infrastructure](https://github.com/scalaquest/PPS-19-ScalaQuest/issues/1)
- [(Issue) CI infrastructure (Scala + Gradle)](https://github.com/scalaquest/PPS-19-ScalaQuest/issues/3)
- [(Issue) Basic application structure: traits and relations](https://github.com/scalaquest/PPS-19-ScalaQuest/issues/5)
- [(Issue) Check style in a split job in CI](https://github.com/scalaquest/PPS-19-ScalaQuest/issues/11)

## Sprint 1 (24th December - 2nd January)

Here is how we really start the group work, splitting the team into two
sub-teams, each one working into a different part of the project. We proceeded
in parallel mostly, but we have done some intermediate meetings for integrate
parts and solve common problems. The two parts are in progress yet, and they
will be finished in the next Sprints. In addition, some minor tasks have been
finished during the Sprint.

Roles:

- **Team 1**: @maldins46, @corinz97, @ThomasAngeliniUnibo: in charge of
  developing the `Model` basics, and linked to it, also the `Interpreter` and
  `Resolver` components;
- **Team 2**: @lippo97, @francescogorini: in charge of developing the Prolog
  engine basics, and linked to it, also the `Parser` and `Lexer`components.

Useful links:

- [(Issue) Change Effect keyword to StateUpdate?](https://github.com/scalaquest/PPS-19-ScalaQuest/issues/8)
- [(Issue) Spotless problems](https://github.com/scalaquest/PPS-19-ScalaQuest/issues/13)
- [(Issue) Deepen model, interpreter and resolver component](https://github.com/scalaquest/PPS-19-ScalaQuest/issues/7)
- [(Issue) Deepen Prolog engine, parser and lexer components](https://github.com/scalaquest/PPS-19-ScalaQuest/issues/6)
- [(Issue) Sprint overview document](https://github.com/scalaquest/PPS-19-ScalaQuest/issues/19)

## Sprint 2 (3rd January - 9th January)

In the second Sprint we basically continued the work started in the first one,
divided in teams. Tasks regarding model and Prolog engine are two of the most
funding part of the project, and as such they deserve particular attention. In
particular, we have carried on various meeting to take some decisions about how
to use the model in a more functional way, as described in the linked issue.

Useful links:

- [(Issue) Rename Update into Reaction](https://github.com/scalaquest/PPS-19-ScalaQuest/issues/17)
- [(Issue) Deepen model, interpreter and resolver component](https://github.com/scalaquest/PPS-19-ScalaQuest/issues/7)
- [(Issue) Deepen Prolog engine, parser and lexer components](https://github.com/scalaquest/PPS-19-ScalaQuest/issues/6)

## Sprint 3 (10th January - 16th January)

In the third Sprint we basically continued the work started in the previous,
divided in teams. Tasks about Model and Engine basic structure are basically
finished. We handled merge conflicts about the two parts during the Sprint
Review. In addition, some minor tasks have been resolved in common meetings.

Useful links:

- [(Issue) Deepen model, interpreter and resolver component](https://github.com/scalaquest/PPS-19-ScalaQuest/issues/7)
- [(Issue) Deepen Prolog engine, parser and lexer components](https://github.com/scalaquest/PPS-19-ScalaQuest/issues/6)
- [(Issue) Improve Scaladoc format rules](https://github.com/scalaquest/PPS-19-ScalaQuest/issues/29)

## Sprint 4 (17th January - 23rd January)

In this Sprint we closed the base structure tasks of the previous Sprint, and we
continued working divided in teams: we finished Model's ScalaDoc and
refactoring, and started a re-organization of the `ItemRef` concept, as an `AST.
Additionally, we started some minor tasks, as an automation structure for the
report, and CI optimization.

Useful links:

- [(Issue) Re-organize Model packages, ScalaDoc](https://github.com/scalaquest/PPS-19-ScalaQuest/issues/35)
- [(Issue) Represent ItemRefs as an ADT](https://github.com/scalaquest/PPS-19-ScalaQuest/issues/30)
- [(Issue) Report basic structure](https://github.com/scalaquest/PPS-19-ScalaQuest/issues/20)
- [(Issue) CI optimization](https://github.com/scalaquest/PPS-19-ScalaQuest/issues/23)
- [(Issue) Improve Scaladoc format rules](https://github.com/scalaquest/PPS-19-ScalaQuest/issues/29)

## Sprint 5 (24th January - 30th January)

In this Sprint we continued working in teams, bringing up more other tasks.
**Team 1** revised the model, dealing with the concept of `MessagePusher` and
`Message`s, improving the ScalaDoc and making some refactoring. In the
meanwhile, **Team 2** started working in a more structured concept of
`ItemDescription` and `Verbs`, as a lexical abstraction for the game concepts.
In addition, the team refactored the `Prolog` generation and some of the related
concepts.

Furthermore, a task has been closed together, regarding a re-organization of the
reports in a Gradle subproject, with a dedicated formatter and Linter for
Markdown.

Useful links:

- [(Issue) Messages and MessagePusher implementation](https://github.com/scalaquest/PPS-19-ScalaQuest/issues/47)
- [(Issue) Dictionary and Prolog Parser refactoring](https://github.com/scalaquest/PPS-19-ScalaQuest/issues/48)
- [(Issue) Represent ItemRefs as an ADT](https://github.com/scalaquest/PPS-19-ScalaQuest/issues/30)
- [(Issue) Reports basic structure](https://github.com/scalaquest/PPS-19-ScalaQuest/issues/20)
- [(Pull request) Set up Markdown subproject](https://github.com/scalaquest/PPS-19-ScalaQuest/pull/46)