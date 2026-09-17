# What breaking a fake quantum computer taught me

*QPU-1 Lab Notes, part 9 — the capstone. No new numbers this time. Just the pattern.*

---

Nine episodes ago I built a quantum computer out of Python and spite, because the explainers kept skipping the hardware. Since then I've measured its T1, shocked it with heat, shielded it with pulse sequences, found every shield's breaking point, watched error correction win and then lose, thrown out a lying metric, run chemistry on it, and measured the two kinds of wrong fighting head to head.

I didn't plan a through-line. One showed up anyway.

## Every protection has a breaking point

XY4 was the hero of the early episodes — a pulse sequence that clawed back 5.4x of lost coherence under thermal shock and stretched survival 12.5x in the duration sweep. Then the correlated-noise sweep showed it actively *hurting* when the noise correlation time dropped below ~50 µs. The shield didn't get weaker. The battlefield changed, and nobody told the shield.

Error correction told the same story: the 3-qubit code beats the bare qubit through ~50 µs, then the crossover hits near 70 µs and the "protection" starts costing you. Every protection in this series came with a regime where it works and a regime where it doesn't, and the boundary was always sharper than I expected.

The general lesson isn't about quantum. It's that no defense is universal — every one of them is a bet about what the world looks like, and the bet expires the moment the world changes shape. XY4 bets the noise is slow. The bit-flip code bets the errors are bit flips. Know what your shield assumes, or you'll deploy it exactly where it hurts you.

## Every metric can lie

The XEB episode is the one I think about most. The metric returned impossible values — 5.71, 1.84, numbers that can't exist — and the temptation was to shrug and publish the curve. Instead I threw the metric out and rebuilt the measurement on TVD, which told a humbler, truer story: no depth advantage established through 30 layers.

Metrics don't just measure. They *persuade*. A number with four significant figures feels like a fact, and XEB's impossible values were wearing that costume. The discipline the series kept coming back to — fit the decay, don't threshold-cross the noise; check the reference against PySCF to seven decimals; distrust the clean-looking shallow benchmark — is really one discipline: the instrument is guilty until proven innocent. Including the instrument you built yourself. *Especially* that one.

## Structure beats effort

The VQE night gave me the cleanest version: one clever parameter beat six dumb ones plus thousands of optimizer steps. The 6-parameter hardware-efficient ansatz had more freedom, more compute, more everything — and lost to a 1-parameter circuit that understood the Hamiltonian's block structure.

I've stopped counting how many times this pattern shows up outside quantum. The generic solution with more resources loses to the specific solution with more understanding. Understanding the problem's shape is leverage; effort applied to the wrong shape is just heat. If this series had a single sentence for a student, it'd be that one: learn the structure before you scale the effort.

## Honest limits are the product

Here's the thing I'm proudest of, and it's not a number. Every episode ended with the limits stated plainly: phenomenological noise, not Lindblad; best-case molecules; metrics that got thrown out. The pop-quantum genre runs on hype — "quantum will change everything" over stock footage of a chandelier fridge — and the gap between that and a real device is where public trust goes to die.

The honest version turned out to be more interesting anyway. "VQE is correct in principle and drowned in practice" is a better story than "quantum chemistry is coming." "Your shield hurts you under fast noise" is a better story than "error suppression works." The failures were the content. Every time the machine embarrassed me, the embarrassment was the episode.

That's the real through-line: the simulator's job was never to make quantum look easy. It was to make the difficulty *measurable* — and then to report the measurements straight.

## What's next

QPU-1 isn't retiring. It's becoming something you can hold.

The plan is a quantum-playground app: an interactive quantum lab that runs on your phone, with the real noise physics underneath — the same transmons, the same T1 decay, the same readout chain, the same Monte-Carlo gauntlet. Run a Bell test and watch readout misclassification eat your fidelity. Sweep a Ramsey wait and fit your own T1. Fire XY4 at a thermal shock and find its breaking point yourself, the way I did in episodes 3 and 4. Every experiment in this series becomes a screen you can touch.

Why an app and not a paper? Because the thing this series actually taught — the *habit* of measuring, of distrusting the metric, of looking for the breaking point — isn't learned by reading. It's learned by running the experiment and watching the curve do something you didn't expect. A playground teaches that. A paper just asserts it.

And honestly: the people who'll matter in quantum's future aren't the ones who watched the hype videos. They're the ones who built the intuition early — who know what T2* feels like, why calibration is the highest-paid boring job in the lab, why one clever parameter beats six dumb ones. If this series gave you any of that, the playground is where it compounds.

Nine episodes. One fake quantum computer. Every number real, every limit stated, every shield broken on purpose.

Now go break something yourself.

## What's next (for the series)

- The episode drafts and charts live in the open — code, demos, and all fifteen charts, free to run and argue with.
- Each episode is being cut into a vertical Short: one chart, one number, sixty seconds.
- The playground app spec is next. If you want a particular experiment from this series in it, that's the time to say so.

*QPU-1 Lab Notes is complete. The lab isn't.*
