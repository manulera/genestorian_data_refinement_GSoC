# Genestorian: data refinement

## Who we are

* Manuel Lera Ramirez (Manu)

Manu is writing this! I did my PhD working with fission yeast (_S. pombe_). Mostly doing microscopy and simulations of filaments inside cells.

In the course of my PhD I experienced first-hand a lot of the limitations of using spreadsheets to store information about strains, and started Genestorian as a side project.

I am currently a biocurator in [Pombase](https://www.pombase.org/), the model organism database for _S. Pombe_ (fission yeast).

I am a self-taught developer, moving from software development applied to modelling simple physical systems and image analysis (that was most of the coding I did for my research) towards web development to master the tools necessary to develop Genestorian.

As you have seen from Yo's email, you will be mostly interacting with me, but you can come to them in case I am not responding to you, or you feel like you need to talk to someone else.

* Yo Yehudi (Yo)

You can have a look at [Yo's personal website](https://yo-yehudi.com/). I got to know Yo through [Open Life Science](https://openlifesci.org/). They are an organiser in this mentorship program for Open Science that I definitely encourage you to check out if you are interested in research.

## Code of conduct

To ensure that everyone feels welcome in this project, we adhere to the [OBF code of conduct](https://github.com/OBF/obf-docs/tree/master/code-of-conduct). You can have a look at the document, which provides guidelines for behaviour, but also what to do if you witness that the guidelines are not followed.

## What you will be doing if you join as a contributor

If you haven't, please read the [internship guidelines](https://www.genestorian.org/internship/) that were linked in the project description in the Open Bioinformatics Foundation website. This gives a brief introduction to the use-case of Genestorian.

The goal of the internship (from that same link) is to develop an application that:

* From a table where the genotypes of strains are represented as strings, identify the allele names.
* See if those alleles correspond to known alleles for that organism (from lists that are available online).
* Extract the information of in which strains a new allele was generated, and the relationships parent-child between strains. How this information is recorded in the spreadsheet (if it is recorded at all) will very likely vary.
* Score the predictions depending on certainty.
* Format those predictions os that they can be imported into the database.
* (Optional) develop a system for users to validate or change the predictions.
* (Optional) develop a web interface for users to input their data, browse through the predictions, and validate or change them there.

### What you will find when you arrive
> **_NOTE:_**
> If you don't understand some of the biological terms used here, don't worry, we will have the time to go through them.

* **Source data:** a series of spreadsheets from labs working on _S. pombe_ which inconsistently follow a nomenclature for alleles.
	* This data is private to labs, and we cannot make it public, but [this website](https://yeast.nig.ac.jp/yeast/fy/StrainAllItemsList.xhtml) hosts a huge dataset of published strains with their genotypes. You can have a look to see how the genotypes look like.
	* Note that __this is not sequencing data__, just genotypes. No sequence analysis will be performed in this project.
* **List of all known published alleles in _S. pombe_:** A list which contains all the known alleles of fission yeast, with their names and some extra information. For example, see [this example](https://www.pombase.org/genotype/cdc25-22-C532Y-amino_acid_mutation-expression-not_assayed):

<table _ngcontent-nsm-c62="" class="genotype-allele-summary">
  <thead _ngcontent-nsm-c62="">
    <th _ngcontent-nsm-c62="" class="ng-star-inserted">Gene</th><!---->
    <!---->
    <th _ngcontent-nsm-c62="" class="ng-star-inserted">Product</th><!---->
    <th _ngcontent-nsm-c62="">Allele name</th>
    <th _ngcontent-nsm-c62="" class="ng-star-inserted">
      Synonyms
    </th><!---->
    <th _ngcontent-nsm-c62="">Description</th>
    <th _ngcontent-nsm-c62="">Type</th>
    <th _ngcontent-nsm-c62="">Expression</th>
  </thead>
  <tbody _ngcontent-nsm-c62="" class="ng-star-inserted">
    <tr _ngcontent-nsm-c62="" class="ng-star-inserted">
      <td _ngcontent-nsm-c62="" rowspan="1" class="ng-star-inserted">
        <app-gene-link _ngcontent-nsm-c62="" class="app-link" _nghost-nsm-c48=""><!---->

<a _ngcontent-nsm-c48="" triggers="" placement="bottom" container="body" href="/gene/SPAC24H6.05" class="ng-star-inserted">
  <span _ngcontent-nsm-c48="" class="gene-link">cdc25</span>
</a><!----><!---->

<!---->
</app-gene-link>
      </td><!---->
      <td _ngcontent-nsm-c62="" rowspan="1" class="ng-star-inserted">
        protein tyrosine phosphatase (M phase inducer) Cdc25  
      </td><!---->
      <td _ngcontent-nsm-c62="">
        <span _ngcontent-nsm-c62="">cdc25-22</span>
      </td>
      <td _ngcontent-nsm-c62="" class="ng-star-inserted">
        <span _ngcontent-nsm-c62="">cdc25.22</span>
      </td><!---->
      <td _ngcontent-nsm-c62="">
        <span _ngcontent-nsm-c62="">C532Y aa</span>
      </td>
      <td _ngcontent-nsm-c62="">amino_acid_mutation</td>
      <td _ngcontent-nsm-c62="">Not assayed</td>
    </tr><!---->
  </tbody><!---->
</table>

In the table you see that the allele with name `cdc25-22` is a gene variant of a gene called `cdc25`, and it is sometimes referred to as `cdc25.22`.

* **Ground truth examples:** I will prepare examples that we anticipate, so that you can get started with some known inconsistencies.

* **A framework to develop the refinement pipeline:** I still have not looked into this, but the idea is to use a framework (or follow the practices of an existing project) for data refinement. The framework should include data models to describe:
	* Input data.
	* Each rule that is applied to the input data to get the output.
	* Output data.
	* Validation / edition of the prediction.
	
	If you have some ideas for such framework, you can include them in your application.
	
### A prospective timeline

Since you have to submit a work plan for your project, here are the minimal milestones of the project:

* After going through the data and understanding the biological concepts and data models that we will use, you prepare a short presentation with the next steps. You receive feedback, and update your presentation if necessary. This presentation is also a good moment to ask a lot of questions that may have emerged.
* You implement the set of rules that covers the cases provided as ground truth, and develop a way to visualise the refinement for each strain. Then, you give a short presentation covering this and remaining inconsistencies. We go through them to see if we can add additional rules that would solve them.
* You write tests for those new rules and implement them.
* You implement a system to link parent and child strains, which performs additional checks about the relationship between the alleles in the parents and children.
* You propose a score metric to measure certainty of the predictions based on previous validations / editions by users in a short presentation, and discuss its implementation. You implement that metric for existing data.
* You implement continuous integration using github actions.

These steps would produce an application that would be really useful for the project, and should be achievable within the project timeline. Then, we can think of further milestones depending on the remaining time and your interests:

* Repeat the same process for a different model organism.
* Develop a minimal web interface for users to input their data, run the analysis, browse through the predictions, validate or change them there, and export them.
* Containerise and host the application.
* Continuous deployment.
* Something else

### Further info for your application

* This is a good project to apply your development skills to a biological context, and learn about biology. I anticipate spending substantial time with you discussing the biology underlying the data.
* It is strongly advised that you have some previous experience working with text processing or that you can show that you can learn it independently. While I can help you with the web/containerisation/continuous integration/continuous deployment needs for this project, I am not an expert on text processing, and can only point you to learning resources or other projects that solve similar problems.
* We are very interested to know about previous projects you contributed to, languages/frameworks that you have used.
* We are also interested on your next career steps and how you think this internship may help you reach your career goals. This can be a very simple sentence: "I am considering doing research in the future, so I want to contribute to a project that is for researchers", or "I want to work as a software developer in a biotech company, so I am looking for bio projects".

### Questions from applicants:

Here we answer some of the questions raised by some applicants:

#### Are you still looking for contributors?

Yes, we are. Applications are open until the 19th of April.

#### Are contributors expected to do something before the starting date?

Not before the Community Bonding Period, which starts May 20th. At that point, we expect to have some interaction with you, and you starting setting up the environment to start to code after June 13th. If you can't start before June 13th, that is also OK. We understand it is a big commitment of your time already, and you may have other duties. Of course, we are happy if you want to start contributing earlier than that, but we will not take this into account when deciding among candidates. We want it to be fair for the people who can't contribute before the start of the program.

#### What do you mean by "measure certainty of the predictions based on previous validations / editions by users"?
A prediction is the guess that the application would make about a certain genotype. For example, let's imagine that a given *S. pombe* strain has a "true genotype" of `ase1Δ::NatMx6`. This means that the gene `ase1` has been [deleted](https://en.wikipedia.org/wiki/Deletion_(genetics)) and replaced with a [selectable marker](https://en.wikipedia.org/wiki/Selectable_marker) named `KanMx6`. There are many ways in which people would type this wrong. A typical one would be `ase1D::NatMx6` (using `D` instead of `Δ`). We can be pretty confident about this one, so we would give it a high score. They can also have written `ase1Δ::Nat`. Most `Nat` markers in *S. pombe* are `KanMx6`, so it is almost safe to assume that it will be `NatMx6` but we cannot be sure, so we would give it a lower score. However, if the allele comes from a parent strain in which the marker is labeled `NatMx6`, we can be more confident that it is indeed `NatMx6`.

#### How many parents can a strain have?
In general, in a collection we can find strains that:|
* Have no parents in the collection: They have been received from another lab, or they are the reference strain (the wild-type).
* Have one parent: Most likely the child strain has been generated by genetic modification of the parents.
* Have two parents: In general, the parents have been sexually crossed to generate the progeny.

#### What is the best way to reach out?
Just send an email to Manu's address, that you can find in the GSoC page.

#### What does the genotype of this strain mean?
Let's take the strain [FY6848](https://yeast.nig.ac.jp/yeast/fy/StrainDetail.jsf?id=6848). Its genotype is `h90 ura4-D18`.


h90 is the mating type of this strain. Mating is the same as sexually crossing. You can read more about it here: https://en.wikipedia.org/wiki/Mating_type
For S. pombe there are three mating types: h-, h+ and h90. h90 can mate with all mating types, h- with h+ and h90, and h+ with h- and h90.

ura4-D18 is the name of an allele in the ura4 locus (https://en.wikipedia.org/wiki/Locus_(genetics)).
* You can find the information about the allele in Pombase: https://www.pombase.org/genotype/ura4-D18-unknown-disruption
* You can see from the table in Pombase that the sequence of the allele is unknown. This means that the sequence of ura4 is messed up in some way that prevents the gene product (a protein) from performing its normal function.
* If you go to 'cell phenotype' you can see that strains that have this allele are auxotroph (https://en.wikipedia.org/wiki/Auxotrophy) for uracil. The reason for this is that ura4 is a gene that is involved in the production of uracil, and cells without ura4 cannot make uracil from other biological molecules. Therefore, they have to be grown in a medium that has uracil.
Many strains in collections have the ura4-D18 allele.
* This is convenient because we can then introduce the ura4 gene as a selection marker. For example, let's say we have a strain with genotype `ura4-D18`, and we want to delete the gene ase1 in this strain. We can replace the sequence of ase1 in the genome by the sequence of the gene ura4. The resulting strain would have the following genotype: `ura4-D18 ase1Δ::ura4`. This new strain has a "normal" copy of ura4, and therefore can grow in the absence of uracil in the medium, so we can select for cells that have this genotype by growing them in the absence of uracil: https://en.wikipedia.org/wiki/Selectable_marker

#### Is it safe to assume that other than the genes in the genotype description, the rest of the alleles are identical to those of the wild-type?

Yes.

#### Is the fission yeast catalogue from yeast.nig.ac.jp the dataset that we will use during the internship

The [example dataset](https://yeast.nig.ac.jp/yeast/fy/StrainAllItemsList.jsf) mentioned is just an example. The datasets that you will be working with will come from research labs and will have more information, such as parent strains, etc.

#### What will be the programming language used in the project?
Python. This is mostly because researchers that code often do so in python, so it's a way to make contributions from researchers more likely. If you have experience in other programming languages but not python, that's really no problem, I am sure if you've used java/php/C++/ruby or something similar it will be easy for you to pick up python.

#### What do you mean by "a framework to develop the refinement pipeline"?

This is something that I am still looking into (if you find examples you can include them in your application). The idea is to follow the practices of another open source project that deals with a similar task or finding a framework for this kind of task. I imagine there must be some existing [web ontology](https://en.wikipedia.org/wiki/Web_Ontology_Language) that is meant to deal with pipelines like this. For example let's imagine the "true phenotype" `h- ase1Δ::NatMx6` (see previous questions). It could be wrongly written as `h-ase1D:Nat`. The application should apply a set of rules to fix the errors/inconsistencies, kind of like a [code linter](https://en.wikipedia.org/wiki/Lint_(software)). There should be an output indicating which rules have lead to the transformations applied to the data and in which order, so that the same transformation can be reproduced without running the analysis again. You could imagine a set of rules + transformations like this:

1. **Rule #XYZ: add space between mating type**: uses an `addition` transformation that adds a space.

    `h-ase1D:Nat -> h- ase1D:Nat`
2. **Rule #XYZ: use Δ to indicate deletion**: uses a `substitution` transformation that changes `D` for `Δ`.
    
    `h-ase1D:Nat -> h- ase1Δ:Nat`

Etc.


#### How much should I know about text processing to join the project?

If you have previously taught yourself other development skills and applied them in a project, that should be ok. In your application, please comment on what skills you have applied to other projects and how you acquired them. We want to find someone that can learn this by themselves or with minimal input from my side, as I have not done something like this myself before. That's one of the reasons why we want to find a framework, so that you can follow the practices in there.

Regarding the actual text-processing algorithms, I think we won't be using things more complicated than regex and approximate string matching (https://en.wikipedia.org/wiki/Approximate_string_matching), so it should be manageable for someone with some developing experience, but for someone for which this is the first time they do something other than scripting, it might not be a good fit.