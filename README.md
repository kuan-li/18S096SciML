# 18.S096 Special Subject in Mathematics: Applications of Scientific Machine Learning

## Lecturer: Dr. Christopher Rackauckas

Machine learning and scientific computing have previously lived in separate
worlds, with one focusing on training neural networks for applications like
image processing and the other solving partial differential equations defined
in climate models. However, a recently emerging discipline, called scientific
machine learning or physics-informed learning, has been bucking the trend by
integrating elements of machine learning into scientific computing workflows.
These recent advances enhance both the toolboxes of scientific computing and
machine learning practitioners by accelerating previous workflows and resulting
in data-efficient learning techniques ("machine learning with small data").

This course will be a project-based dive into scientific machine learning,
directly going to the computational tools to learn how the practical aspects of
"doing" scientific machine learning. Students will get hands-on experience
building programs which:

- Train data-efficient physics-informed neural networks
- Accelerate scientific models using surrogate methods like neural networks
- Solve hundred dimensional partial differential equations using recurrent neural networks
- Solve classical machine learning problems like image classification with neural ordinary differential equations
- Use machine learning and data-driven techniques to automatically discover physical models from data

The class will culminate with a project where students apply these techniques
to a scientific problem of their choosing. This project may be tied to one's
on-going research interest (this is recommended!).

#### Difference from 18.337

Note that the difference from the recent
[18.337: Parallel Computing and Scientific Machine Learning](https://github.com/mitmath/18337)
is that 18.337 focuses on the mathematical and computational underpinning of how
software frameworks train scientific machine learning algorithms. In contrast,
this course will focus on the applications of scientific machine learning,
looking at the current set of methodologies from the literature and learning
how to train these against scientific data using existing software frameworks.
Consult [18.337 Lecture 15](https://mitmath.github.io/18337/lecture15/diffeq_machine_learning)
as a sneak preview of the problems one will get experience solving.

Syllabus
--------

**Lectures**: Monday, Tuesday, Wednesday, and Thursday 1-3pm (2-139). Jan 6 - 31.
Note that there will be no lectures between 13-16.

**Office Hours**: There will be no formal office hours, however help can be found
at the Julia Lab 32-G785 during most working hours.

**Prerequisites**: While this course will be mixing ideas from machine learning
and numerical analysis, no one in the course is expected to have covered all of
these topics before. Understanding of calculus, linear algebra, and programming
is essential. While Julia will be used throughout the course, prior knowledge
of Julia is not necessary, but the ability to program is.

**Textbook & Other Reading**: There is no textbook for this course or the field
of scientific machine learning, so most of the materials will come from
primary literature. For a more detailed mathematical treatment of the ideas
presented in this course, consult the [18.337 course notes](https://github.com/mitmath/18337)

**Grading**: The course is based around the individual projects. 33% of the grade
is based on the writeup due on January 14th, 34% of the grade is based on the
project writeup, and 33% is based on the project presentation.

**Collaboration policy**: Make an effort to solve the problem on your own before
discussing with any classmates. When collaborating, write up the solution on
your own and acknowledge your collaborators.

## Individual Project

The goal of this course is to help the student get familiar with scientific
machine learning in a way that could help their future research activities. Thus
this course is based around the development of an individual project in the area
of scientific machine learning.

Potential projects along these lines could be:

- Recreation of a parameter sensitivity study in a field like biology,
  pharmacology, or climate science
- [Augmented Neural Ordinary Differential Equations](https://arxiv.org/abs/1904.01681)
- [Neural Jump Stochastic Differential Equations](https://arxiv.org/pdf/1905.10403.pdf)
- Acceleration methods for adjoints of differential equations
- Improved methods for Physics-Informed Neural Networks
- New applications of neural differential equations, such as optimal control
- Parallelized implicit ODE solvers for large ODE systems
- GPU-parallelized ODE/SDE solvers for small systems

or anything else appropriate. High performance implementations of library code
related to scientific machine learning is also an appropriate topic, so new
differential equation solvers or GPU kernels for accelerated mapreduce is a
viable topic.

The project is split into 3 concrete steps.

### Part 1: Individual Project Proposal. Due January 12th

The project proposal is a 2 page introduction to a potential project. The proposal
should go over the background of the topic and the proposed methodology to
investigate the subject. It should include at least 3 references and discuss
alternative methods that could be used, and what the pros and cons would be.

**You should be discuss the potential project with the instructor before submission!**

### Part 2: Project Presentation. TBA

Depending on the size of the course, everyone will be expected to give a 20
minute presentation on their project, introducing the class to their topic and
their results. This will take place during the last week of the course.

### Part 3: Project Report. Due February 4th

The final project is a 8-20 page paper using the style
template from the [_SIAM Journal on Numerical Analysis_](http://www.siam.org/journals/auth-info.php)
(or similar). The final project must include the code for the analysis as a
reproducible Julia project with an appropriate Manifest. Model your paper on
academic review articles (e.g. read _SIAM Review_ and similar journals for
examples).

By default these projects will be shared on the course website. You may choose
to opt out if necessary. Additionally, projects focusing on novel research may
consider submission to Arxiv.

## Schedule of Topics

A brief overview of the topics is as follows:

- Introduction to Scientific Machine Learning
- Machine Learning for SciML: how to think about, choose, and train universal approximators
- Introduction to Julia: package/project development and writing efficient code
- Applied numerical differential equations for scientific modeling
- Estimating model parameters from data
- Training neural networks to solve differential equations
- Event handling and complex phenomena in neural-embedded models
- Physics-Informed Neural Networks (PINNs)
- Neural differential equations and universal differential equations
- Acceleration of partial differential equations with neural network approaches
- Choosing neural networks, optimizers, learning rates, and diagnosing fitting
  issues
- Turn neural networks back into equations with SInDy
- Tweaking differential equation solvers to accelerate fitting
- Choices for gradient calculations: differences and understanding the appropriate
  methods to use
- Writing good code for GPU acceleration

## Lecture 1: Introduction to Scientific Machine Learning

#### Lecture Notes

- [What is Scientific Machine Learning?](https://mitmath.github.io/18S096SciML/lecture1/scientific_ml.pptx)

#### Optional pre-reading materials

- [The Essential Tools of Scientific Machine Learning](http://www.stochasticlifestyle.com/the-essential-tools-of-scientific-machine-learning-scientific-ml/)
- [Workshop videos on Scientific Machine Learning](https://icerm.brown.edu/events/ht19-1-sml/)

#### Summary

We will start off by setting the stage for the course. The field of scientific
machine learning and its span across computational science to applications in
climate modeling and aerospace will be introduced. The methodologies that will be
studied, in their various names, will be introduced, and the general formula that
is arising in the discipline will be laid out: a mixture of scientific simulation
tools like differential equations with machine learning primitives like neural
networks, tied together through differentiable programming to achieve results
that were previously not possible.

Don't be worried if this introduction is fast: we'll be going back through
each of these examples in detail, learning how to implement and use these methods.
Today is mostly to introduce the motivation behind learning these methodologies.

## Lecture 2: Introduction to Julia for Scientific Machine Learning

##### Lecture Notes

##### Optional pre-reading materials

It may be a good idea to learn how to write efficient code. Here's a few materials
along those lines:

- [Optimizing Serial Code](https://mitmath.github.io/18337/lecture2/optimizing)
- [Optimizing Your DiffEq Code](http://tutorials.juliadiffeq.org/html/introduction/03-optimizing_diffeq_code.html)
- [Type-Dispatch Design: Post Object-Oriented Programming for Julia](http://www.stochasticlifestyle.com/type-dispatch-design-post-object-oriented-programming-julia/)
- [Performance Matters](https://www.youtube.com/watch?v=r-TLSBdHe1A)
- [You're doing it wrong (B-heaps vs Binary Heaps and Big O)](http://phk.freebsd.dk/B-Heap/queue.html)
