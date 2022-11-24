---
layout: post
title: "Data Visualization vs Design Aesthetics"
date: 2015-05-06
---

<style>body {text-align: justify}</style>

Data Visualization is often mistaken for design aesthetics. I was made more aware of this recently when a course on Data Visualization was offered here in school. I only attended the first lecture but I have been more or less aware of the course material and was quite skeptical about the course content. In my opinion they did not make a distinction between data visualization and design aesthetics. Though Design Aesthetics is important for marketing a product or making a more attractive presentation etc.. it is not critical to problem solving, but Data Visualization is very critical to solving problems. Hence the distinction between the two has to be made.

Data Visualization is most important in getting an intuitive grasp of an algorithm or a geometric manipulations of data in multi dimensional space.

Geometric manipulation could be stuff like Principal Component Analysis, Image convolution, or the kernel trick etc... ( this is a good example of visualizing geometric manipulations - http://setosa.io/ev/principal-component-analysis/ ). A good visualization will give an intuitive understanding of a concept and will internalize your understanding of the concept. Research/Problem-solving is as much about mathematical rigor as it is about creativity. And creative or innovative solutions are not possible without an intuitive grasp of the concepts.

Visualization could also be crucial to designing algorithms - it could help us in choosing the right feature extraction techniques, or in choosing the right heuristic for an NP-Hard problem and so on. For example Bin Packing is an NP-Hard problem, and one of the popular heuristics which gives reasonable bounds in time and accuracy is to segregate the objects based on their size; large objects are first used to fill the bins and then small objects are used to stuff the space remaining in each of the bins after the large objects have been placed in them. This gives a solution with a reasonably tight bound. But in order to know if we can use this heuristic we first need to know the distribution of the sizes of the various objects. If we have all medium sized objects then this heuristic will probably not work. In such cases a good visualization can come in handy.

There was a competition in kaggle, some time back, about Packing Santa's Sleigh, which is slightly similar to the bin packing problem mentioned above, except that, instead of 1-d objects like in the traditional bin packing problem, we have 3-d objects( huge number of objects ~ 100,000) that have to be stacked on a 2-d sleigh with minimum height, and adhering to an ordering condition of the objects. You could see this problem as bin packing or a dynamic programming problem. But in either case we first need an idea about the different height, width, depth and volume details of the different objects. The following visualizations gives an idea about the dimensions of the different objects and might guide us in choosing the right approach to solve them -

<img src="/images/dataviz-sizes.png" alt="Present Sizes" style="height: 200px; width:350px;"/>

<img src="/images/dataviz-opacity.png" alt="Transparent View of Presents" style="height: 200px; width:200px;"/>

Following is an isometric view of all the objects places on a single plane.

<img src="/images/dataviz-isometric.png" alt="Isometric View of Presents" style="height: 200px; width:200px;"/>

As we can see Data Visualization has a clear role to play in coming up with creative and accurate solutions for problems.

On the other hand, stuff like designing an aesthetically appealing resume, or a dream childhood bedroom, or color coding of graphs or design templates for powerpoint presentations etc.. clearly gets categorized as design aesthetics and not data visualization. Though such techniques have their value in marketing a product, they do not play a role in solving the problems.

As shown below these exact topics were some of the assignments given in the Data Visualization class, which I do not think quite fits in with the subject of Data Visualization.

<img src="/images/dataviz-tweet.png" alt="Instructor's tweet" style="height: 300px; width:300px;"/>

I think they both have their significance but their difference need to be noted.