# radon-tools-chart

Helm chart for https://github.com/fmidev/radon-tools

# Contents

Chart contains configuration for two openshift jobs:
* tables-job: handles radon database metadata
* load-job: loads grib/netcdf/geotiff metadata to radon

# Preconditions

Necessary passwords and accounts need to be created.

## tables-job

radon-credentials are given with secret _radon-credentials_ (configurable), secret should contain following fields:

* RADON_HOSTNAME
* RADON_PORT (optional, default: 5432)
* RADON_DATABASENAME (optional default: radon)
* RADON_RADON_ADMIN_PASSWORD

s3-credentials are given with secret _s3-credentials_ (configurable), secret shouldcontain following fields
  * S3_ACCESS_KEY_ID
  * S3_SECRET_ACCESS_KEY

If no credentials are needed for s3 access, leave name field empty.

## load-job

radon-credentials are given with secret _radon-credentials_ (configurable), secret should contain following fields:

* RADON_HOSTNAME
* RADON_PORT (optional, default: 5432)
* RADON_DATABASENAME (optional default: radon)
* RADON_WETODB_PASSWORD

s3-credentials are given with secret _s3-credentials_ (configurable), secret shouldcontain following fields
  * S3_ACCESS_KEY_ID
  * S3_SECRET_ACCESS_KEY

If no credentials are needed for s3 access, leave name field empty.

# Usage

helm create radon-tools .

Nearly all of the options of the tools are exposed to job. See the template for more details.
