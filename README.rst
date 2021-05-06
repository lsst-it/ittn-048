.. image:: https://img.shields.io/badge/ittn--048-lsst.io-brightgreen.svg
   :target: https://ittn-048.lsst.io
.. image:: https://github.com/lsst-it/ittn-048/workflows/CI/badge.svg
   :target: https://github.com/lsst-it/ittn-048/actions/

#############################
CentOS System Disk Encryption
#############################

ITTN-048
========

The Linux Unified Key Setup (LUKS) is a disk encryption, which implements a platform-independent standard on-disk format for use in various tools.  
The Policy-Based Decryption (PBD) is a collection of technologies that enable unlocking encrypted root and secondary volumes of hard drives on physical and virtual machines using different methods like a user password, a Trusted Platform Module (TPM) device, a PKCS#11 device connected to a system, for example, a smart card, or with the help of a special network server.
The PBD as a technology allows combining different unlocking methods into a policy creating an ability to unlock the same volume in different ways. The current implementation of the PBD in Red Hat Enterprise Linux consists of the Clevis framework and plugins called pins. Each pin provides a separate unlocking capability. For now, the only two pins available are the ones that allow volumes to be unlocked with TPM or with a network server.
The Network Bound Disc Encryption (NBDE) is a subcategory of the PBD technologies that allows binding the encrypted volumes to a special network server. The current implementation of the NBDE includes Clevis pin for Tang server and the Tang server itself. 
Based on this tools, the Servers System Disk will we encrypted and when they boot, will request decryption to a centralized server that withholds the Decryption module, avoiding the password prompt at boot. 

Links
=====

- Live drafts: https://ittn-048.lsst.io
- GitHub: https://github.com/lsst-it/ittn-048

Build
=====

This repository includes lsst-texmf_ as a Git submodule.
Clone this repository::

    git clone --recurse-submodules https://github.com/lsst-it/ittn-048

Compile the PDF::

    make

Clean built files::

    make clean

Updating acronyms
-----------------

A table of the technote's acronyms and their definitions are maintained in the ``acronyms.tex`` file, which is committed as part of this repository.
To update the acronyms table in ``acronyms.tex``::

    make acronyms.tex

*Note: this command requires that this repository was cloned as a submodule.*

The acronyms discovery code scans the LaTeX source for probable acronyms.
You can ensure that certain strings aren't treated as acronyms by adding them to the `skipacronyms.txt <./skipacronyms.txt>`_ file.

The lsst-texmf_ repository centrally maintains definitions for LSST acronyms.
You can also add new acronym definitions, or override the definitions of acronyms, by editing the `myacronyms.txt <./myacronyms.txt>`_ file.

Updating lsst-texmf
-------------------

`lsst-texmf`_ includes BibTeX files, the ``lsstdoc`` class file, and acronym definitions, among other essential tooling for LSST's LaTeX documentation projects.
To update to a newer version of `lsst-texmf`_, you can update the submodule in this repository::

   git submodule update --init --recursive

Commit, then push, the updated submodule.

.. _lsst-texmf: https://github.com/lsst/lsst-texmf
