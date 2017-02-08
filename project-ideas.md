# Project ideas 2017

## Information for students

These ideas were contributed by our developers and users.
They are sometimes vague or incomplete.
If you wish to submit a proposal based on these ideas, you may wish to contact the developers and find out more about the particular suggestion you are considering.

Being accepted as a Google Summer of Code student is quite competitive.
Accepted students typically have thoroughly researched the technologies of their proposed project and have been in frequent contact with potential mentors.
Simply copying and pasting an idea from here will not work.
Likewise, creating a completely new idea without first consulting potential mentors is unlikely to work out.

If there is no specific contact given you can ask questions on the [Clojure mailing list](http://groups.google.com/group/clojure) or the [Clojurians slack](http://clojurians.net).

## Adding a proposal

The preferred way to add a proposal is to submit a pull request with your idea added to this document.
Please add your idea to one of the sections below (create a new section if you like) using the following template:

```markdown
#### Project Title

**Brief explanation:**
A few sentences describing the problem to solve.

**Expected results:**
What should the student be able to produce by the end of the project.
This includes tests and documentation.

**Knowledge prerequisite:**
If a student needs to know something to be able to complete the project, be sure to list it.

**Mentor:**
Add your name if you are a developer who is willing to be a primary or secondary mentor for the project.
```

If you cannot submit the project as a pull request, please submit it to:

* The [#gsoc](https://clojurians.slack.com/messages/gsoc/) channel in the [Clojurians slack](http://clojurians.net)
* The [Clojure mailing list](http://groups.google.com/group/clojure) using the subject prefix `[GSoC Idea]`.


## Project ideas

### Clojure

#### Single-pass Clojure compiler, in Clojure

**Brief explanation:**
We need to bridge the gap between the original Clojure compiler
(written in Java) and the nanopass approach given by `tools.emitter`.
The former is fast but hard to configure, while the latter is
slow but very configurable.
A missing middle ground is a port of Compiler.java to Clojure,
that is fast, but configurable.

**Expected results:**
A fully featured single-pass Clojure compiler.

**Knowledge prerequisite:**
Extensive experience with compiler writing. Knowledge of
JVM bytecode. Familiarity with Clojure compilation issues.

**Mentor:**
Ambrose Bonnaire-Sergeant

#### Automatically Spec'ing Code

**Brief explanation:**
The recent emergence of clojure.spec has raised the question
of how to spec existing code. Recently, attempts have been
made to generate specs from unit tests. This project
continues that work, adding support for more interesting
spec invariants and spec evolution alongside project
changes.

**Expected results:**
A tool for users to run over existing code to generate
specs, and evolve existing specs.

**Knowledge prerequisite:**
The student should have an extensive knowledge of clojure.spec
and be familiar with Clojure idioms, data structures, and
runtime.

**Mentor:**
Ambrose Bonnaire-Sergeant

### ClojureScript

#### Self-hosted core.async

**Brief explanation:**
Currently, the Clojure and ClojureScript implementations of core.async
have very different implementations. This project aims to merge them
via a unified AST format.

**Expected results:**
The student should convert the internals of core.async to .cljc
files, that can easily be bootstrapped.

**Knowledge prerequisite:**
Experience with `tools.analyzer` AST formats, familiarity with the
implementation of core.async.

**Mentor:**
Ambrose Bonnaire-Sergeant

### Typed Clojure

#### ClojureScript type checker

**Brief explanation:**
The lack of static type checking in ClojureScript
is a glaring difference
compared to Flow, Dart, and TypeScript.
Typed Clojure has preliminary support for ClojureScript,
but it has many issues. This project aims to bring static
type checking in ClojureScript to an acceptable level.

**Expected results:**
A usable type checker for ClojureScript.

**Knowledge prerequisite:**
Extensive knowledge of the ClojureScript analyzer and
compilation pipeline. Knowledge of the features of
Typed Clojure, including occurrence typing and 
local type inference. Familiarity with the implementation
strategy of Typed Clojure's type checker.

**Mentor:**
Ambrose Bonnaire-Sergeant

#### Semantic Subtyping

**Brief explanation:**
Recent advances in semantic subtyping have shown
how to made a practical type system with unions,
intersection, and negation types.
This project aims to integrate this work in Typed Clojure,
to better support negation types and improve error messages.

**Expected results:**
A semantic subtyping algorithm for Typed Clojure types.


**Knowledge prerequisite:**
Knowledge of semantic subtyping papers, including
Castgna et. al, POPL'15; and references.
Knowledge of Typed Clojure's implementation strategies,
and occurrence typing.

**Mentor:**
Ambrose Bonnaire-Sergeant

#### Extending Annotation Generation

**Brief explanation:**
Typed Clojure annotations must currently be hand written.
Recent work has added support to generate types by instrumenting
functions and exercising them with unit tests.
This project extends the existing work with better support
for reconstructing recursive types, inferring polymorphic types,
and giving a better story for evolving existing annotations.

**Expected results:**
Extensions to Typed Clojure improving user-facing tooling
to generate annotations.

**Knowledge prerequisite:**
Knowledge of Typed Clojure's base types.

**Mentor:**
Ambrose Bonnaire-Sergeant

#### Transducers

#### Mixed variable parameters

**Brief explanation:**
The behaviour of `clojure.core/comp` is a fascinating display
of why type checking Clojure is a challenging task.
This project aims to make similar higher-order functions,
(like `comp`, `partial`, `apply`, `list*`, `some-fn`, `every-pred`)
type checkable _in the general case_, in a similar way
variable parameters are used in `map`'s type annotation.

**Expected results:**
Extensions to Typed Clojure that supports some number
of the previously mentioned functions, in the general case.

**Knowledge prerequisite:**
Familiar with Typed Clojure's implementation, including
occurrence typing and local type inference.
Understands why the previous functions are difficult to 
type check.

**Mentor:**
Ambrose Bonnaire-Sergeant

#### Type checking complicated map operations

**Brief explanation:**
Currently `update-in` is not checkable in Typed Clojure.
Building on previous GSoC work, this project aims to 
extend the base types to reify map operations like
`assoc-in` and `get-in` at the type level, so we can
build the type of `update-in`.
We will then answer the second the question: how to
infer polymorphic applications of `update-in`.

**Expected results:**
Higher-order usages of `update-in` are type checkable
using compositional infrastructure, such that users
can type simple variations on `update-in`.

**Knowledge prerequisite:**
Expert in occurrence typing. Well-versed in existing idioms
around hash maps in Clojure. Familiar with existing solutions
for type checking hash maps in Typed Clojure.

**Mentor:**
Ambrose Bonnaire-Sergeant

#### Spec integration

**Brief explanation:**
Spectrum has prototyped using clojure.spec specs to drive static type
checking. Clojure.spec annotations are quickly becoming more
available than Typed Clojure annotations; this project takes advantage
of this fact and aims to add support for Clojure.spec annotations
to double as Typed Clojure annotations.

**Expected results:**
An extension to Typed Clojure supporting Spec's as annotations, for
local control flow and top-level annotations.

**Knowledge prerequisite:**
Experience with building type checkers. Deep knowledge of clojure.spec.
Familiarity with Typed Clojure types.

**Mentor:**
Ambrose Bonnaire-Sergeant

### Tooling

**Brief explanation:**
Port the `boot-clj` task and/or fileset abstractions to ClojureScript so that it can run on Node.JS.
Part of the porting would be to dive into the boot source code and produce a set of `.cljc` files that are implementing the task [DSL](https://github.com/boot-clj/boot/wiki/Task-Options-DSL), macros, command line parsing and middleware chaining.
The fileset abstraction would be a bit more complicated because it would need to abstract (async) IO calls. so probably that can be left as a bonus.

**Expected results:**
A standalone library or a `boot-clj` PR with `.cljc` files.


**Knowledge prerequisite:**
Familiarity with Clojure and Node.JS.

**Mentor:**
Maybe secondary, after `boot`'s folks, but I can help. Andrea Richiardi (a.richiardi.work@gmail.com).

#### Add cool features to KLIPSE

**Brief explanation:**
[KLIPSE](https://github.com/viebel/klipse) is a clojure[script] web repl and also a javascript tag that transforms static code snippets of an html page into live and interactive snippets. It uses self-host clojurescript for evaluating clojure code inside the browser.

There a plenty of cool features in KLIPSE backlog. Here are a couple of ideas: code completion, source code search, full integration with github gist, literate programming and more...

If you have other ideas, you are welcome to suggest them.

**Expected results:**
Implement several features.
Write blog posts demonstrating the features you have added.

**Knowledge prerequisite:**
Familiarity with clojure.

**Mentor:**
Yehonathan Sharvit as a primary mentor - email: viebel@gmail.com

#### Self-host clojurescript migration

**Brief explanation:**
Make popular clojure[script] libraries self-host compatible.

Self-host clojurescript is the compilation of clojurescript code inside clojurescript. It was introduced in [July 2015](http://swannodette.github.io/2015/07/29/clojurescript-17) but yet not all the popular clojure[script] libraries are self-host compatible. 

When a library is self-host compatible it can be used inside a clojurescipt repl like [planck](https://github.com/mfikes/planck), [lumo](https://github.com/anmonteiro/lumo), [klipse](https://github.com/viebel/klipse) and many more...

Here are some clojure[script] libraries that are not yet self-host compatible: [core.matrix](https://github.com/mikera/core.matrix/), [core.logic](https://github.com/clojure/core.logic), [sablono](https://github.com/r0man/sablono), [rum](https://github.com/tonsky/rum).

**Expected results:**
A pull-request to the github repo of one or more clojure[script] lib that has been made self-host compatible.
A blog post with interactive code snippets demonstrating the usage of the library - using [the klipse plugin](https://github.com/viebel/klipse) like this blog posts about [core.match](http://blog.klipse.tech/clojure/2016/10/25/core-match.html), [clojure.spec](http://blog.klipse.tech/clojure/2016/05/30/spec.html) and [om.next](http://read.klipse.tech/om-next-interactive-tutorial/).

**Knowledge prerequisite:**
Familiarity with clojure macros.

**Mentor:**
Yehonathan Sharvit as a primary mentor - email: viebel@gmail.com.
