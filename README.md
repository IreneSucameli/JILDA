# JILDA

JILDA (Job Interview Labelled Dialogues Assembly) is a novel collection of chat-based mixed-initiative, human-human dialogues
related to the job offer domain and for the Italian language.

JILDA dialogues were collected using a Map-Task approach which involved 50 Italian native speakers to simulate. These speakers simulated a chat-based
conversation between a ”navigator” and an applicant.
In this way we collected in this way 525 mixed-initatives dialogues, with 15-20 Navigator-User interaction.

This repository includes also the MTurk dataset, a collection we previously built for the same domain and language. 
The MTurk dataset includes 220 template-based dialogues collected via Amazon Mechianical Turk. 

The two datasets were annotated using the same annotation schema.
Below are defined the main dialogue acts and slot used to annotate the dialogues collected:

### Dialogue acts
All the DAs can be referred both to the applicant’s utterances (aka usr) and to the navigator’s utterances (sys):

 -  greet,
 -  inform_basic,
 -  inform_proactive,
 -  request,
 -  select,
 -  deny
 
 ### Slots 
 They represent the attributes of the entity job-offer: 
 
 - job_description,
 - contract,
 - duties,
 - skill,
 - past_experience,
 - degree,
 - age,
 - language,
 - area,
 - company_name,
 - company_size,
 - location,
 - contact,
 - other


## Cite

Irene   Sucameli,   Alessandro   Lenci,   Bernardo Magnini,  Maria  Simi,  and  Manuela  Speranza. 2020.   
Becoming JILDA. In Proceedings of the Seventh Italian Conference on Computational Linguistics CLIC-it 2020.


## People
- Maria Simi, professor - Dept. of Computer Science (Universtiy of Pisa)
- Irene Sucameli, PhD student - Dept. of Computer Science (University of Pisa)
- Davide Cucurnia, MA student - Dept. of Computer Science (Universtiy of Pisa)
