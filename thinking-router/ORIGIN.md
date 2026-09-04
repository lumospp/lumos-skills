# Origin and adaptation notes

`thinking-router` is an original Lumos implementation inspired by a user-provided Skill based on 万维钢《现代思维工具100讲》 and by repeated real-case use inside the Lumos Creator System.

The upstream material is treated as an important conceptual source, but this repository version does **not** reproduce the original Skill text verbatim. The behavior here was re-designed around the recurring needs observed in Lumos workflows:

- model the problem before choosing a tool;
- route automatically so the user does not need to name frameworks;
- use one main tool plus only a few complementary / adversarial tools;
- separate models from evidence;
- require models to change judgment or action rather than decorate prose;
- preserve update conditions and reality feedback;
- support long-term internalization through real cases.

## Source information

- Conceptual source: 万维钢《现代思维工具100讲》 and a corresponding user-provided Skill.
- Upstream URL: not recorded in this repository at the time of adaptation.
- Upstream license: not verified.

Because the upstream license has not been verified, this repository intentionally avoids redistributing the upstream Skill text. The current files are a fresh implementation and concise index built from the methods that were actually useful in Lumos testing.

If a canonical public upstream repository and license are identified later, update this file with the exact URL, version/commit, license, and a clearer diff of what Lumos changed.