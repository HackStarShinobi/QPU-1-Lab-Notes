# QPU-1 Lab Notes

I built a quantum computer in pure Python — six transmon qubits, a 10 mK dilution refrigerator, microwave pulse control, a TWPA→HEMT readout chain, and honest Monte-Carlo noise. Then I spent a week breaking it on purpose and writing down what happened.

Every chart in this series comes from a real run of the simulator. Every number is measured, not reasoned. Every episode ends with the limits, not just the wins.

## Episodes

1. [I built a quantum computer in pure Python](episodes/01-built-a-quantum-computer.md) — the full machine tour: transmon, 6-qubit chip, 10 mK fridge, microwave control with virtual-Z gates, readout chain, noise. Bell 92%, GHZ-3 81%, Deutsch 4/4.
2. [Measuring T1 with microwaves and patience](episodes/02-measuring-t1.md) — sweep the wait, fit the decay: 102.3 µs measured vs 104.3 programmed.
3. [XY4 vs thermal shock](episodes/03-xy4-vs-thermal-shock.md) — 150 mK collapses T2* 60.3→6.9 µs; XY4 recovers 5.4x. Shock-duration sweep: 12.5x survival stretch.
4. [Every shield has a breaking point](episodes/04-breaking-point.md) — tighter XY4 spacing breaks *earlier*; the methods lesson about biased threshold-crossing.
5. [When error correction actually wins](episodes/05-error-correction.md) — 3-qubit bit-flip code beats the bare qubit ≤ 50 µs, crossover ~70 µs. Plus: the metric that lied (XEB's impossible 5.71) and what replaced it.
6. [The noise is never white](episodes/06-correlated-noise.md) — correlated dephasing: XY4 protects only when τc ≳ 50 µs; below that it actively hurts.
7. [Quantum chemistry is harder than it looks](episodes/07-vqe-chemistry.md) — VQE H₂ matches FCI to 5 decimals in the ideal case; noise drags it 38–96 mHa. One clever ansatz parameter beat six dumb ones.
8. [Coherent errors are silent killers](episodes/08-coherent-errors.md) — systematic miscalibration compounds quadratically (1.81) vs stochastic linear (0.92).
9. [What breaking a fake quantum computer taught me](episodes/09-capstone.md) — the through-line, and what's next: a quantum-playground app.

## The machine

`edison-qpu` — pure stdlib Python, zero dependencies. QPU-1: 6 transmons (2×3 grid), T1 ≈ 104.3 µs, T2* ≈ 60.3 µs, single-qubit fidelity ≈ 99.91%, two-qubit ≈ 98.5%, readout ≈ 96.5%. Honest valuation: capable early-2020s NISQ behavior; practical ceiling ~20 qubits (the 2ⁿ wall is real).

Charts live in [`charts/`](charts/) — all generated from real runs.
