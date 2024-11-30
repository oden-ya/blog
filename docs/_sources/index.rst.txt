.. blog documentation master file, created by
   sphinx-quickstart on Tue Jul 30 00:19:58 2024.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

blog documentation
==================

Add your content using ``reStructuredText`` syntax. See the
`reStructuredText <https://www.sphinx-doc.org/en/master/usage/restructuredtext/index.html>`_
documentation for details.


.. toctree::
   :maxdepth: 4
   :caption: Contents:

AWS
=================================
Manegement & Governance
------------------------------
.. toctree::
   :maxdepth: 1
   :caption: Multi-Account:

   aws/manegementAndGovernance/awsOrganizations
   aws/manegementAndGovernance/awsServiceCatalog
   aws/manegementAndGovernance/awsControlTower

.. toctree::
   :maxdepth: 1
   :caption: Monitoring:

   aws/manegementAndGovernance/amazonCloudWatch
   aws/manegementAndGovernance/awsCloudTrail
   aws/manegementAndGovernance/awsConfig
   aws/manegementAndGovernance/awsHealth

.. toctree::
   :maxdepth: 1
   :caption: Managemant:

   aws/manegementAndGovernance/awsSystemsManager
   aws/manegementAndGovernance/awsLicenseManager

.. toctree::
   :maxdepth: 1
   :caption: Deployment:

   aws/manegementAndGovernance/awsCloudFormation

Security,Identity & Compliance
------------------------------
.. toctree::
   :maxdepth: 1
   :caption: Identity and Access Management:

   aws/securityIdentityAndCompliance/awsIam

.. toctree::
   :maxdepth: 1
   :caption: Authentication and Authorization:

   aws/securityIdentityAndCompliance/awsSts
   aws/securityIdentityAndCompliance/amazonCognito
   aws/securityIdentityAndCompliance/awsDirectoryService

.. toctree::
   :maxdepth: 1
   :caption: Encryption:

   aws/securityIdentityAndCompliance/awsKms
   aws/securityIdentityAndCompliance/awsSecretsManager
   aws/securityIdentityAndCompliance/awsCertificateManager

.. toctree::
   :maxdepth: 1
   :caption: Protection:

   aws/securityIdentityAndCompliance/amazonDetective
   aws/securityIdentityAndCompliance/amazonGuardDuty
   aws/securityIdentityAndCompliance/amazonMacie
   aws/securityIdentityAndCompliance/amazonInspector
   aws/securityIdentityAndCompliance/awsSecurityHub

Storage
------------------------------
.. toctree::
   :maxdepth: 1
   :caption: Object Storage:

   aws/storage/amazonS3
   
SRE
=================================