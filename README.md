# STORYTEL DATA MODEL 

The STORYTEL data model is an entity-relationship model that follows the best practice of reusing established ontologies and vocabularies rather than defining new properties whenever suitable existing semantic models are available. The main ontologies re-used are:
-	**LRMoo**, the object-oriented extension of the Library Reference Model (LRM), derived from FRBRoo and compatible with CIDOC-CRM. It provides the conceptual framework for representing intellectual and cultural resources through the distinction between Work, Expression, Manifestation and Item (WEMI), while also modelling the events through which these entities are realized and created. 
-	**CIDOC-CRM **, an event-based ontology originally developed for the cultural heritage domain. It provides the general framework for representing entities, events, actors, places and the relationships between them. 
-	**CRMDig**, an extension of CIDOC-CRM for representing the production, derivation and provenance of digital objects and digital representations. 
-	**Web Annotation Ontology**, a formal representation of Web Annotation Data Model of W3C which is used to represent annotations and the relationship between an annotation and the resource or specific segment to which it refers in a structured, shared and interoperable manner.

[A visual representation of Storytel Data Model](DATA-MODEL.svg)

The data model structure can be summarized at four interconnected levels:

1. **Conceptual level**: The central conceptual structure of the model is based on LRMoo and CIDOC-CRM. CIDOC-CRM was selected because of its event-oriented approach, which makes it suitable for representing the processes involved in the production and transformation of the audiovisual resources. LRMoo provides a model for distinguishing the intellectual or conceptual resource from its different expressions.
In this context, the different audiovisual resources are represented as LRMoo Expressions of a common Work. The Work represents the conceptual level of the conversational storytelling material, while the Expressions represent its different realizations in the workflow. In particular, the model distinguishes between:
- the _full raw video_, representing the original audiovisual recording; 
- the _story_, representing a selected segment of the full video corresponding to a storytelling episode; 
- the _anonymized story_, representing an anonymized version of the selected story segment. 
This distinction allows the model to represent the fact that these resources are interconnected objects: the story is derived from a segment of the full video, while the anonymized story is derived from the corresponding story. At the same time, the three resources can be understood as different expressions of the same underlying Work. 

2.	**Process level**: creation events represent the recording, selection and anonymization processes through which the Expressions are produced and connect them to the actors, devices and other contextual entities involved. 
The creation of each Expression is represented through a dedicated creation event. 
This event-based representation is particularly useful for STORYTEL because the resources are the results of a sequence of recording, selection, transformation and anonymization processes. 

3.	**Contextual level**: relationships that describe the contextual information associated to the Expressions. For example, participants, place of recording, language, recording device and temporal characteristics of the recording. The model also represents the duration and temporal boundaries of the audiovisual resources. This makes it possible to distinguish the temporal extent of the full recording from that of the selected story segment. In the case of the anonymized story, the anonymization process does not create a new temporal segment: the anonymized resource corresponds to the same storytelling interval as the original story, while its audiovisual content has been modified to manipulate identifying information.

4.	**Annotation level**: annotations provide semantic or computational information about specific audiovisual resources or segments, while the Web Annotation model allows the target, content and generation process to be represented separately. This makes it possible to distinguish between the resource being annotated and the information produced as an annotation about that resource. For example, an annotation may refer to a specific segment of an anonymized story and contain a textual or computational result, such as a transcription. The model can therefore represent both the target of an annotation and its body, while also recording the software or procedure used to generate the annotation when applicable. In the current model, this structure is particularly relevant for representing automatically generated material coming from the STORYTEL pipeline. The software used to produce the transcription is represented separately from the annotation itself, making it possible to preserve information about how the annotation was generated without confusing the computational process with the resulting content.
