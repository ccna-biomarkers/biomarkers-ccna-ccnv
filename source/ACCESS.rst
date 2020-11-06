Access
======

Data Transfer Agreement (DTA)
:::::::::::::::::::::::::::::

To access the CCNA dataset, it is required to complete a form with a brief description of planned analyses, and complete an inter-institutional data transfer agreement.
The DTA must be signed by the researcher responsible for the project as well as a representant of the main acadamic institution where the research team is affiliated.
The application will be evaluated by a data access committee and, if approved, a transfer key will be shared with the research team in order to transfer the data (see :ref:`Downloading the dataset` section below).
The operations of the data access committee are still being established.

How to acknowledge
::::::::::::::::::

We require that all publications using the CCNA data include the following language in the acknowledgement section:
  
  The CCNA biomarker project...

The CCNA biomarker team is based at "Centre de Recherche de l'Institut Universitaire de Gériatrie de Montréal", with several other institutions involved.
See the CCNA biomarker documentation for an up-to-date list of contributors (https://ccna-biomarkers.readthedocs.io/en/latest/AUTHORS.html). 

In addition, we encourage you to include the name of the cneuromod data release used in the analysis (e.g. ccna-2020), as well as any relevant excerpt from this documentation.
Although some journals flag reproductions of technical documentation as plagiarism, using a standardized wording help consistency and reproducibility in the literature.
Please reproduce this documentation verbatim to the greatest extent possible, and justify to the editor that this practice does not fall under plagiarism.

.. note::
  Multiple versions of the documentation exist, one for each CCNA release, so please make sure to use excerpts from the correct version of the documentation, matching the data release used in the analysis. 

Ethics
::::::

The ccna biomarker project has been approved by the institutional research ethics board of the `CIUSSS du Centre-Sud-de-l'île-de-Montréal <https://ciusss-centresudmtl.gouv.qc.ca/propos/services-en-anglais>`_.
The CIUSSS is a large governmental health organization, and the core NeuroMod team is based at the Research Centre of the Montreal Geriatric Institute (`CRIUGM <http://www.criugm.qc.ca/en.html>`_), which is a part of the CIUSSS, and affiliated with the `University of Montreal <https://www.umontreal.ca/>`_.

The ethics documentation may be useful for research teams to receive ethics approval for secondary analysis by their local institutions, if required.

* `approval_irb_ciusss_french.pdf <./_static/ethics/approval_irb_ciusss_french.pdf>`_: letter of approval from the institutional review board for the CCNA biomarker project.
* scientific overview of the CCNA biomarker project.
* the informed consent form signed by participants.

Downloading the dataset
:::::::::::::::::::::::

All data are made available as a `DataLad collection (currently requires to be part of the biomarker team) <https://github.com/ccna-biomarkers>`_ on github.
`DataLad <https://www.datalad.org/>`_ is a tool for versioning a large data structure in a git repository. The dataset can be explored without downloading the data, and it is easy to only download the subset of the data you need for your project.
See the `DataLad handbook <http://handbook.datalad.org/en/latest/>`_ for further information.

We recommend creating an SSH key (if not already present) on the machine on which the dataset will be installed and adding it to github.
See the official `github instructions <https://help.github.com/en/enterprise/2.15/user/articles/adding-a-new-ssh-key-to-your-github-account>`_ on how to create and add a key to your account.

To obtain the data, you need to install a recent version of the `DataLad software <http://handbook.datalad.org/en/latest/intro/installation.html>`_, available for Linux, OSX and Windows.

  .. note::
    You will need to have valid login credentials to access the NeuroMod git as well as the NeuroMod `Amazon S3 <https://aws.amazon.com/s3>`_ fileserver.

Once you have obtained these credentials, you can proceed as follows in a terminal:

.. code-block:: bash

  # Install recursively the dataset and subdataset of the current project.
  # If using ssh git clone as follow, you can set your public SSH key in the present git to ease future updates.
  datalad install -r git@github.com:courtois-neuromod/cneuromod.git
  # If errors show up relative to .heudiconv subdataset/submodule, this is OK, they are not published (will be cleaned up in the future).
  cd cneuromod

You will most likely want to checkout a stable release tag for your analyses. For instance:

.. code-block:: bash

  git checkout ccna-2020

We now set as environment variable the credentials to the file server. The s3 access_key and secret_key will be provided by the data manager after being granted access to cneuromod by the user access committee.

.. code-block:: bash

  # This needs to be set in your `bash` everytime you want to download data.
  export AWS_ACCESS_KEY_ID=<s3_access_key>  AWS_SECRET_ACCESS_KEY=<s3_secret_key>

You can now get data using:

.. code-block:: bash

  datalad get -r <any/file/in/the/dataset.example>


Updates
:::::::

The dataset will be updated with new releases so you might want to get these changes (unless you are running analyses, or trying to reproduce results). The master branch will evolve with the project, and can be unstable or messy.
Thus, we recommend using specific release tags.

.. code-block:: bash

  git checkout 2020-alpha2 # checkout the dataset tag
  git submodule update --init # checkout the subdatasets corresponding commits

There is one stable release per year, e.g. ``ccna-2020``, which is preceded by one or multiple alpha release (e.g. ``ccna-2020-alpha``), beta release (e.g. ``ccna-2020-beta``) and release candidate (e.g. `cneuromod-2020-rc`).

To update your dataset to the latest version, use:

.. code-block:: bash

  # update the dataset recursively
  datalad update -r --merge

Once your local dataset clone is updated, you might need to pull new data, as some files could have been added or changed.
