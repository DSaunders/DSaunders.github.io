---
layout: post
title:  "We're all architects"
subtitle: ""
date:   2014-05-04 13:00:00
---

We seem to use the term 'Software Architect' to represent a certain person, or
level, within an organisation.

I'm not sure I'm keen on this. It implies that there is one person that is
responsible for all of the 'architectural stuff' on the project.

When I hear this term, It makes me think of a software project like building a house. The architect
designs the house, the builders and other contractors are responsible for their
own individual trade, but have little or no say in how the house looks or functions.

<span class="full-width-image">
  ![Everybody is an architect](/img/everybodyarchitect/OldModel.png)
</span>

I've worked on projects like this, and I can't say I liked it that much.

The further removed from the 'architect' you are, the less invested you are in the
project. That's not to say that the people at the bottom of the pyramid don't
care (I was one of these people and I can tell you that I most certainly *did*
care) it's just that they have little or no influence, as they are abstracted from
any decisions that matter.


#'Everybody is an Architect'

I subscribe to a different philosophy, I think *everybody is an architect*.
In this model, a software project is more analogous to building a town than an
individual house.

<span class="full-width-image">
  ![Everybody is an architect](/img/everybodyarchitect/MacroArchitecture.png)
</span>

Here, we still have somebody who oversees the entire project. This person is
responsible for making sure that all of the individual, smaller, building projects adhere
to the overall standard. He/she is tasked with the bigger decisions, like how the
individual elements fit together, but they are not responsible
for micro-managing every individual element itself.

This person is more like a 'town planner' than an architect. They are responsible
for what I call the *Macro Architecture* of the project.

The developers in this model are tasked with creating their own building in our
town. They are responsible for the architecture of this themselves, providing
they adhere to the principles outlined by the *Macro Architect*. How a developer
solves a problem is their own responsibility, all that matters to the rest of
the project is that the problem is solved. This could be a small task (e.g create a contact
  form) or a larger element (e.g. build the data layer).  

These developers are responsible for their own *Micro Architecture*.

I want to be clear that I am not talking about micro-services here.
This is not about how a project is structured or how elements communicate with each
other, it's more about how
developers are empowered to work on a section of a project without being micro-managed
from above.

<br/>

The *everybody is an architect* model does require a lot of trust in your team
though.

Each developer must be trusted to deliver their own element of the project without
micro-management. The *Macro Architect* also carries a lot of responsibility; they
must ensure that they have a clear vision for the project as a
whole and that they can communicate it effectively, to ensure that the end
result is a unified solution, rather than many
disparate elements all struggling to fit together.

Overall though, I think we can build better software, faster, by empowering
*everybody* to be responsible for it's architecture.
