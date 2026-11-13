# Exam 2 Topic List (Fall 2026)

[Click here for the practice exam](exam2_practice.pdf)

# Format

- Open notes: bring as much printed material as you want
- Closed computers / phones / everything else
- If you successfully completed the homework assignments, the questions should be easy
- Liberal partial credit applied - if unsure, explain your reasoning (even for multiple-choice questions)

# Topics

Common theme throughout:
- Privacy / Utility tradeoff. Specifically, these are tricks to do better on BOTH!

## Parallel Composition

- Definition / theorem
- Histograms and their sensitivity

When can you use it? when you are working with dijoint chunks of data (e.g.
histograms)
Works on n-d historgrams, but be careful of signal to noise ratio. We still have
utility problems when the bins get too small.

## (ε, δ)-Differential Privacy

- Definition
- Gaussian mechanism
- L1 / L2 sensitivity of vector-valued functions
- Advanced composition: **HAVE THE BIG EQUATION WRITTEN DOWN IN MY NOTES TO
  BRING TO THE EXAM**. Make special note of that one graph where advanced and
  sequential composition are graphed together and show that for smaller
  iterations that sequential is actually better than advanced composition.
- Advantages and disadvantages (e.g. failure probability)


- What does the definition do? : "I don't care about privacy for very
low-probability events".
- reason to use it: (a.) Gaussian Mech and (b.) "advanced composition" (not really)
- L1/L2 sensitivity: sensitivity of vector valued functions, know how to compute these.
- Vector mechanisms: these add noise to entire vector *without* composition.

## Variants of Differential Privacy

- Advantages compared to ε, (ε,δ)-DP
- Rényi DP
- Zero-concentrated DP
- Conversion from variants to (ε,δ)-DP

Use these because they allow gaussian mechanism and tight composition, without
failure probability. Bottom line: this is the one you should use, no reason not
to use it.
- Tight composition: best known theoretical bound on total privacy cost for
  multiple mechanisms combined. Best possible theoretical upper bound for
  composed gaussian mechanisms.


  Know: pricacy paraemteres, composition, gaussian mechanism, and **conversion
  between them**.

## Algorithm Design

- Exponential mechanism: report noisy max: selects the approximately best option
  from a set of options with DP. Privacy cost is independant of the number of
  options in the original set.
- Sparse vector technique: we implemented Above Threshold, which returns the
  first query in a list/streamn whose noisy answer exceeds the threshold, useful
  for finding a clipping parameter. Privacy cost is independant from the number
  of options in the list/stream.
- Splitting the privacy budget

## Differentially Private Machine Learning

- Why machine learning models can memorize sensitive training data
- Gradient perturbation (noisy gradient descent)
  - What is gradient descent
  - What is the format of a linear model
  - How to bound the sensitivity of the gradient (clipping the gradient's L2 norm)
  - Composition issues and best privacy variants

Main issue is overfitting/memorization.

Noisy gradient descent: used for all sorts of models, linear all the way up to
language models.
A linear model is a vector of coefficient with X number of
features/coefficients.

In practice: everyone uses RDP, zCDP, or some other recent variant, because you
often run gradient descent for thousands of iterations, so composition matters a
lot for having better utility.

In practice: sequential < advanced < zCDP/RDP

## Units of Privacy

- Definition (in terms of neighboring datasets)
- Evaluating a unit of privacy: "user-level" vs others
- Common units
  - User-level (individual-level)
  - Row-level (event-level)
  - User-day-level
  - User-month-level
- Transforming the unit of privacy
  - Bounding user contribution & adjusting sensitivity



- be familiar with definitions. Be familiaty with the 1 row = 1 person
  assumption, be careful to take note of when does this assumption hold.
- Contribution bounding: if each person can contribute to k rows, multiply
  sensitivies by k.
- Summation: do clipping AND contribution bounding; sensitivity becomes b * k.