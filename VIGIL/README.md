# VIGIL Incident Artefact Contract

This directory is the canonical storage location for binary and file-based source artefacts used by VIGIL Incident records.

## Storage boundary

Occurrence-specific screenshots, source images, videos, preserved prompts, model outputs, documents and logs **must not be stored in the CAM-Initiative/Vigil repository**.

They belong in:

```text
CAM-Initiative/Registry
└── VIGIL/
```

The Vigil repository remains the canonical home for structured Incident records, taxonomy adjudication, harm assessment and provenance metadata. Registry holds the referenced media/file artefact itself.

Branding, taxonomy-publication artwork and other non-Incident build assets are outside this contract.

## File naming

Use the canonical Incident identifier as the filename stem:

```text
VIGIL/VIGIL-INC-000129.png
VIGIL/VIGIL-INC-000010.mp4
```

Where an Incident has more than one artefact of the same or similar type, use a stable two-digit suffix beginning at `-02`:

```text
VIGIL/VIGIL-INC-000032.png
VIGIL/VIGIL-INC-000032-02.png
VIGIL/VIGIL-INC-000172.png
VIGIL/VIGIL-INC-000172-02.png
```

Do not encode transient labels such as `final`, `new`, `latest` or dates into the canonical filename unless the date is necessary to distinguish independently meaningful source artefacts.

## Artefact selection standard

An Incident artefact should earn its place by adding evidentiary or explanatory value beyond the ordinary Case File prose.

The Incident record's prose remains responsible for the complete bounded factual account. A reader must not need to inspect an image to learn a material occurrence fact that should have been stated in the Incident summary, factual basis or supporting evidence.

Prefer artefacts that make information materially easier to understand than prose alone, for example:

- graphs, timelines and charts showing scale, chronology, clustering or change over time;
- diagrams, maps, interface states or system views showing relationships, topology or workflow;
- source images, screenshots or outputs that demonstrate the observed state directly;
- compact contextual source passages where the source's framing, qualification, comparison or surrounding context is itself evidentially useful and would be awkward or misleading to flatten into the general Incident narrative.

A screenshot of prose is therefore not automatically inappropriate. It is appropriate when the preserved passage adds source-specific context that the Incident narrative should not merely duplicate or absorb. It is inappropriate when it simply photographs facts already adequately stated in the Case File.

Do not select an artefact merely because it is visually striking, because a graph is available, or because an Incident already has an image slot. Before preserving or rendering an artefact, ask:

> What does this artefact let the reader see or understand that the structured Incident record does not convey as effectively on its own?

If the answer is only "the same information again", do not use it as a public-facing Incident artefact.

## Capture and preservation workflow

1. Identify the original public or otherwise admissible source artefact.
2. Preserve the artefact in this `VIGIL/` directory.
   - Literal browser/source captures may be stored as PNG.
   - Original audiovisual evidence may be stored in its source-appropriate format such as MP4.
   - A raw log or document may be stored directly where that is the evidence being preserved.
3. Do not represent a generated reconstruction, redrawn image or synthetic recreation as a source screenshot.
4. Avoid substantive editing. Cropping for legibility is acceptable only where it does not remove material context. Any redaction, annotation, stitching or transformation that could affect interpretation must be disclosed in VIGIL provenance metadata.
5. Commit the Registry artefact first.
6. Use the resulting **Registry commit SHA** to construct immutable references in the VIGIL Incident record.
7. Only after the Registry artefact exists should the VIGIL Incident's `incident_artefacts[]` entry be added or updated.

## VIGIL Incident reference contract

The Incident record stores metadata and references; it does not duplicate the media bytes.

For a Registry artefact at:

```text
VIGIL/VIGIL-INC-000129.png
```

committed at Registry SHA:

```text
ec6d88572cb2cca00b7bac5fbe8da68d1533631d
```

the VIGIL record uses:

```json
{
  "artefact_id": "VIGIL-INC-000129-A01",
  "artefact_type": "source-screenshot",
  "title": "OpenAI-published Astra-family persona compaction example",
  "media_type": "image/png",
  "permalink": "https://github.com/CAM-Initiative/Registry/blob/ec6d88572cb2cca00b7bac5fbe8da68d1533631d/VIGIL/VIGIL-INC-000129.png",
  "render_url": "https://raw.githubusercontent.com/CAM-Initiative/Registry/ec6d88572cb2cca00b7bac5fbe8da68d1533631d/VIGIL/VIGIL-INC-000129.png",
  "source_url": "https://original-source.example/item",
  "capture_role": "visual cross-reference",
  "capture_status": "maintainer-captured",
  "alt_text": "Accessible description of the preserved source artefact.",
  "caption": "Plain-language description of what the artefact shows and why it is relevant.",
  "provenance_note": "Commit-pinned Registry capture preserving the source artefact. The Registry copy is a VIGIL-maintained evidentiary cross-reference, not an asset hosted by the original publisher."
}
```

### Reference rules

- `permalink` must be the human-facing GitHub URL for the Registry file and must be **commit-pinned**.
- `render_url` must be the corresponding raw Registry URL and must be **commit-pinned**.
- Do not use `main`, another moving branch name or an unpinned raw URL in canonical Incident records.
- `source_url` identifies the originating external source. It must not be replaced by the Registry permalink.
- `capture_status` records how the Registry artefact was preserved; it does not upgrade the source's evidentiary status.
- `incident_artefacts[]` remains an evidentiary cross-reference layer. Source propositions relied upon for the Incident still belong in `source_records[]`.

## Screenshots of logs and telemetry

A literal screenshot of a public log/report view may use:

```text
artefact_type: source-screenshot
capture_status: maintainer-captured
```

A raw exported log preserved directly should use:

```text
artefact_type: log
```

A screenshot is not a substitute for the underlying source citation. The VIGIL record should retain the original report/log URL in `source_url` and the corresponding evidence source in `source_records[]` when the log supports substantive Incident facts.

For multiple log captures from one Incident, preserve only the minimum set needed to make materially distinct propositions visible. Do not create galleries of repetitive telemetry.

## Migration rule

If an occurrence-specific screenshot, video, log or document is found inside the Vigil repository:

1. copy the original bytes into `CAM-Initiative/Registry/VIGIL/` using the naming convention above;
2. commit the Registry file;
3. update every VIGIL `incident_artefacts[]` reference to the new commit-pinned Registry URLs;
4. verify the public renderer can resolve the Registry artefact;
5. remove the duplicate binary from the Vigil repository.

Do not delete the Vigil copy before the Registry copy is committed and its immutable references are recorded.

## Ownership boundary

**Registry owns the artefact bytes. VIGIL owns the Incident interpretation and the reference metadata.**

This separation is intentional: evidence media remains durably preserved without turning the structured VIGIL corpus into a binary asset repository.
