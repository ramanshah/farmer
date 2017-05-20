# In-browser implementation of FARMER

*Under construction*

## What is FARMER?

My friend Toan and colleagues developed the FARMER method, standing for Fast
and Accurate Relocation of Microscopic Experimental Regions. Briefly, for many
kinds of science involving microscopes, you want to be able to take a picture
of a tiny structure (say a cell or nanostructure on a microscope slide) with
one microscope, carry the structure over to another kind of microscope, and
take a different kind of picture of it there too. Finding the tiny object in
the second microscope is the challenge. Before this work, one would customarily
spend "grad student capital" or submit to complex micro/nanofabrication of
guide markers to help you find your object on two different platforms. The
authors developed a three-point calibration using amazingly low-tech tools
(e.g., permanent markers) along with some linear algebra and geometry to find
the object. With (x,y,z) coordinates of the three conspicuous spots, one can
solve for the transformation (a translation, rigid body rotation, and scale
determination of the microscope's three axes) and interpolate the position of
the object on the second microscope.

You can read about it here:

T. Huynh, M. K. Daddysman, Y. Bao, A. Selewa, A. Kuznetsov, L. H. Philipson, &
N. F. Scherer. [Correlative imaging across microscopy platforms using the fast
and accurate relocation of microscopic experimental regions (FARMER)
method](http://dx.doi.org/10.1063/1.4982818). Rev. Sci. Inst. 88:5, 053702,
2017.

## Problem statement

A typical setting is an expensive microscope in a core facility. Such a
microscope is typically operated by a dedicated computer running Windows. The
computer is kept disconnected from the network for cybersecurity reasons; blank
CD-R discs are supplied to take data away from the machine. The instrument is
administered by a risk-averse professional. One wants to be able to run FARMER
on such a system but also for FARMER to be highly ergonomic on more permissive
systems (say, the researcher's Internet-connected laptop carried into such a
facility). Despite the lack of network connection, the microscope computer will
often have a vestigial copy of Internet Explorer.

An in-browser implementation of FARMER is motivated by these constraints. To
get FARMER onto a microscope computer, one would have to convince the
administrator to install a few HTML/CSS/JS files, which is a lower bar than
installing executable binaries. And if network-connected, one could run such an
application merely by pointing one's broswer to `github.io` or similar.

## Requirements for our solution

- Enter reference and region-of-interest coordinates in forms in the app.
- Hit "Calculate" and get FARMER results.
- Read CSV of entered values (typically from the first microscope) from a file.
  (One could not do this on a locked-down machine, but it should be available
  for permissive environments.)
- Write CSV of entered/calculated values to a file. (One can even do this on a
  locked-down machine.)
