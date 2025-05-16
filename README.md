# JabRef-GitHub-GFIs
This repository contains notes and code towards a first step to classify GitHub issues. We concentrated here on Good First Issues in the Jabref project. We explored their characteristics (surface metrics and qualitative characteristics) to be able to recognize them and help newcomers to open-source projects find them more easily.

The file "get chracteristics of human-validated GFIs.ipynb" contains the code used to get characteristics of 28 open Jabref GFIs. We first computed surface metrics (for lexical metrics we only concentrated on the title and the body of the issues) and then we asked ChatGPT-4o for qualitative metrics. We then computed metrics scores and eventually obtained a general GFI score, which we then used in the GPT prompt with few-shots.

To be able to run the code with the GPT client, you will need to get an API key at https://platform.openai.com/api-keys. 

We then injected 15 closed GFIs from Jabref into our scraped dataset of Jabref open issues to see if GPT was able to recognize them.

With the first try, GPT correctly recognized 10/15 planted GFIs. Recall on planted GFIs: 66.67%. These numbers are not very interesting because we did not have any counter examples (no NO-GFIs).

We reran with introducing 5 NO examples in the GPT prompt. How did we add NO GFI examples? We went to the Jabref issue page and logged issues labeled second good issue, third good issue, and fourth good issue. Since we only have the definition of a second good issue “Involves a tour across multiple intertwined components in the project”, we are treating all 2, 3, and 4 second issues as NO GFIs.
Planted GFIs recognized: 6/15 (40.00%)
Calculate the F1 score: 2 x (precision x recall) / precision + recall
F1 = 0.57

To try to get a better recall, we improved the prompt with chain of thought. Also added 7 YES examples (instead of 5).
Results: Planted GFIs recognized: 12/15 (80.00%)
F1-Score: 0.88

The file github_issues_with_readability_and_lexical2.json contains all the issues scraped from Jabref with their comments, lexical richness, and readabilty scores for further research.
