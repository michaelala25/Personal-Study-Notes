# Analogical Problem Solving

By Mark T. Keane, first published 1988

The ideas presented in this book aren't necessarily state of the art research, but may still serve as an interesting background to the topic. It's based on a Ph.D. carried out by Keane at Trinity College Dublin.

## 1 - Prologue

Scientific progress is marked by persistent use of analogical problem solving, as the basis of many important discoveries. However, the mechanism of analogical problem solving itself remains elusive, and its manifestations diverse.

Analogies serve to provide insight into the underlying mechanics of a problem. Analogies can, for instance provide thought experiments supporting a conscious line of reasoning. In other cases, they provide a *sudden insight* for the consolidation of previously incoherent ideas. Some even argue that concept formation as a whole is fundamentally metaphorical or analogical.

Of course, many of the accounts of the utility of analogy are *retrospective*, and don't serve as a reliable study for the mechanism of analogy itself.

Despite the recognition of the importance of analogical thinking, there are a number of question which remained relatively untouched until recently. For example, "how is information retrieved from long-term memory for the formation of analogies?" More fundamentally, "how does a person draw analogy between two domains?" All that is known is the *requisite* criterion of "relational similarity" or "dynamical similarity" between the domains.

### Early Accounts of the Phenomenon of Creativity

Poincaré (1913) talks about how one must accumulate a wealth of factoids and concrete ideas, and then let them gestate in the subconscious, eventually crystallizing into a fundamentally new insight.

Mednick (1962) produced a "rigorous associationist" version of the same idea, called the "Remote Associates" theory. Koestler (1964) built off of this with "bisociative thought", a conceptually richer framework. These conceptual frameworks were developed independently, though in parallel, with applied techniques to *train* creativity, such as Gordon's "synectics".

- What is associationism?

In philosophy, rather than psychology, there exist earlier attempts at understanding analogical thinking. Charles Sanders Peirce proposed three types of reasoning: deductive, inductive, and abductive, the latter of which includes analogical reasoning as a subtype. (Wietzenfeld & Klein, 1979, for a review). Mary Hesse (1966) in her work "Models and Analogies in Science" taxonomized the various types of analogy.

### Keane's Roadmap to Understanding Analogical Problem Solving

The following three topics, in order, are explored in order to elucidate the domain.

1. Issues surrounding the solution of a particular problem by analogical means.
2. How analogies might be remembered or retrieved in solving a problem.
3. The core phenomenon of drawing analogies.



## 2 Theories of Analogy

### Gentner's Structure-Mapping Theory

Introduced by **Dedre Gentner** in the early 1980s. First uses a natural method by which **domains** (systems of interconnected ideas in a specific niche or field) are *represented*, known as **propositional networks**. Propositional networks were introduced by **Dr. Zenon Pylyshyn** in 1973, as means of representing mental relationships between objects.

A **domain** consists of a **propositional network**, which itself is composed of **objects** and **relations between objects**. **Relations** are typically seen as predicates, though I suppose one might also think of them as more general functions (returning not merely a truth value, but an object of any type, such as a number). Objects can possess **attributes**, which are just **unary relations**. **First-order relations** are relations which take objects as their arguments, and **second-order relations** are relations which take first-order relations as arguments (e.g., `Collide(x, y)` is 1st-order, whereas `Cause(Collide(x, y), Break(x, y))` is 2nd-order), and so on inductively. Another example of a 2nd-order relation might be `Propotional(Pressure(Liquid, Source, Goal), Flow-Rate(Liquid, Source, Goal))`. 

* A **predicate** is the *main content verb* of a *declarative sentence*, which takes *arguments* (e.g. in "Frank likes cake", "like" is the predicate).
* A **proposition** is the *meaning* of a *declarative sentence*, typically assumed to bear a *truth-value* (which can be binary, fuzzy, modal, etc.)
* In a proposition, a **referent** is a *thing* to which a certain name is ascribed. For instance, in "Mary saw me", the referent of the *word* Mary is the *actual person Mary*.

Some notes on Gentner's representation of a domain:

1. Sometimes attributes can be seen as *relations* relative to some prototype object (e.g. `Large(x)` is really `Large(x, prototype)`, since it means different things to say "the Sun is large relative to the Earth" vs "the nucleus is large relative to an electron"). In these instances, the attribute is only considered a true *nonunary relation* if the prototype object of consideration is both *relevant to the domain* and *non-constant*.
2. **Decomposition** refers to the phenomenon whereby

#### Mapping of Analogues

According to Gentner's theory, a **base domain** (B) is mapped to a **target domain** (T) via the following rules:

1. The *objects* of B get mapped onto those of T (likely after changing names).
2. The *lower-order* relations of B (1st-order) get mapped to those of T (often *without* changing names).

subject to two important constraints:

1. Attributes tend *not* to be carried from B onto T.
2. (**Systematicity**) the choice of *which* lower order relations are mapped is limited to those which form *systems* of *interconnected higher-order relations*. For instance, if a 1st order relation P(x, y) is mapped over from B into T, and both B and T contain a 2nd order relation R(P(x, y), Q(x, y)), then we can assume Q(x, y) is *also* be mapped from B into T.

#### Syntacticity of Gentner's Theory

It is important to recognize that the *content* of an analogue is highly dependent on the *syntax* in which it is represented. The *choice of words* with which a system is described can influence whether or not a target analogue is a valid candidate for mapping. For instance, one's word choice might necessitate the *decomposition* of an object in the base domain which introduces new structural relations between ideas (thus effecting whether or not systematicity holds between analogues).

In short, the content of an analogue is at best a reductive representation of the content of its referents.

#### Problems with Gentner's Theory

One critique levied against structural-mapping theory is that analogue *retrieval*, a central component in the discussion of analogical problem solving, was *not* one of Gentner's main concerns.

##### The Problem of Object Identification

##### The Problem of Selection

The only real constraint Gentner imposes on the selection of relations for structure mapping is the principle of systematicity, which some scholars argue is inefficient to account for the *selection problem*. A seemingly valid mapping of a domain onto an analogue is sometimes *invalidated* through procedures such as *decomposition* or *the inclusion of extraneous contextual information*. It may appear at a *certain level of organizational structure* that two domains are analogically similar, only for that similarity to disappear once certain objects or object-relations are decomposed or consolidated.

The common response (Gentner, Holyoak, Keane) is that the analogist's *goals* in mapping the domain onto the analogue aid in determining which relations, or more generally which *level of organizational structure*, are relevant to the mapping.

##### The Problem of Validity

Assuming a domain can be structurally mapped onto an analogue, what criteria are used to evaluate the *validity* of said mapping? Without *named relations*, the problem of structural-mapping is in essence no different from the graph isomorphism problem, subject to slightly tighter constraints (systematicity): thus two domains may have *structural components* in common (shared interconnectivity of relations, or shared systems of higher order relations) without the analogue having *any relevance* towards the base domain.

**Gentner's proposal:** A two-step process whereby first a mapping is performed (if applicable) and then a validation check is performed.

##### Problems of Syntacticity

The first two of problems are essentially "problems of syntacticity"; a problem inherent to any situation which rests on the interplay, and eventual equipoise, of the forces of *abstraction* and *accuracy of representation*. To the analogist solving a problem, one aspires to convey *only as much information* as is relevant to capture the *dynamics* and *architecture* of a given domain, such that it is *amenable to mapping onto other analogous domains*. Often there is an added constraint that the source domain structure is "intricate enough" such that one of these new domains admits *lucid extraneities* - new relevant information which is both easily witnessed and can be append to  target domain without altering its inherent structure - such that it can then be mapped *back* onto the source domain in a way which elucidates some latent structure.

Gentner's theory is not a theory about *how this equipoise is achieved* in the base domain. It is merely a proposal for the *representational structure* of ideas, and the constraints on *how a mapping can occur*.

In other words, we have a lot of work to do in determining how object identification and relation selection occurs, and how the *purpose* of an analogy influences these procedures.

### Holyoak's Theory

