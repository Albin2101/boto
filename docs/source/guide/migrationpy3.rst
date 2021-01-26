.. _guide_migration_py3:

Migrating to Python 3
=====================

Python 2.7 was deprecated by the `Python Software Foundation <https://www.python.org/psf-landing/>`_ on January 1, 2020 following a multi-year process of phasing it out. Because of this, AWS has
deprecated support for Python 2.7, which means that new releases of the SDK will no longer work on
Python 2.7.

This affects both modules that comprise the AWS SDK for Python: Botocore (the underlying low-level
module) and Boto3 (which implements the API functionality and higher-level features).

Timeline
--------
Going forward, all projects using the AWS SDK for Python need to transition to using Python 3, with
Python 3.6 becoming the minimum by the end of the transition. Boto3 and Botocore will end support
for Python 2.7 effective July 14, 2021, while Python 3.5 and lower will need to be updated to Python
3.6 by February 1, 2021.

Updating your project to use Python 3
-------------------------------------

Before you begin to update your project and environment, make sure you’ve installed or updated to
Python 3.6 or later as described in :ref:`upgrade to Python 3 <quickstart_install_python>`. You can
get Python from the `PSF web site <https://www.python.org/downloads>`_ or using your local package
manager.

After you have installed Python 3, you can upgrade the SDK. To do so, you need
to update both the Boto3 and Botocore Python modules. You can do this globally
or within your
virtual environment if you use one for your project.

To update the AWS SDK for Python
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. Uninstall the currently installed copies of Boto3 and Botocore::

    $ python -m pip uninstall boto3 botocore

2. Install the new version of Boto3. This will also install Botocore, which it requires::

    $ python3 -m pip install boto3

3. (Optional) Verify that the :command:`aws` tool is using the correct version of Python::

    $ python3 -c "import boto3, sys; print(f'{sys.version} \nboto3: {boto3.__version__}')"
    3.8.6 (default, Jan  7 2021, 17:11:21)
    [GCC 7.3.1 20180712 (Red Hat 7.3.1-11)]
    boto3: 1.16.15

If you're unable to upgrade to Python 3
---------------------------------------

It may be that you're unable to upgrade to Python 3, for example if you have a large project that's
heavily dependent on syntax or features that no longer work as desired in Python 3. It's also
possible that you need to postpone the Python transition while you finish updates to your code.

Under these circumstances, you can prepare for the deprecation date in order to avoid inconvenience
when the time arrives by keeping all software up-to-date. If you're using an existing installation
of the AWS SDK for Python on Python 2, you can keep using it even after the deprecation date, but
deprecated versions of Boto3 will not receive further feature or security updates.

pip-based installations
~~~~~~~~~~~~~~~~~~~~~~~

If you installed Boto3 using :command:`pip` 10.0 or later, you'll automatically stop receiving Boto3
updates after the last Python 2 compatible version of the SDK is installed. If you're using an older
version of :command:`pip`, you need to pin your Boto3 install to no later than version 1.17.

Other installation methods
~~~~~~~~~~~~~~~~~~~~~~~~~~

If you installed Boto3 and Botocore from source or by any other method, be sure to download and
install a version released prior to the Python 2.7 deprecation date.
