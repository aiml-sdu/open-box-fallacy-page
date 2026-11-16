# The Open-Box Fallacy

> Markdown version of the project page at https://aiml-sdu.github.io/open-box-fallacy-page/. Interactive figures are on the web page. Every number here also appears there and comes from the paper or its stored results.

Position paper · arXiv 2026

Why AI deployment needs a calibrated verification regime

Deployment in sensitive domains is often held back until a model can be explained from the inside. We argue that the licence to deploy should come from calibrated verification of one specific use, and that this can be reported beside capability scores.

Phongsakon Mark Konrad1, Tim Lukas Adam1, Ane Cathrine Holst Merrild1, Riccardo Terrenzi1, Rebecca De Rosa1, Toygar Tanyel2, Serkan Ayvaz1

1Centre for Industrial Software, University of Southern Denmark 2ProMake, Newark, DE · May 2026

[arXiv](https://arxiv.org/abs/2605.10601) · [PDF](https://arxiv.org/pdf/2605.10601) · [Markdown](index.md) · Cite this article

Ledger · five regimes on six rails

Point at any regime or rail. The paper's own coding, cell for cell.

From Table 2 of the paper. The coding is a diagnostic use of the vocabulary. It is not an empirical measurement and not a legal compliance determination. It scores the surrounding regime, never a model.

## Table 2 of the paper, the ledger

| Regime | Domain Coverage | Verifier Strength | Monitoring Maturity | Accountability Clarity | Contestability | Revocation Readiness |
|---|---|---|---|---|---|---|
| Medicine (FDA CDS; AI/ML devices) | H | H | L | H | M | M |
| Credit (ECOA/Reg. B; adverse action) | H | M | L | H | H | M |
| Employment (NYC LL144; state AI laws) | H | M | M | M | M | L |
| Autonomous systems (critical infrastructure) | M | M | H | M | L | M |
| Criminal justice (post-Loomis) | M | L | L | H | L | L |

H means instantiated by statute, regulation, binding agency process or routine practice. M means partial, voluntary, indirect or unevenly enforced. L means thin, practically inaccessible or not attached to the AI deployment.

## Table 1 of the paper, failure modes and rails

| Deployment problem | Required regime property |
|---|---|
| Capability varies across nearby tasks (§2.1) | Domain-scoped authorization |
| Self-reported evidence may be incomplete or conflicted (§3.1) | Independent checkability |
| Performance can change after release (§5) | Monitoring |
| Harm requires a responsible actor (§2.3) | Accountability |
| Affected parties detect errors evaluators miss (§3.1) | Contestability |
| New evidence should change deployment status (§3.3) | Revocation |

## TL;DR

Mechanistic interpretability can show how a model works. It cannot by itself show that a given use is scoped, monitored and accountable. We call the demand that it serve as the deployment gate the open-box fallacy.

Two facts carry the argument. Capability is uneven across nearby tasks, and in one field experiment consultants using AI were 19 percentage points less likely to solve a task just beyond its reach. Societies have also long licensed opaque experts through credentials, monitoring, liability, appeal and revocation.

Understanding need not become control. One clinical study reports a 53 point gap between hazard information the model represents and what its output corrects. One scoping review found a prospective surveillance study for only 62 of 692 FDA approved AI/ML devices, or 9.0%.

We propose Verification Coverage. It is a profile of six components with a minimum rule, so a single missing rail withholds authorization.

## Abstract

**First,** we name the open-box principle and the open-box fallacy. The principle says mechanistic evidence matters for deployment. The fallacy is the stronger demand that it decide deployment. Transparency is neither necessary when outputs can be checked from outside nor sufficient when the use has no scope, monitoring, accountability, contest path or way to revoke it.

**Second,** we build calibrated verification as the alternative. Four evidence streams feed three verifier classes, and six regime properties follow from six documented failure modes. Authorization attaches to a deployment in a domain and to its deployer of record, never to a model in general.

**Finally,** we propose Verification Coverage as a reportable standard that sits beside capability scores in model cards, leaderboards and regulatory disclosures. Applied to five existing regimes, it shows uneven coverage everywhere, and criminal justice has four thin rails out of six.

**Where it could fail** The position would be wrong if mechanistic understanding reliably turned into correct behaviour, or if regimes with strong explanation demands proved safer than regimes with strong external checks. The paper cites evidence against the first, a 53 point gap between internal representation and output correction. It does not test the second. The scores in its domain table are a reasoned coding, and no one has yet measured Verification Coverage on a deployment.

## Terms

Open-box principle

Mechanistic evidence about how a model produces its outputs is relevant to whether and how it should be used.

Open-box fallacy

The stronger demand that mechanistic evidence be the decisive condition for deployment.

Calibrated verification

A governance regime of formal checks, expert validation, institutional review, contestability, monitoring and revocation, scoped to one use.

Jagged capability

A model can help on one task and hurt on a seemingly similar task in the same workflow.

Deployer of record

The named actor accountable for one deployment context. A freely distributed model yields many such contexts.

Verification Coverage

A deployment level profile of six components, each present or absent, read with a minimum rule.

Minimum composition

The weakest required rail is binding. A zero on any one of them withholds authorization, whatever the others score.

Chapter 01

## Capability is jagged, so authority attaches to a use

A model's capability is not one property that carries smoothly from task to task. In a field experiment with consultants, AI raised productivity and quality on many tasks but lowered correctness on a complex managerial task beyond its demonstrated reach. On that task consultants with AI were 19 percentage points less likely to reach a correct solution than those without it. Model level studies tell the same story, for instance models that recognise letters but fail to count them reliably.

If AI were uniformly incompetent, the debate would be short. If it were uniformly reliable, it would be shorter still. Models are capable enough to be useful, opaque enough to be hard to inspect and uneven enough that blanket acceptance and blanket refusal both fail. So authorization should attach to a deployment context with a named deployer, and the same base model can then be acceptable in one context and prohibited in another.

*Figure.* **One base model, three deployment contexts.** The contexts are the paper's own examples. Each one carries its own deployer of record and its own verification duties, so a single model never receives one general authorization.

Chapter 02

## Seeing inside is one stream of evidence

Calibrated verification draws on four evidence streams. Mechanistic evidence reads internal structure. Behavioural evaluation tests outputs on held out data, red team probes and prospective trials. Independent review checks the process that produced the evidence. Domain experts and affected people find harms and contest paths that evaluators miss. Each stream has a scope limit, and the streams feed three verifier classes, called formal, empirical and social normative.

Mechanistic evidence is valuable and still bounded. In one clinical setting a model represented hazard information internally, yet a 53 point gap separated that representation from correction of its output. On steering benchmarks, prompting and finetuning beat sparse autoencoder methods. Behavioural evidence is bounded too. Frontier models often tell evaluation from deployment, and one reaches an AUC of 0.83 against a human baseline of 0.92.

*Figure.* **The four evidence streams of Section 3.1.** Choose a stream to read what it contributes and where its scope ends. The numbers are those the paper cites. The bars compare quantities within one study each and are not on a shared scale.

Chapter 03

## Six rails, each from a failure mode

The six properties of the regime are not a wish list. Each answers a deployment failure that the paper documents. Capability varies across nearby tasks, so authorization must be scoped to a domain. Self reported evidence may be incomplete, so it must be independently checkable. Performance can change after release, so it must be monitored. Harm needs a responsible actor, affected people catch errors evaluators miss, and new evidence should change a deployment's status. Those give accountability, contestability and revocation.

The properties do not trade against each other. Strong benchmark results do not stand in for a contest path in a domain that affects rights. Strong interpretability evidence does not stand in for a monitoring plan in a clinical setting that drifts.

*Figure.* **Table 1 of the paper.** Point at a failure mode to light the property it requires, and the reverse. The mapping is one to one.

Chapter 04

## The weakest rail decides

Verification Coverage records, for a deployment, whether each of the six components is present and sufficiently documented. It is reported first as that profile. The minimum rule makes the weakest required rail binding, and a zero on any rail withholds authorization. A weighted sum may be reported for convenience, with weights set by the authorizing institution, but it must never replace the profile, because the same sum can hide different gaps.

Passing does not compel deployment. It only permits consideration, and institutional judgment about residual risk remains. Failing on a required rail blocks authorization until the deployment is redesigned and evaluated again.

Switch rails on and off for a hypothetical deployment. Equal weights are used for the convenience sum.

*Figure.* **Profile, sum and minimum.** With five rails on, the equal weight sum reads 5/6 whichever rail is missing, while the minimum stays at zero and names the rail to repair. The hypothetical deployment and the equal weights are ours. The rule is the paper's.

Chapter 05

## Existing regimes are partly verified

High stakes regimes already separate model output from deployment authority. None of them is fully verified. Medicine has authorization and reviewability but weak surveillance. Credit has reasons and correction but weak lifecycle monitoring. Employment has audit and notice but weak revocation. Autonomous systems report incidents but give affected non operators little route to appeal. Criminal justice has a named institutional authority but weak verification and contestability.

The medical gap has a number. A 2024 scoping review found that only 62 of 692 FDA approved AI/ML devices contained a prospective study for post-market surveillance. Under the Monitoring Maturity floor, that deficiency would block authorization.

62 of 692 devices with a prospective post-market surveillance study (9.0%).

*Figure.* **One dot per device in the scoping review the paper cites.** The highlighted dots are the devices whose documents contained a prospective surveillance study.

Criminal justice is the limiting case. A state supreme court allowed consideration of a proprietary risk score with cautions, later work found that the score did not beat a simple two feature model or pooled lay judgments on the task studied, and the tool's secrecy has been criticised. Higher stakes call for stronger verifiability, not simply stronger demands for explanation. Select any row of the ledger above to read its rails.

## What the argument covers

### It shows

- Why mechanistic evidence is relevant to deployment yet insufficient as its sole gate.

- A regime in which authorization attaches to one use and one deployer of record.

- Six properties derived from documented failure modes, and a reportable profile with a minimum rule.

- A diagnostic coding of five existing regimes with this vocabulary.

### It does not show

- That interpretability is unimportant. It stays one evidence stream, and plausibly the most direct signal for deceptive internal objectives.

- A validated universal score. Verification Coverage is a structured report, and its domain table is not a measurement or a legal finding.

- That passing coverage compels deployment. Named institutions keep final authority.

- That AI should be treated as a human expert. The analogy is institutional.

We answer seven objections in the paper, among them that general purpose models cannot be gated by domain, that some domains have no verifier, and that the metric invites false precision. A domain with no plausible verifier scores low on Verifier Strength, and the minimum rule then withholds autonomous consequential use while decision support under a named human remains available.

## Cite this article

```bibtex
@article{konrad2026openbox,
  title   = {The Open-Box Fallacy: Why {AI} Deployment Needs a Calibrated Verification Regime},
  author  = {Konrad, Phongsakon Mark and Adam, Tim Lukas and Merrild, Ane Cathrine Holst and
             Terrenzi, Riccardo and De Rosa, Rebecca and Tanyel, Toygar and Ayvaz, Serkan},
  journal = {arXiv preprint arXiv:2605.10601},
  year    = {2026}
}
```

Every number and every ledger cell on this page comes from the paper. Widgets marked illustration explain a rule and show no results.

A project of the [Applied and Interpretable Machine Learning Research Group](https://aiml-sdu.github.io) at the University of Southern Denmark.
