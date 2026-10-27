The metadata profile was slightly modified and expanded to meet the project needs, mainly for archival purposes and basic domain-related searches.  
The JSON file is compiled through a combination of automatic pipeline processes and manual researcher input. It is divided into four sections reflecting the event-creation structure of the STORYTEL ontology:

```json
{
  "full_video": { … },
  "full_video_creation": { … },
  "story": { … },
  "story_creation": { … }
}
```

`full_video` and `full_video_creation` replace the previous single `video` section, distinguishing between the properties of the digital object itself and the properties of the recording event that produced it — consistent with the `Full_Video` and `Full_Video_Creation` classes in the ontology. Similarly, `story_creation` is kept separate from `story` to reflect that clipping is a distinct event carried out by a different actor (the linguistics researcher) at a different time from the original recording.

This metadata profile re-uses already existing standards, in particular [Dublin Core Terms](http://purl.org/dc/terms/), [Schema.org](http://schema.org/) and [DataCite](https://datacite-metadata-schema.readthedocs.io/en/4.7/).

The **Compilation** column indicates how each field is expected to be populated:
- `AUTO` — set automatically by the pipeline
- `MANUAL` — must be filled in by the researcher

---

## `full_video`

Properties intrinsic to the `Full_Video` digital object, including governance and access metadata.

| Field | Predicate (Property) | Value | Compilation |
| --- | --- | --- | --- |
| **Video Identifier** | [Dublin Core `dcterms:identifier`](http://purl.org/dc/terms/identifier) | e.g. `"UBO-001"` — generated following a defined naming convention | AUTO |
| **Video Duration** | [Schema.org `duration`](http://schema.org/duration) | e.g. `"1:32"` — extracted from file technical metadata | AUTO |
| **Language** | [Dublin Core `dcterms:language`](http://purl.org/dc/terms/language) | e.g. `"Italian"` | MANUAL |
| **Resource Type** | [Dublin Core `dcterms:type`](http://purl.org/dc/terms/type) | Fixed value: `"Dataset"` | AUTO |
| **File Format** | [DataCite `Format`](https://datacite-metadata-schema.readthedocs.io/en/4.7/properties/format/) | e.g. `"mp4"` — extracted from file extension or MIME type | AUTO |
| **Resource Type General** | [DataCite `resourceTypeGeneral`](https://datacite-metadata-schema.readthedocs.io/en/4.7/appendices/appendix-1/resourceTypeGeneral/#audiovisual) | Fixed value: `"Audiovisual"` | AUTO |
| **Funding Reference** | [DataCite `fundingReference`](https://datacite-metadata-schema.readthedocs.io/en/4.7/properties/fundingreference/) | Fixed value: `"KA220-HED - Cooperation partnerships in higher education"` | AUTO |
| **Keywords** | [Schema.org `keywords`](http://schema.org/keywords) | e.g. `"game, friends, compliment"` — comma-separated list | MANUAL - CRITERION TBD |
| **Permission Type** | [Schema.org `permissionType`](http://schema.org/permissionType) | Fixed value: `"Restricted"` | AUTO |
| **Ethics Policy / Protocol** | [Schema.org `ethicsPolicy`](http://schema.org/ethicsPolicy) | e.g. `"Prot. no. 0086617 del 12/05/2026"` — fixed per institution, set once at project level | AUTO |
| **Consent Form Type** | [Schema.org `AgreeAction`](http://schema.org/AgreeAction) | e.g. `"Written"` — fixed value | AUTO |

---

## `full_video_creation`

Properties of the recording event (`Full_Video_Creation` in the ontology): who recorded it, where, when, with what device, and who participated.

| Field | Predicate (Property) | Value | Compilation |
| --- | --- | --- | --- |
| **Start Date** | [Schema.org `startDate`](http://schema.org/startDate) | e.g. `"2026-06-17"` — extractable from file  metadata | AUTO |
| **Recording Venue** | [Schema.org `EventVenue`](http://schema.org/EventVenue) | e.g. `"Home"` — not inferable from the file | MANUAL |
| **Country** | [Schema.org `addressCountry`](http://schema.org/addressCountry) | e.g. `"Italy"` — not inferable from the file| MANUAL |
| **Region** | [Schema.org `addressRegion`](http://schema.org/addressRegion) | City or region of the recording — manual | MANUAL |
| **Recording Instrument** | [Schema.org `instrument`](http://schema.org/instrument) | e.g. `"Smartphone"` — fixed | AUTO |
| **Contributor** | [Dublin Core `dcterms:creator`](http://purl.org/dc/terms/creator) | ID or name of the student who uploaded the video | MANUAL |
| **Role Name** | [Schema.org `roleName`](http://schema.org/roleName) | Fixed value: `"Being recorded"` | AUTO |
| **Party Size** | [Schema.org `partySize`](http://schema.org/partySize) | Number of people present in the video  | MANUAL |
| **Recording Type** | [Schema.org `recordingOf`](http://schema.org/recordingOf) | Fixed value: `"VideoRecording"` | AUTO |
| **Participants** | [Schema.org `participant`](http://schema.org/participant) | Array of objects; each contains the participant's identifier | MANUAL |
| **Participant Identifier** | [Schema.org `identifier`](http://schema.org/identifier) | ID of each participant | MANUAL (?) |

---

## `story`

Properties of the `Story` object (the clip), including its temporal position within the parent video.

| Field | Predicate (Property) | Value | Compilation |
| --- | --- | --- | --- |
| **Story Identifier** | [Dublin Core `dcterms:identifier`](http://purl.org/dc/terms/identifier) | e.g. `"UBO-001_Story_1"` — derived from parent video identifier and clip number | AUTO |
| **Is Part Of** | [Dublin Core `dcterms:isPartOf`](http://purl.org/dc/terms/isPartOf) | Reference to the parent video identifier, e.g. `"UBO-001"` | AUTO |
| **Start Time** | [Schema.org `startTime`](http://schema.org/startTime) | Start time of the clip relative to the original video | AUTO |
| **End Time** | [Schema.org `endTime`](http://schema.org/endTime) | End time of the clip relative to the original video | AUTO |
| **Clip Number** | [Schema.org `clipNumber`](http://schema.org/clipNumber) |  | MANUAL (?)|

---

## `story_creation`

Properties of the clipping event (`Story_Creation` in the ontology): who cut the clip and when.

| Field | Predicate (Property) | Value | Compilation |
| --- | --- | --- | --- |
| **Date Created** | [Dublin Core `dcterms:created`](http://purl.org/dc/terms/created) | Timestamp generated automatically when the clipped file is saved (`YYYY-MM-DD` format) | AUTO |
| **Creator** | [Dublin Core `dcterms:creator`](http://purl.org/dc/terms/creator) | Name or ID of the linguistics researcher who extracted the clip — fixed | AUTO |
