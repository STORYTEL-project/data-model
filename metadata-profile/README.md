The metadata profile was slightly modified and expanded to meet the project needs, mainly for archival purposes and basic domain-related searches.  
The JSON file, manually compiled by a researcher, is mainly divided into two sections which group the video metadata and the story metadata: 
```json
{
  "video": {
    …
  },
  "story": {
    …
  }
}

This new metadata profile re-uses already existing standards, in particular [Dublin Core Terms](http://purl.org/dc/terms/), [Schema.org](http://schema.org/) and [DataCite](https://datacite-metadata-schema.readthedocs.io/en/4.7/).  

The new metadata structure is the following:


| Field                | Predicate (Property)                                                    | Value                           |
| -------------------- | ----------------------------------------------------------------------- | ------------------------------- |
| **Video Identifier** | [Dublin Core `dcterms:identifier`](http://purl.org/dc/terms/identifier) | e.g. `"UBO-001"`                |
| **Video Duration**   | [Schema.org `duration`](http://schema.org/duration)                     | e.g. `"1:32"` — duration format |


| Field                        | Predicate (Property)                                                                                                                            | Value                                                                                 |
| ---------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| **Story Identifier**         | [Dublin Core `dcterms:identifier`](http://purl.org/dc/terms/identifier)                                                                         | e.g. `"UBO-001_Story1"`                                                               |
| **Is Part Of**               | [Dublin Core `dcterms:isPartOf`](http://purl.org/dc/terms/isPartOf)                                                                             | Reference to the parent video, e.g. `"UBO-001"`                                       |
| **Date Created**             | [Dublin Core `dcterms:created`](http://purl.org/dc/terms/created)                                                                               | Creation date (`YYYY-MM-DD` format)                                                   |
| **Creator**                  | [Dublin Core `dcterms:creator`](http://purl.org/dc/terms/creator)                                                                               | Name of the researcher who extracted the clip                                         |
| **Resource Type**            | [Dublin Core `dcterms:type`](http://purl.org/dc/terms/type)                                                                                     | e.g. `"Dataset"`                                                                      |
| **File Format**              | [DataCite `Format`](https://datacite-metadata-schema.readthedocs.io/en/4.7/properties/format/)                                                  | e.g. `"mp4"`                                                                          |
| **Resource Type General**    | [DataCite `resourceTypeGeneral`](https://datacite-metadata-schema.readthedocs.io/en/4.7/appendices/appendix-1/resourceTypeGeneral/#audiovisual) | e.g. `"Audiovisual"`                                                                  |
| **Funding Reference**        | [DataCite `fundingReference`](https://datacite-metadata-schema.readthedocs.io/en/4.7/properties/fundingreference/)                              | Name of the project, e.g. `"STORYTEL"`                                                |
| **Language**                 | [Dublin Core `dcterms:language`](http://purl.org/dc/terms/language)                                                                             | e.g. `"Italian"`                                                                      |
| **Keywords**                 | [Schema.org `keywords`](http://schema.org/keywords)                                                                                             | e.g. `"game, friends, compliment"` — comma-separated list                             |
| **Consent Form Type**        | [Schema.org `AgreeAction`](http://schema.org/AgreeAction)                                                                                       | e.g. `"Written"`                                                                      |
| **Recording Venue**          | [Schema.org `EventVenue`](http://schema.org/EventVenue)                                                                                         | Location of the recording, e.g. `"Home"`                                              |
| **Country**                  | [Schema.org `addressCountry`](http://schema.org/addressCountry)                                                                                 | e.g. `"Italy"`                                                                        |
| **Region**                   | [Schema.org `addressRegion`](http://schema.org/addressRegion)                                                                                   | City or region of the recording                                                       |
| **Contributor**              | [Schema.org `contributor`](http://schema.org/contributor)                                                                                       | ID or name of the student who uploaded the video                                      |
| **Ethics Policy / Protocol** | [Schema.org `ethicsPolicy`](http://schema.org/ethicsPolicy)                                                                                     | e.g. `"Prot. no. 0086617 del 12/05/2026"` — reference to the ethics approval protocol |
| **Recording Instrument**     | [Schema.org `instrument`](http://schema.org/instrument)                                                                                         | e.g. `"Smartphone"` — device used for recording                                       |
| **Party Size**               | [Schema.org `partySize`](http://schema.org/partySize)                                                                                           | Number of people present in the video                                                 |
| **Permission Type**          | [Schema.org `permissionType`](http://schema.org/permissionType)                                                                                 | e.g. `"Restricted"`                                                                   |
| **Recording Type**           | [Schema.org `recordingOf`](http://schema.org/recordingOf)                                                                                       | e.g. `"VideoRecording"`                                                               |
| **Required Max Age**         | [Schema.org `requiredMaxAge`](http://schema.org/requiredMaxAge)                                                                                 | e.g. `22` — maximum age of the participants                                           |
| **Required Min Age**         | [Schema.org `requiredMinAge`](http://schema.org/requiredMinAge)                                                                                 | e.g. `21` — minimum age of the participants                                           |
| **Role Name**                | [Schema.org `roleName`](http://schema.org/roleName)                                                                                             | e.g. `"Being recorded"`                                                               |
| **Start Date**               | [Schema.org `startDate`](http://schema.org/startDate)                                                                                           | e.g. `"2026-06-17"`                                                                   |
| **Start Time**               | [Schema.org `startTime`](http://schema.org/startTime)                                                                                           | Start time of the clip relative to the original video                                 |
| **End Time**                 | [Schema.org `endTime`](http://schema.org/endTime)                                                                                               | End time of the story relative to the original video                                  |
| **Clip Number**              | [Schema.org `clipNumber`](http://schema.org/clipNumber)                                                                                         | Ordering number of the story based on the extraction process                          |
| **Participants**             | [Schema.org `participant`](http://schema.org/participant)                                                                                       | Array of objects; each object contains the participant's identifier (see below)       |
| **Participant Identifier**   | [Schema.org `identifier`](http://schema.org/identifier)                                                                                         | ID of the participant present in the video                                            |
