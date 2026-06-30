# On-Device rPPG Heart-Rate Coach (VisionCardio)

**Role:** end-to-end (data → model → Core ML → iOS app) · **Output:** iOS app + Core ML model + sim-to-real study

## Problem
Estimate heart rate from a **front-facing camera** (remote photoplethysmography, rPPG) and
turn it into useful, *bounded* wellness guidance — entirely **on-device**, with no wearable,
no diagnosis claims, and no hidden background camera use.

## Approach
- **Model:** PhysNet-style rPPG network mapping short face-video clips → pulse signal → heart rate.
- **Training data:** **SCAMPS** synthetic avatars (physiologically-grounded simulated PPG) plus
  **UBFC-rPPG** real recordings; studied the **sim-to-real gap** between synthetic and real faces.
- **Deployment:** exported to **Core ML** (`VisionCardioHR.mlpackage`) and wrapped in a native
  **iOS / Swift** app (`VisionCardio.xcodeproj`) — capture, on-device inference, and coaching all local.
- **Product layer — "PHRM" pattern:** short capture windows + **confidence gating**. The app
  maps HR relative to the user's resting baseline to one of `easy / maintain / push / defer`,
  and **defers instead of guessing** when frames are noisy or occluded.

## Why it's interesting
- Real generalization problem: a model trained largely on synthetic faces has to work on real
  skin tones, lighting, and motion — the project explicitly tracks and mitigates that gap.
- Honest UX constraints baked into the state machine (`idle → ready → capturing → analyzing →
  coaching / deferred`): wellness-only language, explicit permission, confidence-gated output.
- Full vertical slice: dataset engineering → training (W&B-tracked) → Core ML export → shipping app.

## Stack
PyTorch (PhysNet) · SCAMPS / UBFC-rPPG datasets · Core ML / coremltools · iOS · Swift · Weights & Biases.
