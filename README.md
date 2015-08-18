# Mentorsup

Mentorsup is a new way for fledging developers to get mentorship on their GitHub repos and experienced developers to give back.

## Why?
Recently I came across a GitHub repo of someone that was just learning to program. Reading through their code, I noticed there was a section in which they were doing more work than they had to do. I wanted to help, but didn't want to come off as a jerk by randomly giving them tips.  

What if there was a way for new developers to signal that they needed help? What if there was a way for experienced programmers to easily find new programmers that they could help in their free time?  

There is a need to grow the base of programmers, particularly among communities that are underrepresented in software development. There are many great efforts towards this goal and this project will attempt to support those efforts.

## How Does It Work?

Developers looking for feedback on their project (hereby referred to as a "mentee") add a `mentorship.json` file into their GitHub repo(s). This file, inspired by `package.json` from the JavaScript world, includes the details of their project and how they will accept feedback.  

The Mentorsup web application will crawl GitHub for projects' `mentorship.json` files and display them on in a web application that mentors can browse to find projects that they can help out on. Potential mentors read through the code of a project that they are experienced in and submit feedback where appropriate.

## `mentorship.json` Specification

The `mentorship.json` file is a valid JSON file that details the project and mentorship terms. The specification is a work in progress and will certainly change.  

```json
{
    "name": "mentorsup",
    "description": "Mentorsup is a new way for fledging developers to get mentorship on their GitHub repos and experienced developers to give back",
    "repo": "http://github.com/davewalk/mentorsup",
    "langs": ["python", "CSS", "HTML", "JavaScript"],
    "libraries": ["django"],
    "keywords": ["mentorship", "learning", "teaching", "software development"],
    "authors": [
        { 
            "name": "Dave Walk",
            "email": "daviddwalk@gmail.com",
            "url": "http://davewalk.net",
            "github": "davewalk"
        }
    ],
    "mentorship": {
        "terms": {
            "mediums": ["issues", "email"],
            "guidelines": "All feedback must be constructive. Please keep in mind that while I have used Django a bit in the past this will be my first full Django project."
        },
        "mentors": [
            { 
                "name": "John Doe",
                "email": "johndoe@gmail.com",
                "url": "http://johndoe.com",
                "github": "johndoe",
                "count": 2
            }
        ]
    }
}
```

#### name [string]
The name of the project. Does not have to the same name as the GitHub repostiory.

#### description [string]
A description of the project.

#### repo [string]
The URL of the repo.

#### langs [array]
A list of one or more programming languages that the mentee is requesting feedback on. This does not have to be the full list of languages that your project uses, just the ones that you need help with.  

Also while CSS, HTML and some others are not actually "programming languages" but for the sake of brevity they can be included in this list if they are what you need help with.

#### libraries [array]
The list of libraries/frameworks that the mentee is requesting feedback on.

Like `langs` above, this is intentionally vague so as to handle as many use cases as possible.

#### keywords [array]
A list of keywords about the application for discovery on the Mentorsup website.

#### authors [array]
An array of author objects describing the authors of this project. `github`, for the person's GitHub username, is the only required key/value but `email`, `url` and `name` will also be included on the Mentorsup website if they exist. You may also want to include social media details here if you accept feedback via those mediums (see mentorship terms below).

#### mentorship [object]
Describes the details of the mentorship opportunity. Must include `terms` and `mentors` values.

**terms** -> **mediums** [array]  
A list of strings conveying how you will accept feedback. Valid values at this time are `issues` (meaning GitHub issues) or `email`. It is important that these values are exactly these so that the Mentorsup crawler can correctly display your repo's info.

**terms** -> **guidelines** [string]  
Describes the guidelines of submitting feedback.

**mentors** [array]  
Lists the mentor(s) that have helped on this repo so far. The structure of the object is identical to the `authors` object with the addition of a `count` value for signifying how many times the mentor helped.

## Future

There are many things that this system can explore if there is a demand for it.  Potential ideas:

* Badges: embeddedable images that show how many times someone has mentored through Mentorsup
* Twitter feed: of new projects that have recently been added to the app

## Name
Still open to better names! Maybe there should be an exclamation point at the end? "Mentorsup!" Hmm.

## Feedback/Help
I'm intentionally starting this project as only a `README` file to gather as much feedback as possible before I start coding. Have questions, suggestions, anything else? Want to help? Please email me at daviddwalk at gmail dot com or open an issue in this repo.