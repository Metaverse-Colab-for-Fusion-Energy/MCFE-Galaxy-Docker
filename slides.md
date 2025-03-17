---
marp: true
theme: uncover
paginate: true
header: Oliver Woolland - Workflows: a user perspctive
footer: RSE Show and Tell, March 2025
---

### **Workflows**: a user perspective
### Oliver Woolland (RSE, 2025)

---

# What is a workflow?

---
### My answer ~2022:

#### **Formalised chains of software tools, explicitly defining the flow of data between them.**

- **Abstract**: logic separate to data, remix / compose
- **Automated**: reusable, reproducible, provenance
- **Scalable and portable**: local / HPC, Windows / Linux
- **Shareable and citable**: publishable, create DOIs

---

## What is a workflow *for a user?

Workflows are really about:
- **Enabling research** not setting up computers 
- **Doing research** not manually running tools
- **Accelerating research** using HPC / cloud
- **Sharing research** not just reports and papers

---

## So what changed?

I became familiar with Galaxy!

(and spent more time with researchers)

--- 

## Why Galaxy changed my mind?
<style scoped>
section {
    font-size: 30px;
}
</style>

⛔ Installing a framework / tool / docker / plugin
✅ Just use your browser
####
⛔ Installing tools
✅ Just use your browser
####
⛔ YAML / Python / text editor faffing
✅ Just use (the GUI) in your browser
####
⛔ "Yeah you can use my workflow! Clone this repo, install this tool, configure this library, download this file"
✅ "Just go to [your URL] in your browser"

---

### "But my workflow engine is **better** 😤"

Well, maybe. But as a group we should pick one.

List of 361 workflow engines:
https://github.com/common-workflow-language/common-workflow-language/wiki/Existing-Workflow-systems

---

## Why Galaxy is good enough

- Administered by sysadmins not users
- Browser interface is best for users
- Can interfce with HPC
- Has an API
- Actively developed
- Widely adopted
- Extensive training materials

---

# **Can I prove Galaxy is good enough?**

### I think so! 
Let's look at a worked example

#### The research aim: 
**To mine data from a database of phrases**

---

## Demo

### Time for chaos

--- 

# What did we see?

- Researchers doing research! 
- Without any setup
- Using tools, making workflows, sharing output

---

## How would this look for RSEs?

- No more unguided learning of workflow engines
- We can form a community 
- We can pool config, tools, visualisations, workflows

#### We do less work

But... how do we start?

---

##### **Doesn't Galaxy needs a server to set up and maintained?**

##### **Doesn't Galaxy make it hard to do local development?**

I thought this for a long time but now have an answer!

Clone this repo for an example **self hosted Galaxy using Docker**

---

### Example tool

```xml
<tool id="letter_count" name="Letter Count" version="0.1.0">
  <description>Counting letters in a string</description>
  
  <requirements>
    <container type="docker">python:3.13-slim</container>
  </requirements>
  
  <command>
    <![CDATA[
      python '$__tool_directory__/letter_count.py' '$input_file' '$output_file'
    ]]>
  </command>

  <inputs>
    <param type="data" name="input_file" label="Sentance File" help="Enter the string to count the letters" />
  </inputs>

  <outputs>
    <data format="txt" name="output_file" label="Letter Count" help="Output file containing the letter count" />
  </outputs>
  
  <help>
    This tool counts the number of letter in each word of a string.
  </help>

</tool>
```

---

![bg fit](./overall_workflow.png)

---

## Galaxy's big question 

### **Wont the Galaxy server die at the end of my project?**

Well...

---

## My suggestion(s)

We trail a persistant, central Galaxy instance for RSEs

We put a workstation *under a desk*

--- 

## The future

If the instance too popular and a workstation can't cope:
- Good problem to have!
- Can investigate backing on to HPC / cloud

If it is not:
- Nice workstation for someone

If we don't step up and instance:
- Galaxy is still a good choice for projects!
- The Docker solution makes it easy to get set up and working
- I am happy help anyone that is interested

---

## Conclusions

- Workflows should be about:
  - user experiences
  - enabling research
- We can save ourselves pain by standardising
- [Opening Up Reserach](https://www.manchester.ac.uk/about/news/opening-up-research-202425/)

## We should (gently) start to host our own Galaxy
