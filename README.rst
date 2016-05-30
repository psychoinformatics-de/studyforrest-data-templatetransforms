studyforrest.org Dataset
************************

|license| |access|

Template images and image space transformations
===============================================

This repository contains data derived from the raw data releases of the
*studyforrest.org* project. In particular these are:

* participant/scan-specific template images
* transformation between these respective image spaces

For more information about the project visit: http://studyforrest.org

File name conventions
---------------------

Each directory in the subject directories and the "templates" directory
corresponds to one image template. Templates in ``sub*`` directories are
participant-specific (not aligned across participants). However, templates with
the same name have corresponding input data. Templates in the ``templates``
directory have been derived from all participants, and there are typically
transformation from participant specific templates into the group template
space provided. Group template images carry a ``grp`` prefix in their label.

All transformations are the output if FSL tools: either MAT files with
4x4 affine transformation matrices from FLIRT, or FNIRT warp files.

Here is an example of how transformations can be located. The transformation
of the template image created from all 3T BOLD images of participant ``01``
acquired in phase 2 of the project into the group template space for 3T BOLD
scans can be found in:

``sub-01/bold3Tp2/in_grpbold3Tp2/subj2tmpl_warp.nii.gz``

Each template directory contains one or more image files with more-or-less
self-explanatory names, such as "head", "brain", or "brain_mask". File with
such a name in the one of the ``in_*`` folders represent the image in the parent
folder, aligned and resliced to the target space for this transformation.
These images can be used to inspect the quality of the transformation.

Lastly, the ``code/`` directory contains the source code for computing template
images and transformation between them.


How to obtain the dataset
-------------------------

This repository contains metadata and information on the identity of all
included files. However, the actual content of the (sometime large) data
files is stored elsewhere. To obtain any dataset component, git-annex_ is
required in addition to Git_.

1. Clone this repository to the desired location.
2. Enter the directory with the local clone and run::

     git annex init

   Older versions of git-annex may require you to run the following
   command immediately afterwards::

     git annex enableremote mddatasrc

Now any desired dataset component can be obtained by using the ``git annex get``
command. To obtain the entire dataset content run::

     git annex get .


Keep data up-to-date
--------------------

If updates to this dataset are made in the future, update any local clone by
running::

     git pull

followed by::

     git annex get .

to fetch all new files.




.. _Git: http://www.git-scm.com

.. _git-annex: http://git-annex.branchable.com/

.. |license|
   image:: https://img.shields.io/badge/license-PDDL-blue.svg
    :target: http://opendatacommons.org/licenses/pddl/summary
    :alt: PDDL-licensed

.. |access|
   image:: https://img.shields.io/badge/data_access-unrestricted-green.svg
    :alt: No registration or authentication required
