<div style="text-align: center;">
  <img src="./assets/logos-off-gsoc.webp" alt="Logos OFF & GSoC" width="540">
</div>

# GSoC 2025 OpenFoodFacts

## Project description

| Contributor  | Estrella Paoli                                                                                                                                                       |
|--------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Project      | [Implementation of a new structured nutrition schema](https://summerofcode.withgoogle.com/programs/2025/projects/mzpDaWXd)                                           |
| Organisation | [Open Food Facts](https://world.openfoodfacts.org/)                                                                                                                  |
| Repository   | [Open Food Facts server](https://github.com/openfoodfacts/openfoodfacts-server)                                                                                      |
| Mentors      | [Louis Bastarache](https://github.com/LouisBastarache), [Stéphane Gigandet](https://github.com/stephanegigandet), [Charles Nepote](https://github.com/CharlesNepote) |
| Github       | [@Vic142](https://github.com/Vic142)                                                                                                                                 |
| LinkedIn     | [Estrella Paoli](https://www.linkedin.com/in/estrella-paoli)                                                                                                         |

The Open Food Facts database stores data on products all around the world. 
Even though the database has a lot of data in Europe, it could be completed in North America 
and more particularly in Canada. The original main goal of this project was to complete the import 
of products data from the USDA'S Food Data Central database that was initiated since January 2025. 
At the beginning of the GSoC, it was then determined that it would be better to wait 
until the new nutrition schema was integrated in the Open Food Facts database.

A new nutrition schema was designed to solve current problems and difficulties it caused. 
The schema was designed by consulting the Open Food Facts community 
and the discussions and the selected schema can be found in the 
[2025 - API - Nutrition Facts Schema and API](https://docs.google.com/document/d/19ZRrlWJraJm61E6U7AwxQ1uubPDvmSuNfl9F1oLC0Tg/) document. 
The designed schema was revised and evolved throughout this project.
The main problem with the old nutrition schema was that it lacked structure, which could lead to confusion for users 
and creates unnecessary challenges during the development of some new features or when integrating external data sources. 
Moreover, it could not allow the storage of data from several sources which would be very useful to use data 
from a particular source for example.

This project then changed to implement the new products nutrition schema in the Open Food Facts code. 
It provides a new nutrition schema, which has a lot of benefits to the Open Food Facts database 
such as more clarity, an easier development of new features, better support for importing data from other databases 
and the ability to store nutrition data from multiple sources.


## Goals of the project

- Document the new nutrition schema structure
- Implement the new schema features
- Implement the migration functions (upgrade and downgrade of products versions)
- Refactor the existing code with the new nutrition schema


## Contributions

### Presentation

The goals of the project changed at the beginning of the GSoC program, 
so I almost immediately started to work on the new schema.

Since the Open Food Facts code is in Perl and I wasn't familiar with the Perl language, 
I first had to learn this language and how the Open Food Facts code uses it. 
Because of that my first contribution was a small PR to import one more claim
from the files provided to Open Food Facts by the GS1.
- [feat:add no added sugars label from gs1](https://github.com/openfoodfacts/openfoodfacts-server/pull/12084)

<br>After this, the documentation of the new nutrition schema on OpenAPI and on other documentation files was the first actual step of this project.
- [docs: OpenAPI documentation for new product nutrition data schema](https://github.com/openfoodfacts/openfoodfacts-server/pull/12132)
- [docs: New schema version number for the nutrition facts schema change](https://github.com/openfoodfacts/openfoodfacts-server/pull/12143)

<br>When the documentation was done, the implementation of the new schema and of the new features, including testing, was the most important step.
During this part of the project some questions and discussions lead to changes to the new nutrition schema.
- [feat: preferred set generation](https://github.com/openfoodfacts/openfoodfacts-server/pull/12170)
- [feat: upgrade product version nutrition](https://github.com/openfoodfacts/openfoodfacts-server/pull/12231)
- [feat: update new nutrition schema](https://github.com/openfoodfacts/openfoodfacts-server/pull/12239)

<br>Finally, after the new nutrition schema features and migration functions were done, the last step consisted of 
updating the existing code with the new nutrition schema to prevent the existing features from breaking. 
The strategy for this step consisted of creating a branch used a base branch for the update of existing features 
considering the amount of work needed and the fact that it should all be merged at once in order no to break the deployed code. 
Then each update of features would be done in a branch created from this base branch, which allowed to maintain small PRs.
- [refactor: Nutrition data panel](https://github.com/openfoodfacts/openfoodfacts-server/pull/12310)

<br>Considering the volume of this project, the last step couldn't be completed before the end of the program.

### All pull requests

- [Merged pull requests](https://github.com/openfoodfacts/openfoodfacts-server/pulls?q=+is%3Apr+author%3AVic142+is%3Amerged+created%3A%3C%3D2025-09-01+)
- [Open pull requests](https://github.com/openfoodfacts/openfoodfacts-server/pulls?q=is%3Aopen+is%3Apr+author%3AVic142+created%3A%3C%3D2025-09-01)
- [All pull requests](https://github.com/openfoodfacts/openfoodfacts-server/pulls?q=is%3Apr+author%3AVic142+created%3A%3C%3D2025-09-01+)


## Next steps for future work

The next steps will consist of completing the migration of the products to their new version. 
For this, the following tasks should be done:
- Refactor all the existing code that use the nutrition data of the products
  - Create a branch from the refactor base branch *new-nutrition*
  - Merge each refactor into this base branch individually
  - The features that have to be refactored are features that break when the product version number is set to 1003 and/or that use the now deleted *nutriments* field of the products.
- When all features are updated, merge the base branch of the last step


## Main challenges and takeaways
- One of the main challenges was understanding and familiarizing myself with the code of the [Open Food Facts server repository](https://github.com/openfoodfacts/openfoodfacts-server),
which is written in a language that was completely new to me. Since Perl was new to me, it was very hard for me to understand such a complex project at first.
This GSoC project was a really great opportunity for me to master a new programming language.
- I have also invested a good amount of time during the project start for developing understanding on the architecture 
of the Open Food Facts database and code of the repository. Thanks to the guidance of my mentors I was able to familiarize myself faster 
and more easily before starting actively working on the project.
- The fact that the new nutrition schema still had unknown parameters and evolved during and after its implementation was another challenge, 
which taught me to learn how to manage evolving goals.
- Since the heart of this project consists of changing the whole nutrition schema, I learned a lot about databases structures, 
needs, and about the nuances of each solution, which was very interesting.
- Before this project, I had never used OpenAPI for documentation. This was a great chance for me to learn to use it.
- Finally, I also really enjoyed developing my communication skills by engaging with the community on Slack.

## Acknowledgements
I would like to thank my mentors [Louis Bastarache](https://github.com/LouisBastarache), [Stéphane Gigandet](https://github.com/stephanegigandet) and [Charles Nepote](https://github.com/CharlesNepote) for their invaluable guidance and support throughout the summer.
I would also like to thank [Alex Garel](https://github.com/alexgarel) for his help and support throughout the project.
I would like to thank Open Food Facts and the Google Summer of Code program for the opportunity of doing this project.

Contributing to Open Food Facts has been an amazing experience. 
I truly enjoyed contributing to Open Food Facts for this project, and I plan to keep on contributing in the future! 
I am glad to have collaborated with such an amazing set of people at Open Food Facts.
