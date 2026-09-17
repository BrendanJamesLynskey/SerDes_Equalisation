# Equalisation in High-Speed Serial Links

Deck 03 of the [Matrix Methods in Engineering](https://github.com/BrendanJamesLynskey/Mathematics#linear-algebra) series.

**Live presentation:** https://brendanjameslynskey.github.io/SerDes_Equalisation/

One real channel, characterised and then equalised all the way to a link budget.
28.8 inches of differential stripline across two line cards and an 18-inch
backplane, carrying 28 GBd — worked through from the S-parameters to the pulse
response, through every equaliser block, to a budget that says the link lands
**1.36 dB short** of a 10⁻¹² error rate. The deck then prices seven candidate
remedies and finds that the obvious one — more equalisation — is worth a fifth
of what changing the board is worth.

Every number in the deck and the PDF is computed by the channel model in
[`serdes_model.py`](https://github.com/BrendanJamesLynskey/Matrix_Articles), not
asserted: the channel is an ABCD cascade of lossy transmission-line sections,
vias, connectors and an un-backdrilled via stub; the pulse response comes from an
IFFT of the resulting S<sub>dd21</sub>; and the CTLE, transmit FFE and
decision-feedback taps are designed against that pulse response.

## What's inside

- What closes an eye — loss, reflection, crosstalk, jitter, and which block fixes each
- A short history: XAUI → 10GBASE-KR → CEI-28G → PAM4 and mandatory FEC → ADC-DSP receivers → 224G
- The same problem on every other bus — PCIe 1.0 through 7.0 and its negotiated preset table, USB4's PAM3, SAS, InfiniBand, and UCIe at the far end of the reach axis
- Laminates by generation: FR-4 through Megtron 7, with Dk, Df and dielectric loss per inch, plus copper roughness, glass weave, and why the RF laminates (RO4350B and the PTFE grades) are not the answer despite being lower loss
- The channel characterised: stackup, lengths, insertion and return loss, mode conversion
- **Interactive:** the via stub — a 110 mil barrel puts a λ/4 notch within a percent of Nyquist
- From S-parameters to a pulse response: cursor, pre-cursors, post-cursors, and the closed eye in numbers
- The four equaliser blocks and what each one costs — CTLE, transmit FFE, receive FFE, DFE
- **Interactive:** the whole chain — CTLE setting, transmit FFE, DFE taps and crosstalk, with a live noise budget, Q and BER
- The worked design stage by stage, in both millivolts and normalised to the cursor — which blocks must shrink the cursor and why, and what actually falls monotonically (signal-to-noise, not the cursor)
- Tap values and eye diagrams
- The noise budget, and why reading it before choosing a fix matters
- Seven remedies priced in dB: the board buys 1.5–2.5 dB, the silicon buys 0.26–0.46 dB
- The same channel at 56 Gb/s PAM4: where the 9.5 dB goes, and why FEC stopped being optional
- Adaptation, link training, and how the CDR and the equaliser fight
- Where this is going: MLSE, soft-decision FEC, co-packaged and linear-drive optics

## Long-form companion

The same material as a written report:
[SerDes_Equalisation.pdf](SerDes_Equalisation.pdf) (19 pp).

## Companion decks

- [Matrix Methods in Network Parameters](https://github.com/BrendanJamesLynskey/Matrix_Methods_Network_Parameters) — S, Z and Y, mixed-mode, passivity, the Smith chart
- [Matrix Concepts in Digital Filter Design](https://github.com/BrendanJamesLynskey/Matrix_Concepts_Digital_Filters) — state-space stability, Wiener–Hopf, paraunitary banks

Single-page HTML, KaTeX-rendered maths, no build step. Open `index.html` directly.
