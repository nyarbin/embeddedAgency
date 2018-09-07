I am what the AI safety community would probably call an AI skeptic, although I do believe that
agents created by humans with significantly more capability than an individual human can be quite
dangerous, but can also be usefully studied in theory in order to work out how to handle them. I
read several popular essays arguing that machine or computer intelligence is of particular concern,
or is the entirety of the hypercapable agent problem, and have repeatedly come away unconvinced, as
the arguments were generally fairly similar. In general, the claim seems to be that (1) intelligence
is unbounded above, or effectively so, (2) if an agent can construct an agent more intelligent than
itself, that growth is subject to exponential returns in the intelligence of the constructed agent
and value to the constructing agent, (3) extreme intelligence implies extreme capability on short
timescales, and finally (4) this sort of "intelligence explosion" has not occurred in human history,
and is uniquely enabled by electronic computing technologies. Support for this line of argument, or
something like it, seems to be growing, but I remain unconvinced.

I have various specific objections to all of the above claims, but I do not wish to cleave to my
skepticism out of simple stubbornness or to change my mind based on shifting poll results. To that
end, I am attempting to formalize my objections and develop a firm theoretical grounding for my
counterclaims, but I've been having difficulty framing my arguments and claims in a formal way. I'd
appreciate help doing so from anyone with experience in computation and complexity theory; this work
also has important connections to physics, economics, and game theory, so I expect that anyone
knowledgable on those subjects could assist in some way. Below is an informal sketch of my ideas and
arguments; my halting and scattered attempts to formalize them can be found in the "results"
directory.

This work involves a number of questions proposed in Soares and Fallenstein's research agenda
proposed in 2017. Specifically, it implicates most of section 2 of that paper, directly or
indirectly, in how the universe is modelled and how agents' approval relations are defined.

Working Definition of an Agent
##############################

An "agent" is an abstract machine with particular properties implemented on another computing
machine. The implementing machine, called the "universe", is a Turing machine or equivalent
structure, and the agent is a linearly bounded automaton (or equivalent) with two extensions.

The first extension is a "sensor", which can transfer data into the agent's memory from other parts
of the universe. The second is an "actuator", which can respond to changes in the agent's memory by
changing other parts of the universe. An LBA with sufficiently powerful sensors and actuators can
give itself arbitrary additional sensors and actuators, and with arbitrary sensors and actuators can
arbitrarily extend its memory, allowing it to bootstrap itself to TM-level computational power. Only
LBAs with this bootstrapping ability (and the computational structures discussed below) are agents
for our purposes.

This bootstrapping means that any agent which is at least as powerful as an LBA can in principle
bootstrap itself up to the computational power of the universe containing it. Agency in universes
of degree greater than **0'** should likely be explored in the future, but for now this is not a
focus of mine. Trivially, we live in a universe of degree at least **0'**, and humans are agents of
degree at least **0'**, so this seems to be the most important Turing degree to explore.

Computationally, the agent contains a model of the universe's current state, a model of the
universe's dynamic properties (its physics), and some representation of a desired state of the
universe. The agent can use its models to decide on a course of action that will bring the universe
into (or close to) the desired state, enact that plan with its actuator(s), and check the results
with its sensor(s), updating the models based on the difference (if any) between the expected
results and the actual results. This update and assesment process is very important and in need of
attention. I have the beginnings of a model which I call the approval relation; it is worth noting
that, unlike the "utility" concept, my model does not require that the agent's desires to have
reached an equilibrium state or constitute a function from universe state to degree of approval. It
can also clearly identify the problem with goals like that of the paperclipper, and some of the
degenerate results of altruistic utilitarianism.

Time, Space, Locality
#####################

TMs and cellular automata have natural, obvious notions of time (rule applications, which I call
ticks) and space (memory cells). These make it easy to show that they have a locality property:
the state of a particular region r at time t can only affect or be affected by that of a specific
region r' for any finite time interval. In TMs and CA, there is a bijection from every region r to
another region r' for each time interval, and the region r' is always a superset of r. I believe
this is true for any universe of degree **0'**, but I'm not sure whether that's trivially true from
the fact that TMs and CAs obey the principle of locality, provable, or simply false.

Characterizing the Universe from Within
#######################################

Conceptualizing space as a collection of memory cells with adjacency relationships leads fairly
straightforwardly to characterizing regions of space by the data they contain and how that data may
change, and from there to discrete objects which can move around. For more, look into "digital
physics" and strip out all the philosophical hand-wringing. I've done some work on this already, but
I recently came across the digital physics wikipedia page and believe I may have been duplicating
work that has been ongoing for more than fifty years.

Limitations from Embedding
##########################

Most interesting properties of agents come from the limitations they are subject to due to the fact
that they are embedded within the universe they are modelling. It is clear to me that agents are
subject to tradeoffs between and limitations to speed, precision, accuracy, and scope in predictions
they make about the universe, and that predicting other agents is particularly difficult, for
reasons that boil down to the fact that the universe cannot run a simulation of itself faster than
its own clock speed. That in turn I believe is closely related to the halting problem, although
other avenues of proof seem like they'd be more fruitful. However, I'm having a great deal of
trouble formalizing my reasoning on these areas. It's here that I would most immediately like help.

I also doubt that baysian or probabalistic reasoning is sufficient to escape these tradeoffs in a
reliable way, since SAT and bayesian inference, even approximated, are both NP-hard problems,
implying a fairly significant upper bound on speed for any sort of predictive reasoning and
decision-making.

Measuring Agent Power
#####################

Yudkowskian focus on "intelligence" as an agent property is (somewhat) misplaced. The relevant
metric in comparing agents is something I call capability, a problem-specific property that
incorporates intelligence, prior knowledge, sensory acuity, and what I've been calling action
economy (a concept with enough distinct components that it too might be worth subdividing). Agents
like the paperclipper, the 17-rule genie, and the like are defined to be superintelligent, but are
more relevantly hypercapable: they can reliably bring a very large region of space into accord with
their goal(s) very quickly.

The hypothetical "AI foom" is not a significant concern for humans as long as human population
remains large and social/economic graphs remain dense. As soon as a machine agent starts copying
itself, it must deal with all the same value drift problems that humans face creating machine agents
in the first place. Such copying is thus not a uniquely relevant as a source of unfriendly agents.
Similarly, a hypothecized more intelligent agent created by humans will not necessarily lead to a
cascade of ever-more-intelligent agents being created because of the value drift problems. If humans
are able to notice the issue and attempt solutions, so can any created AI. If the agent is not able
to generate an absolute solution (or no such solution exists, which I believe is likely),
constructing a more intelligent agent is a poor strategy for accomplishing the agent's goals, just
as it would be for humans. The "AI foom" concept further assumes that intelligence is unbounded
above, which is likely either an illformed statement or simply false, as discussed above.

All superintelligent agents (for reasonable definitions of superintelligence) can be expected to
achieve hypercapability at some point absent intervention, but those with extremely limitted action
economy (the "boxed" AI and friends) will take much longer to do so than other kinds of agents. This
sort of boxed AI is neither a significant concern for AI safety nor particularly useful, and is thus
not likely to be built in the first place, for the same reason that building a house without the use
of power tools is both safer for the construction crew and not a worthwhile way to build a house
given the availability of such tools.

Composite Agents and Interaction
################################

Agents make enourmous effective gains in all components of capability when they act in concert with
other agents. Communication, transient cooperation, and defection are important baseline areas of
study when dealing with the effects and incentives of agent interaction, but these ultimately have
relatively little relevance to the real world. That said, it is probably worthwhile to examine
closely the results related to Aumann's agreement theorem and the meaning of "agreement" in that
context.

Vastly more important are composite agents. Composite agency is a description of a particular
strategy that agents can perform when other agents are available, where the agents agree to
coordinate their actions in order to move the universe to a state that is closer to their individual
goal states. The composite agent has a goal state that amounts to an averaging of the constituent
agents' goal states, and can substantially improve on the action economy and general capability of
the constituent agents, but can have uncontrolled or unanticipated negative effects as well. The
study of composite agents, implicit and explicit, is a vastly more important in solving problems
caused by hypercapable agents, since composite agents are naturally hypercapable and already exist
in the form of governments, corporations, associations, tribes, and other groups acting in concert
of varying degrees of explicitness, deliberateness, and permanency. The emergence of such groups in
new forms likely explains the two previous "singularities" apparent in human history (the
agricultural and industrial revolutions).
