# Simulation Lectures

- [x] [Lecture 1](#lecture-1)
- [ ] [Lecture 2](#lecture-2) :construction:
- [ ] [Lecture 3](#lecture-3)
- [ ] [Lecture 4](#lecture-4)
- [ ] [Lecture 5](#lecture-5)
- [ ] [Lecture 6](#lecture-6)

# Lecture 1

## Systems and System Environment:

* System is defined as a groups of objects that are joined together in some regular interaction toward the accomplishment of some purpose.
  - For example: An automobile factory: Machines, components parts and workers operate jointly along assembly line.

* System environment: changes occurring outside the system.
  - Factory : arrival orders
  - Banks : arrival of customers

## Components of a System:

* **Entities:** Elements that often make up the system.
* **Attribute:** A property of an entity.
* **Activity:** represents a time period of specified length.
* **State of system:** is defined to be that collection of variables necessary to describe the system at any time, relative to the objective of the study.
  - In the study of a bank possible state variables are number of busy tellers, number of customers waiting in the queue or being served, arrival and service times of the next customer.
* **Event:** is defined as an instantaneous occurrence that may change the state of the system.
* **Endogenous** – used to describe the activities and events occurring within a system.
* **Exogenous** – is used to describe activities and events in the environment that affect the system.
  - In the bank: arrival of a customer is exogenous event
                 completion of service of a customer is endogenous event.
## Examples on components of a system:

<!-- make it as a table -->
                      Entites     Attributes            Activities             Events         State variables

* Banking System     Customers    the balance           making deposits.     arrival,       The number of busy tellers,
                                                                                            the number of customers waiting in line or being served,
                                                                                            and the arrival time of the next customer.
                                  in their checking                          departure.
                                  accounts.



Examples: Rail System
Entities – Commuters
Attributes – Origination , Destination
Activities – Traveling
Events – arrival at station, arrival at destination
State variables – Number of commuters waiting at each station,
                  number of commuters traveling

Examples: Production System
Entities – Machines
Attributes – Speed , Capacity, Breakdown rate
Activities – Welding, Cutting, Stamping
Events – breakdown
State variables – Status of machines – busy, idle or down

Examples: Communications System
Entities – Messages
Attributes – Length , Destination
Activities – Transmitting
Events – arrival at destination
State variables – Number of messages waiting to be transmitted


## Ways to study a system:

<!-- place image in slide 8 -->

* **Simulation:** is the imitation of the operation of real- world process or system over time.
* A model construct a conceptual framework that describes a system.
* Simulations involve designing a model of a system and carrying out experiments on it as it progresses through time.


## Goal of modeling and simulation:
* A model can be used to investigate a wide verity of “what if” questions about real-world system.
* Simulation can be used as:
  - Analysis tool for predicating the effect of changes.
  - Design tool to predicate the performance of new system.
* It is better to do simulation before implementation.


## Reason for using a model:

1. Helps in understanding the behaviour of a real system before it is built.
2. Cost of building and experimenting with a model is less.
3. Models have the capability of scale time or space in favourable manner.

<!-- make the next two points as a table -->

## When Simulation Is Appropriate:

* Simulation enables study of internal interaction of subsystems in complex system.
* Simulation can be used with new design and policies before implementation.
* Simulation models are designed for training make learning possible without cost disrupting.

## When Simulation Is Not Appropriate:

* When the problem can be solved by common sense.
* If it is easier to perform direct experiments.
* If cost exceed savings.
* If resource or time are not available.
* If system behavior is too complex like human behavior


<!-- make the next two points as a table -->
## Advantages of simulation:

* New policies, operating procedures, information flows and so on can be explored without disrupting ongoing operation of the real system.
* Time can be compressed or expanded to allow for a speed-up or slow-down of the phenomenon (clock is self-control).
* A simulation study can help in understanding how the system operates.
* “What if” questions can be answered.

## Disadvantages of simulation:

* Model building requires special training.
* Vendors of simulation software have been actively developing packages that contain models that only need input (templates).
* Simulation results can be difficult to interpret.
* Simulation modeling and analysis can be time consuming and expensive.


## Areas of application:

1. Semiconductor Manufacturing.
2. Military application.
3. Transportation modes and Traffic.
4. Business Process Simulation.
5. Health Care.
6. Risk analysis.
7. CPU, Memory.
8. Network simulation.

## How to simulate:

1. By hand.
2. Spreadsheets
3. Programming in General Purpose Languages => Java.
4. Simulation Languages => SIMAN.
5. Simulation Packages => Arena.

## Types of Models:

* All models can be grouped into three types:
  1. Graphic models:
    - Conceptual drawings, graphs, charts, and diagrams.
    - Football coaches develop them to show how players (components) should interact during an offensive or defensive play (system).

  2. Mathematical models:
    - Show relationships in terms of formulas.
    - complex mathematical models track storms and space flights, predict ocean currents and land erosion, and help scientists conduct complex experiments.

  3. Physical models:
    - three-dimensional representations of reality => (Model Airplane, Model House, Model City).
    - Two types of physical models exists:
      1. Mock-up: is used to evaluate the styling, balance, color, or other aesthetic feature of a technology artifact.
      - Mock-ups are generally constructed of materials that are easy to work with => wood, clay, Styrofoam, paper, and various kinds of cardboard.
      2. Prototype: is a working model of a system.
      - Prototypes are built to test the operation, maintenance,
      and/or safety of the item and is built of the same material as the final product.

## Types of Models:

* Dynamic vs. Static
* Stochastic vs. Deterministic
* Discrete vs. Continuous

<!-- place image in slide 20 -->

## Characterizing a Simulation Model:

<!-- make this part as a table -->

* Deterministic:
  - No random variable in the model.
  - behavior is predictable.
  - patients arriving at a clinic at scheduled appointment time.

* Stochastic (NON-DETERMINISTIC or PROBABILISTIC)
  - model has one or more random variables as inputs.
  - behavior cannot be predicted.
  - Bank: random customer inter-arrival and service times.

* Static:
  - No time element.
  - Time Independent view of the system.
  - e.g. Class has same number of students in an year.

* Dynamic:
  - Passage of time is important part of model.
  - Time dependent view of the system.
  - E.g. ATM can accept card only when it is in ready state. ATM cannot read card when it is in ERROR state. Thus state of ATM is a dynamic aspect.

* Discrete system:
 - state variables change only at discrete set of points in time (a countable number of points in time).

* Continuous system:
 - the state variables change continuously over time (infinite number of states).


## How to develop a model?

1. Determine the goals and objectives.
2. Build a conceptual model.
3. Convert into a specification model.
4. Convert into a computational model.
5. Verify.
6. Validate.

## Three Model Levels:

1. Conceptual:
  - Very high level
  - How comprehensive should the model be?
  - What are the state variables, which are dynamic, and which are important?

2. Specification:
  - On paper
  - May involve equations, pseudocode, etc.
  - How will the model receive input?

3. Computational:
  - A computer program.
  - simulation language.

## Steps in Simulation Study:
<!-- place image in slide 29 -->
