# AILuminate Naming and Versioning v1.0
AILuminate is not a single benchmark, but an expanding suite of benchmarks. This file describes how we name and version AILuminate benchmarks and major components to maintain clarity.

# Audiences and goals

Audiences have their own goals for why they’re looking at the name of a benchmark, and we have goals for what we want to accomplish with that name. Everybody wants clarity and simplicity, but what those mean varies based on the goals of each audience.

| **Audience** | **Naming and versioning goals** |
| :---- | :---- |
| MLC developers and researchers | Keep track of what version they’re currently working on Keep track of which product/project they’re working on Issue tracking: exactly *which* blob of overlapping/interacting software components does the issue refer to? Planning: a shared vocabulary for what is being worked on *now*, what is going to be worked on *next*, and roughly what is going to be done either in another development initiative or *later* |
| Product Managers | Distinguish between what efforts affect one specific development initiative and what affects multiple initiatives Communicate development plans to developers Communicate plans to other stakeholders, such as members, partners, or potential adopters |
| General public and non-technical users | Want to see progress Want to know what the options are Want to know which part of the product suite they need |
| Technical general public | Developers and data scientists tasked with implementation need to know what software to get Researchers want to test the appropriate model and reference the appropriate model in their papers Competitors\*/Product Managers want to know the range of capabilities |

# Naming

## Goals

* Clearly distinguish at a glance *this* benchmark from other AILuminate benchmarks so potential users can clearly distinguish between different families of the AILuminate benchmark.  
* Communicate the main focus of *this* benchmark in terms that are useful to readers.

## Basic name format:

* Use spaces or snake\_case. It’s 2025, we should be able to put spaces in filenames, but it’s still sometimes easier to use underscores.  
* Capitalize important name components. 

**\[AILuminate\] \+ \[SUT Type\] \+ \[Combination of name components\] \+ \[Language in [BCP 47](https://en.wikipedia.org/wiki/IETF_language_tag) abbreviation\] \+ \[[Semantic Version](https://semver.org/): x.y.z\] \+ \[Release type, optional\]**

## Name components

| **Component** | **Examples** |  |
| :---- | :---- | :---- |
| *Language* | French | Simplified Chinese |
| *Region* | \[Belgium \| Canada \|...\] | \[Shanghai \| Taiwan \| …\] |
| *SUT Type* | Language | Multimodal |
| *SUT Specialization* | \[Interactive Chat \| instruction generation \| …\] | \[Image-to-text \| Speech-to-text \| …\] |
| *Domain* | General Purpose | \[Financial \| Medical \| …\] |
| *Release type* | General Availability | \[Release Candidate \| Test \| …\] |

## Examples

| **Bad** | **Good, maybe** |
| :---- | :---- |
| AILuminate Multimodal Speech-to-text Medical French Cameroon Release Candidate 2.3.4 | AILuminate Multimodal Med FR 2.3.4 |
| AILuminate 2.3.4-MMFC1 AILuminate 2.3.4 | |
| AILuminate 2.3.4 | |

# Versioning

I cribbed from the [Semantic Versioning scheme](https://semver.org/) and modified their rules for when to version and what the version should be.

## Versioning rules

1. A normal version number MUST take the form X.Y.Z where X, Y, and Z are non-negative integers, and MUST NOT contain leading zeroes. X is the major version, Y is the minor version, and Z is the patch version. Each element MUST increase numerically. For instance: 1.9.0 \-\> 1.10.0 \-\> 1.11.0.  
2. Once a versioned package has been released, the contents of that version MUST NOT be modified. Any modifications MUST be released as a new version.  
3. Major version zero (0.y.z) is for initial development. Anything MAY change at any time. The release SHOULD NOT be considered stable.  
4. Version 1.0.0 defines the public release. The way in which the version number is incremented after this release is dependent on how the benchmark changes. The public release consists of:  
   1. A set of Official Prompts  
   2. A corresponding Evaluator Model  
   3. Practice prompts, Demo prompts, offline evaluators, etc. are not part of the full version, though they can synchronize with it and use the same naming conventions.  
5. Patch version Z (x.y.Z | x \> 0\) MUST be incremented if only backward compatible bug fixes are introduced. A bug fix is defined as an internal change that fixes incorrect behavior. *For example, a fix to the scoring function of the evaluator that will not affect most results is a patch.*  
6. Minor version Y (x.Y.z | x \> 0\) MUST be incremented if new, backward compatible functionality is introduced. It MUST be incremented if any public functionality is marked as deprecated. It MAY be incremented if substantial new functionality or improvements are introduced within the private code. It MAY include patch level changes. Patch version MUST be reset to 0 when minor version is incremented. *For example, adding a new language to an existing benchmark is a minor version update.*  
7. Major version X (X.y.z | X \> 0\) MUST be incremented if any backward incompatible changes are introduced to the benchmark. It MAY also include minor and patch level changes. Patch and minor versions MUST be reset to 0 when the major version is incremented. *For example, when a benchmark implements a fundamentally new approach to generating prompts and evaluating them, but the SUT type doesn’t change, the major version MUST be incremented.*   
8. The language version is associated with a specific model. *For example: AILuminate Multimodal Med FR 2.3.4 and AILuminate Multimodal Med ZH 2.3.1 can both coexist under AILuminate Multimodal Med 3.1 because each evaluator model is updated separately, but they both contribute to a single release.*

# Illustration
![AILuminate Versioning Illustration](AILuminate%20Versioning%20Illustration%20Feb-2025.svg)
