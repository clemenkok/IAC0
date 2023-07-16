# IAC0: A Repository to plug the missing gaps

There are several important skills that are needed to succeed in second year. This repository contains several tutorials on how to pick them up. It is recommended that you spend some time learning the basics below as the year goes by. Some are relevant for the IAC lab (Linux, Git), so check them out before the first lab.

Feel free to create a pull request.

## Progress

- [ ] [General Advice](#general-advice)
- [ ] [C++ and OOP](#cpp-and-oop)
- [ ] [Linux and the Command Line](#linux-and-the-command-line)
- [ ] [Scripting](#scripting)
- [ ] [Git](#git)
- [ ] [Docker](#docker)
- [ ] [Cloud](#cloud)
- [ ] [Vim](#vim)

## General Advice

- Start your internship hunt early (like right now). Use a popular CV template such as [Jake's CV Template](https://www.overleaf.com/latex/templates/jakes-resume/syzfjbzwjncs).  
- Learn some LaTeX - will come in handy for report writing.

Refer to the table below to find out what langauges / frameworks you will need to learn:  
|Modules|Technologies|
|---|---|
|ELEC50006 Discrete Mathematics|Python|
|ELEC50011 Mathematics for Engineers IIA/B|NIL (Math)|
|ELEC50014 Software Systems|Python, SQL|
|ELEC50002 Communications|LabView|
|ELEC50004 Control Systems|MATLAB|
|ELEC50003 2nd Year Project|Depends on your subsystem. Command - React, Node.js, AWS, Control - MATLAB, Drive - C++, Vision - FPGA/C++, Power - C++, Integration - RTOS.|
|ELEC50009 Information Processing|Depends on your subsystem. If you're doing the FPGA part, you need to know how to use Quartus, C, SystemVerilog and UART (so Python). If you're doing a game, probably Unity/C# (some people used common webdev stacks too). Cloud/Databases - AWS, SQL, Python.|
|ELEC50010 Instruction Architectures and Compilers|Autumn part - SystemVerilog, C++. Spring part - C++, Flex, Bison (brush up on OOP)|

## C++ and OOP

## Linux and the Command Line

## Scripting

## Git

## Docker

### What's Docker?

Docker is a tool that lets developers easily create, deploy and run applications in a consistent and reproducible environment. It does this through containers.  

A container is a standalone executable package of software that includes everything needed to run an application, including code, libraries, system tools and settings.  

Docker lets developers create container images that include applications and its dependencies, then deploy those images to systems that have Docker installed.

### The Container Analogy

A shipping container provides a standardized, secure and portable way to transport goods. Similarly, Docker provides a standardized, secure and portable way to transport software applications.

Additionally, just like how shipping containers are sealed and separated from one noather, Docker containers provide isolation and ensure that applications are not affected by conflicts with other applications/the host system.

### Getting Started

Install Docker [here](https://www.docker.com/).

The Docker [getting-started](https://docs.docker.com/get-started/02_our_app/) tutorial is an excellent introduction to Docker.  

### Advice

- Learn how to write Dockerfiles, they will come in handy during projects / internships.
- A good resouce you can follow would be these [tutorials](https://www.bogotobogo.com/index.php).
- Starting with Docker is a good first step in learning Kubernetes, which is used by most major companies. I'd recommend spending some time learning about [what Kubernetes is](https://kubernetes.io/docs/concepts/overview/) and how companies use it, for general awareness.

## Cloud

### What's Cloud Computing and why is it important?

Cloud Computing delivers compute resources over the Internet via pay-as-you-go pricing. This is important beacuse it enables (1) agility, since companies do not need to pay upfront for compute, (2) elasticity, since companies do not need to over-provision resources up front to deal with peaks in business activity, (3) cost, since companies can trade upfront expenses for variable expenses (with the added benefit of economies of scale), (4) performance - cloud companies have servers all over the world which you can deploy to, enabling reductions in latency.  

### Why is Cloud Computing important for YOU?

As you may have read above, cloud computing (AWS) is used in several modules - namely InfoProc and the 2nd year project. If you are an aspiring developer, it'll come in extremely useful during work ([most companies engage a major cloud provider one way or another](https://aws.amazon.com/industries/?nc2=h_ql_sol_ind_id)).    

### Useful Resources

- [Cloud Resume Challenge](https://cloudresumechallenge.dev/)
- [AWS Skill Builder](https://skillbuilder.aws/)

### Advice

- Learn Infrastructure-as-Code, it's the modern standard to deploy and interact with cloud resources. Picking up [Terraform](https://developer.hashicorp.com/terraform/tutorials/aws-get-started/infrastructure-as-code) and doing a few projects with it serves as a good starting point. Terraform is good because it's cross-platform, meaning that it works with any cloud provider.
- Get to know your Python, Linux and Networking fundamentals first. I recommend watching [this series of videos](https://learn.cantrill.io/p/tech-fundamentals).

## Vim 

### What's Vim and how to get started?

Vim is a command line terminal interface. It's important when you want to edit code on systems which may not have the capacity to support a GUI. Many people also use it because its simply faster to code with Vim. You'll understand more as you learn it.  

## Contributor Appreciation

Thanks to the following people for contributing to this repository:

- [Clemen Kok](https://clemenkok.com/) (BEng'24)
