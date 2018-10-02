# **Course Title**<br/>by **Course Author**

README and sample lesson deadline: YYYY-MM-DD 

As part of the 'Course Spec' process, you will need to complete the following tasks:

- [ ] Edit this README by filling in the information for steps 1 - 7 according to our README rubric.
- [ ] Update the requirements.R file in your course repository on GitHub. If you need to install any additional libraries, you may need to update the requirements.sh file as well. Check with your CL as needed.
- [ ] Add the datasets for your course in the Teach Editor.
- [ ] Complete one sample lesson according to the sample lesson rubric.

## Course development resources

* Course admin page: https://www.datacamp.com/teach/

## Step 1: Brainstorming 

This part of the 'Course Spec' process is designed to help guide you through course design by having you think through several key questions. Please make sure to delete the examples provided here for you.

### 1. What problem(s) will students learn how to solve? (minimum of 5 problems)

- [ ] Write a list of ideas for problems that the students will encounter in the course.
> From a course on fraud detection:
>
>- How to identify and predict fraudulent transactions
>- How to effectively work with highly imbalanced data


### 2. What are the learning objectives of the course?

- [ ] Write a list of learning objectives for the course. These are not shown to the students, but they will be used to ensure your vision for the course aligns with the vision of your Curriculum Lead.

>Example from our scikit-learn course:
>
>- Learn the key concepts of supervised learning and how to implement them on real-world datasets;
>- Learn to distinguish regression from classification problems;
>- Learn to evaluate how well your classification and regression modes perform;
>- Learn best practices in supervised learning, such as splitting into test/train sets and k-fold cross validation;
>- Learn how to improve model performance by both preprocessing your data and regularizing your models.


### 3. What technologies, packages, or functions will students use? Please be exhaustive.

- [ ] Write a list of ideas for technologies that you want to use in the course. Include things like R/Python packages, SQL modules, or Google Sheets add-ons. If there are any important functions, methods, or commands that you want to teach, you can mention them here.

- [ ] Add the packages students will use to the requirements.r file of this repository.

>Example from a course on keras. This example has only a few Python packages and goes into depth on the functions that will be used.
>
>- keras, pandas, sklearn
>- Keras functions:
>- Dense
>- Concatenate, Subtract, Multiply (operate on two layers)
>- l2
>- Embedding
>- Flatten
>- keras.preprocessing.text.text_to_word_sequence
>- keras.preprocessing.sequence.pad_sequences
>- GRU
>- Bidirectional


### 4. What terms or jargon will you define?

- [ ] Write a list of technical terms, jargon, and acronyms that will be used in the course.

> Example from a course on experimental design. This has an extensive list of statistical terms.
>
>Randomization, replication, blocking, Latin Square, Greco-Latin Squares, factorial, ANOVA, T-test, F-test, normality, >qqplot, variance, type I/II error, null/alternative hypothesis, effect size, factor/categorical variable


### 5. What analogies or heuristics will you use?

- [ ] Write a list of analogies for concepts, heuristics for best practices, and any other non-technical explanations of things that may be helpful to students _(minimum of two)_.

>Example from a course on forecasting product demand. This analogy is likely intuitive to most people.
>
>Signal and noise - It's like trying to hear someone across a crowded room. Remove the noise, and you can easily understand what they are telling you.


### 6. What mistakes or misconceptions do you expect? 

- [ ] Write a list of common mistakes _(minimum of two)_ that you think students will make. These can be programming mistakes, conceptual misunderstandings, or simply examples of things that are unintuitive. 

>Example from a course on generalized additive models:
>
>The difference between prediction intervals and confidence intervals.


### 7. What datasets will you use? 

- [ ] Write a list of datasets that you will use in the course, a short description of each dataset (if it's not clear from the title), how you intend to use it and include a link to its source(s).

- [ ] Upload these datasets to your course on the Teach Editor. 

![teach_editor_datasets_upload](https://user-images.githubusercontent.com/20912644/44154482-d2e04b3a-a078-11e8-8ff9-2944fdcabeae.png)

Please avoid [overused datasets](https://authoring.datacamp.com/courses/design/brainstorming-datasets.html).

## Step 2: Who is this course for?

Terms like "beginner" and "expert" mean different things to different people, so we use personas to help instructors clarify a course's audience. When designing a specific course, instructors should explain how it will or won't help these people, and what extra skills or prerequisite knowledge they are assuming their students have above and beyond what's included in the persona.

- [ ] Please select the learner personas that align with your course. 
- [ ] Include an explanation describing your reasoning behind choosing the corresponding learner persona and any other relevant information.

Choose the appropriate learners for your course by following this link to [learner personas](https://authoring.datacamp.com/courses/design/personas.html)

* Learner persona 1: explanation
* Learner persona 2: explanation
* Learner persona 3: explanation

## Step 3: Course outline

A typical course is structured as follows:

- Chapter 1 has three lessons. This chapter is shorter than the rest since it serves as an introduction to the topic.
- Chapter 2 has 3-4 lessons.
- Chapter 3 has 3-4 lessons.
- Chapter 4 has 3-4 lessons.

A typical lesson is comprised of:

- A video exercise with slides and script, e.g. [sample video exercise](https://campus.datacamp.com/courses/introduction-to-the-tidyverse/data-wrangling-1?ex=4).
- 2-4 exercises that review what is covered in the video exercise.

*Remind yourself about [course terminology](https://authoring.datacamp.com/courses/design#terminology-and-structure), then describe the flow of the course.*

> Example from a course on interactive data visualization using leaflet

> Chapter 1 - Setting Up Interactive Web Maps
>   * Lesson 1.1 - Introduction to leaflet
>     * A learning objective: Create a basic interactive web map in R using the `leaflet` and `htmlwidgets` packages.
>     * Some functions introduced/used: `leaflet()`, `addTiles()`, `%>%`
>   * Lesson 1.2 - Working with Map tiles
>     * A learning objective: Tweak the base map in `leaflet` using provider tiles, such as those on [OpenStreetMap](https://www.openstreetmap.org/)
>     * Some functions introduced/used: `stringr::str_detect()`, `addProviderTiles()`
>   * Lesson 1.3 - Setting the Default Map View
>     * A learning objective: Create a default map by centering on a certain location, setting a default zoom level, and adding markers or pins to your map.
>     * Some functions introduced/used: `setView()`, `addMarkers()`, `addTiles()`

> Chapter 2 - Plotting Points
>   * Lesson 2.1 - Introduction to IPEDS Data
>     * A learning objective: Clean up a map to restore the default view. Create a map step-by-step to gain a better understanding of how your data will dictate the map you create.
>     * Some functions introduced/used: `clearMarkers()`, `clearBounds()`, `count()`, `arrange()`
>   * Lesson 2.2 - Mapping California Colleges
>     * A learning objective: Pan and plot a point on a map using the IPEDS case study.
>     * Some functions introduced/used: `addMarkers()`, `clearMarkers()`, `clearBounds()`,
>   * Lesson 2.3 - Labels and Pop-ups
>     * A learning objective: Center, zoom in, and plot points on the IPEDS map.
>     * Some functions introduced/used: `addTiles()`, `addCircleMarkers()`
>   * Lesson 2.4 - Color Coding Colleges
>     * A learning objective: Enhance the appearance of the IPEDS map by changing the color palette of the markers and adding a map legend.
>     * Some functions introduced/used: `addCircleMarkers()`, `addLegend()`

> Chapter 3 - Groups, Layers, and Extras
>   * Lesson 3.1 - The Leaflet Extras Package
>     * A learning objective: Add search capabilities to your map! Find a location by typing it in a search bar, plus find the name of a location by clicking on a point in your map.
>     * Some functions introduced/used: `addSearchOSM()`, `addReverseSearchOSM()`, `addCircleMarkers()`
>   * Lesson 3.2 - Overlay Groups
>     * A learning objective: Clarify how your data is distributed by adding toggles to group data on your map.
>     * Some functions introduced/used: `dplyr::filter()`, `addLayersControl()`
>   * Lesson 3.3 - Base Groups
>     * A learning objective: Give your user control over their view by adding toggles between base maps.
>     * Some functions introduced/used: `addTiles()`, `addProviderTiles()`, `addLayersControl()`, `setView()`
>   * Lesson 3.4 - Pieces of Flair
>     * A learning objective: Create an advanced and searchable map using special features like clustering.
>     * Some functions introduced/used: `addSearchFeatures()`, `addCircleMarkers()`

> Chapter 4 - Plotting Polygons
>   * Lesson 4.1 - Spatial Data
>     * A learning objective: Define your map boundaries by performing a spatial join.
>     * Some functions introduced/used: `class()`, `slotNames()`, `glimpse()`, `left_join()`
>   * Lesson 4.2 - Mapping Polygons
>     * A learning objective: Perform exploratory data analysis using polygons to examine data missingness.
>     * Some functions introduced/used: `addPolygons()`, `addTiles()`, `base::summary()`
>   * Lesson 4.3 - Putting it All Together
>     * A learning objective: Use interactive web maps to explore and understand the properties of data.
>     * Some functions introduced/used: `slotNames()`, `base::summary()`, `addPolygons()`

  
  - [ ] Does each lesson have a clear learning objective?
  - [ ] Does each lesson include a brief list of functions or packages that the student will use?
  - [ ] Does the outline have at least 12 lessons and no more than 15?

## Step 4: Capstone exercises

Create a capstone exercise for **each chapter**  of your course in the Teach Editor. **(Note: This is different from what you did when you submitted your course outline application, which was just one exercise for the entire course)** Let your Curriculum Lead know when you have completed this step so that they can review your exercises and provide you with feedback.

A capstone exercise should showcase how far learners are likely to get at the end of each chapter.

Please ensure that your capstone exercises pass our [rubric](http://authoring.datacamp.com/courses/exercises/normal-exercises/review-rubric.html) and meet our [content guidelines](https://authoring.datacamp.com/courses/guidelines/content.html).

## Step 5: Build ONE complete lesson on the Teach Editor

This should include:
1. A video exercise with slides (this can be the same as or similar to slides/video that you already created for your audition).
2. Between 2 and 4 exercises that allow students to practice what you taught in the video exercise.  This **does not** include Solution Correctness Tests (SCTs), but **does include** the success message for each exercise.


Why create a lesson as part of your course spec?

It will:

- Allow you to become familiar with the Teach Editor along with our different exercise and slide types earlier.
- Give you a better understanding of course scope (e.g., what can be covered in a reasonable amount of time, and what must be saved for a future course - compared to creating just a course outline.)

In combination, this will result in faster course development time, a more frictionless course development experience, and prevent roadblocks that arise out of miscalibrated course scope.

Our experience working with over a hundred expert instructors over the past 4 years has taught us that the most challenging part of creating a DataCamp course is in understanding the scope of what can be covered in a lesson (and, by extension, a course). 

We believe that students learn best when their hands are on the keyboard, writing code, working with data, and solving problems. Consequently, our courses consist of short  3 to 4-minute videos separated by interactive coding exercises, with occasional multiple choice exercises interspersed. The videos are intended to teach students the concepts necessary to solve the exercises that follow. 

You can read through all of our content guidelines [here](https://authoring.datacamp.com/courses/guidelines/content.html).

Four-minute videos correspond to between **400 and 600 words total** in the script. 

**Teaching data science concepts in this amount of time is not easy:** 
- It forces you to drill down to the essence of the concept and eliminate everything extraneous. 
- It requires a different approach compared to giving 50-minute college lectures.
- Writing such a script as part of your sample lesson will help you in creating a course outline that covers the right amount of content.

All lessons MUST follow our [content guidelines](https://authoring.datacamp.com/courses/guidelines/content.html).

## Lesson Rubric and Process

### Process

**Timeline**

Please work with your Curriculum Lead to ensure that all of the following boxes are checked. Once that happens, the Content Development team will review the lesson within **3 working days**, and you must incorporate the feedback (if any!) within the next **3 working days.** 

**Feedback Delivery**

There will be no more than **2 rounds of feedback** by a Content Developer, and in each round of feedback, the Content Developer will be specific and unambiguous in explaining exactly what revisions are necessary before the course can be considered ready for handoff. If, after two rounds of feedback, the lesson is still not deemed acceptable by the Content Development team, DataCamp will not move forward with course development.

### Lesson Rubric

#### General

- [ ] Does the lesson consist of 1 video followed by 2-4 exercises?
- [ ] Are there at least 2 coding exercises?
- [ ] Is there no more than 1 multiple choice exercise?
- [ ] Is the script for the video between 400 and 600 words?
- [ ] Are the titles of the exercises and slides written in sentence case?
- [ ] Do all of the exercises run on DataCamp in less than 3 seconds?
- [ ] Does the build pass?

#### Video

- [ ] Are the slides dynamic? That is, is there movement on the slides, such as in the form of transitions between bullets and lines of code, or progression through a visual/schema?
- [ ] Are full sentences in slides avoided?
- [ ] Is there a clear learning objective and/or narrative that motivates why the concept is important?
- [ ] Is there code in the slides? Learning by Doing requires Teaching by Doing!
- [ ] Does the code incorporate a relevant dataset that is [not overused](https://authoring.datacamp.com/courses/design/brainstorming-datasets.html)?
- [ ] Is the code properly formatted and placed inside backticks? It is your responsibility to ensure that your slides are properly formatted.
- [ ] Is the (trans)script written in complete sentences, without any bullet points or markdown? The script should correspond to exactly what you will say in the final recording and will be used to generate the subtitles for your course.

#### Exercises

- [ ] Are the [Content Guidelines](https://authoring.datacamp.com/courses/guidelines/content.html) met?
- [ ] Context: 180-780 characters
- [ ] Instructions: 1-4 bulleted instructions
- [ ] Hints: 1-4 bulleted hints
- [ ] Sample/Solution code: Less than or equal to 15 lines of code
- [ ] Success Message: Is there an informative success message?
- [ ] Do the comments in the sample and solution code match?
- [ ] Are the comments abbreviated instructions?
- [ ] Are the comments free of backticks?
- [ ] Is each comment less than 60 characters of length?
- [ ] Does each comment start with a space?
- [ ] Are different sections of code properly spaced?
- [ ] Are the instructions bulleted?
- [ ] Are the hints bulleted?
- [ ] Is the sample code appropriately scaffolded? R courses use 3 underscores.

#### FAQs

##### Which lesson should I create for my sample lesson?

This is your choice. We recommend the final lesson of your course, as it has the following advantages:

- The concepts will likely be more advanced, and confirming that you can adequately teach the material in less than 600 words will verify that the course scope is appropriate.
- Similarly, the code will tend to be more advanced and computationally intensive. Confirming that the code runs on DataCamp and that the exercises meet our content guidelines will provide another check to verify that the course scope is indeed appropriate. 
- It provides clarity on where students will be at the end of the course and a clear stopping point that you can then work towards during the rest of course development.

**Whichever lesson you create, it is important to keep in mind the spirit of the sample lesson:** 
- it is an important check on course scope, 
- an opportunity to acquaint yourself with the tools you will be using to build your course, 
- and a chance to receive early feedback on teaching style to ensure you and DataCamp are aligned on course vision.

## Step 6: Revisit course outline

Having created your sample lesson, you should now have a much better understanding of course scope. This is an ideal time to revisit your outline and update it if necessary.

## Step 7: Write course description and list course prerequisites

**Course Description**

Add a one-paragraph description of the course in the [course.yml](course.yml) file following `description:`.

> An example from a course analyzing survey data

```
description: You've taken a survey (or 1000) before, right? Have you ever wondered
  what goes into designing a survey and how survey responses are turned into actionable
  insights? Of course you have! In Analyzing Survey Data in R, you will work with
  surveys from A to Z, starting with common survey design structures, such as clustering
  and stratification, and will continue through to visualizing and analyzing survey
  results. You will model survey data from the National Health and Nutrition Examination
  Survey using R's survey and tidyverse packages. Following the course, you will be
  able to successfully interpret survey results and finally find the answers to life's
  burning questions!
```

**Prerequisites**

*Which DataCamp courses cover topics that a student should be familiar with before attempting this course? Here are some examples:*

- [Introduction to R](https://www.datacamp.com/courses/free-introduction-to-r)
- [Intermediate R](https://www.datacamp.com/courses/intermediate-r)
- [Intro to the Tidyverse](https://www.datacamp.com/courses/introduction-to-the-tidyverse)
