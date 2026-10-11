# VIGIL Incident Artefact Contract

This directory holds **curated, original-source evidence captures** for VIGIL Incident records. It accepts authentic visual media and **purposeful PDF captures of volatile informal sources**. It is not an evidence-processing workspace, scraping cache, or repository for exported source metadata.

## Storage boundary

Occurrence-specific screenshots, relevant original audiovisual media, and selected **PDF printouts preserving volatile original pages** must not be stored in the CAM-Initiative/Vigil repository. Formal reports, ordinary research PDFs, source metadata, scraping results and transcripts are normally referenced by their original URLs and structured analysis in Incident `source_records`, **not copied into Registry** merely because they exist.

They belong in:

```text
CAM-Initiative/Registry
└── VIGIL/
```

The Vigil repository remains the canonical home for structured Incident records, taxonomy adjudication, harm assessment and provenance metadata. Registry holds **selected original-context media and volatile-page PDF captures**, not arbitrary copies of documents. Do not commit scraped Reddit JSON submissions, browser API responses, temporary capture manifests, HTML-to-PNG reproductions, logs of capture attempts, or working research files under `Registry/VIGIL/`. Retaining a volatile source's authentic browser print-to-PDF is different from importing a publisher's normally durable assessment report.

Branding, taxonomy-publication artwork and other non-Incident build assets are outside this contract.

## File naming

Use the canonical Incident identifier as the filename stem:

```text
VIGIL/VIGIL-INC-000129.png
VIGIL/VIGIL-INC-000010.mp4
```

Where an Incident has more than one artefact of the same or similar type, use stable two-digit suffixes. A first screenshot may be unsuffixed or, for a pre-existing numbered sequence, `-01`; then continue `-02`, `-03` and so forth. A separate source PDF can use the same incident stem with `.pdf`:

```text
VIGIL/VIGIL-INC-000032.png
VIGIL/VIGIL-INC-000032-02.png
VIGIL/VIGIL-INC-000172.png
VIGIL/VIGIL-INC-000172-02.png
VIGIL/VIGIL-INC-000195-01.png
VIGIL/VIGIL-INC-000195-02.png
VIGIL/VIGIL-INC-000195.pdf
```

Do not encode transient labels such as `final`, `new`, `latest` or dates into the canonical filename unless the date is necessary to distinguish independently meaningful source artefacts.

## Artefact selection standard — source context, volatility and added value

**Default: cite a formal source, do not screenshot it.** Official reports, regulator findings, court decisions, academic studies, standards, published product assessments, and other ordinarily durable institutional publications are cited in canonical `source_records` with their exact source URLs and primary-document details. Do not photograph title pages or prose simply to populate the Case File's image slot. Preserve original published figures or irreplaceable visual evidence only when visual context itself is material and not reproducible in the narrative.

**Priority: preserve informal, volatile, first-person sources as authentic screenshots or PDF captures.** Public Reddit posts, X/Twitter posts, social-media threads, and informal user conversations are frequently editable or deleted. When they are material firsthand Incident evidence, seek a **literal capture of the actual displayed post/conversation, or the original page printed to PDF**, not just a model-written account. This lets an independent reader see:
- the original author's displayed identity/handle, platform, date or timestamp when available, and the post body;
- the original media or attached model interaction, if material, and enough surrounding thread/reply context to interpret it correctly;
- the visible distinction between what a user says, what the AI is shown saying, and reactions/reposts by others.

Preserve the source-native presentation **for legibility and context**, without reassembling or editing it in a way that changes attribution, removes significant qualifiers or makes multiple comments look like one exchange. For long posts, use numbered source-native screenshots and/or a browser print-to-PDF of relevant page sections. A printed PDF may show a collapsed `Read more` section; mark that limitation and do **not** imply the hidden words appear in the saved printout. Use a separate image for materially different attached media or continuation. If multiple users' posts form separate occurrences, never combine them into one artefact or Harm Impact assessment.

**Authenticity rule:** A screenshot or PDF must be a real capture/printout of the original social platform post, a genuine user-supplied capture, or an explicitly identified archived *visual rendition of the same source-native post*. A screenshot of an archive API JSON response, search snippet, scraped text, markdown, a model-generated quote card, a reconstructed page, or an error/block screen is **not** a screenshot of the user post. Never label such a representation `source-screenshot`.

If the original platform blocks browser access, record the blocked status in the **Vigil review/audit**, preserve the original post URL in `source_records`, and acquire a legitimate readable source-native screenshot before adding `incident_artefacts`. Do not substitute a prettified reconstruction merely to satisfy a screenshot request. Where an authentic source capture is unavailable, the Incident's evidence limitations must be explicit; image/PDF acquisition and Incident admission are distinct decisions.

**Selection question:** Would seeing the real original evidence materially help a reader verify authorship, occurrence context, wording, interaction sequence, visual state, or later deletion risk? If yes, include an authentic, appropriately bounded capture. If the screenshot would merely duplicate the summary of an institutional report, omit it.

## Capture and preservation workflow

1. Identify the original public or otherwise admissible source artefact.
2. For selected volatile-source context or primary evidence, preserve an authentic capture in this `VIGIL/` directory.
   - Literal browser screenshots or source-published images may be stored as PNG.
   - **Browser Print-to-PDF documents of volatile first-person posts, threads or interactions may be stored as PDF** if they preserve useful original authorship, post content and context. Do not upload arbitrary institutional reports simply as backups.
   - Original relevant video evidence may be stored in its source-appropriate format such as MP4.
   - Do **not** commit JSON, scraped/post archive exports, machine-readable capture manifests, synthetic rendering templates, or page-fetch/debug outputs. Keep audit logs under Vigil review/audit paths if genuinely necessary.
3. Inspect the saved image **or PDF** for recognisable original platform framing, the source author's visible identity/context, relevant material wording, and any attached user–AI interaction. Explicitly flag cropped or collapsed content and missing dialogue. Do not represent a generated reconstruction, archive JSON page, redrawn image, or synthetic recreation as a source screenshot.
4. Avoid substantive editing. Cropping for legibility is acceptable only where it does not remove material context. Any redaction, annotation, stitching or transformation that could affect interpretation must be disclosed in VIGIL provenance metadata. A Reddit archive's raw API JSON should never be photographed as if it were the original post.
5. Commit the Registry artefact first.
6. Use the resulting **Registry commit SHA** to construct immutable references in the VIGIL Incident record.
7. Only after the Registry artefact exists should the VIGIL Incident's `incident_artefacts[]` entry be added or updated. Use renderable PNGs for the website's inline evidence gallery; a source PDF should ordinarily be linked as a preserved document and **not disguised as an image**.

## Original-source citation, rights and preservation purpose

- **The original source is always primary.** Record its literal original public URL, author/publisher, title/description, original date where evidenced, date of capture, and any source-content limits in the canonical Incident `source_records[]`. Do **not** substitute a Registry image or PDF URL for that link.
- **The Registry copy is an archival reference.** Where relevant, also link the commit-pinned screenshot or PDF as a preserved copy that allows a reviewer to inspect what was visible when captured, even if the original is later edited, deleted, made private or changed.
- **Do not overclaim authenticity.** A browser print-to-PDF proves what the capturing session displayed, not the original AI model's hidden instructions or omitted messages. Distinguish source author's words from actual captured model output and replies by other users.
- **Copyright and privacy still apply.** Preservation for research, criticism, accountability or reproducibility is **not automatic copyright clearance or immunity**. Prefer the minimum necessary material with appropriate attribution, preserve links, assess licences/permission and applicable exceptions where relevant, and consider privacy, user safety and personal information before publicly embedding a capture. A publicly accessible source does not automatically permit unlimited republication.
- **Respond to rights concerns.** If a rights holder or affected individual raises a justified concern, review the source and copy, applicable permission or exception, redaction, restricted access or removal options, and retain an appropriately bounded provenance trail in VIGIL. An archived copy can persist in Git history even after removal from the current branch; do not promise complete erasure through an ordinary Git deletion.
- **Evidence retention is not an assertion of ownership.** CAM Initiative's preservation, display and attribution do not imply endorsement by, affiliation with, or copyright ownership of the original author or platform.

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
