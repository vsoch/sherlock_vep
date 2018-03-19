# sherlock_vep

## Instructions for building

To build the container locally:

```
sudo singularity build ensembl-vep Singularity
```

To build the container with a cloud builder, make sure you have a Google Cloud
project, along with your [credentials file](https://cloud.google.com/video-intelligence/docs/common/auth#authenticating_with_application_default_credentials). The below commands
use the default builder, so you don't need to think about configuration.

```
# Setup export project and credentials for Google Cloud
export SREGISTRY_GOOGLE_PROJECT=vanessasaur
export GOOGLE_APPLICATION_CREDENTIALS=/path/to/credentials.json
```
```
# 1. Install sregistry
$ pip install sregistry[google-compute]

# 2. Preview the build configuration, with a particular recipe (json output to console)
$ sregistry build --preview https://github.com/eilon-s/sherlock_vep

# 3. Deploy the builder
$ sregistry build https://github.com/eilon-s/sherlock_vep
```

The message will give you information about the builder, and a web address.
You should wait a minute or two to go here, as the server needs to be set up.

```
sregistry build https://github.com/eilon-s/sherlock_vep
[client|google-compute] [database|sqlite:////home/vanessa/.singularity/sregistry.db]
[bucket][sregistry-vanessa]
Found config google/compute/ubuntu/securebuild-2.4.3 in library!
INSTANCE anxious-fudge-5230
eilon-s-sherlock_vep-builder https://singularityhub.github.io/builders_cloud/google/compute/ubuntu/securebuild-2.4.3.json
Robot Logger: http://35.230.66.133
Allow a few minutes for web server install, beepboop!
```

While you are waiting, you can check instances

```
$ sregistry build instances
[google-compute] Found 9 instances
1  anxious-fudge-5230	RUNNING
2  instance-1	RUNNING
...
```
to verify it is running. When the container is sent to storage, you will be able
to see it:

```
$ sregistry search
```

and then pull the container with the URI that you want.

```
$ sregistry pull <container>
```

## Using container

And to run the software:

```
./ensembl-vep 
#----------------------------------#
# ENSEMBL VARIANT EFFECT PREDICTOR #
#----------------------------------#

Versions:
  ensembl              : 91.18ee742
  ensembl-funcgen      : 91.4681d69
  ensembl-io           : 91.923d668
  ensembl-variation    : 91.c78d8b4
  ensembl-vep          : 91.3

Help: dev@ensembl.org , helpdesk@ensembl.org
Twitter: @ensembl , @EnsemblWill

http://www.ensembl.org/info/docs/tools/vep/script/index.html

Usage:
./vep [--cache|--offline|--database] [arguments]

Basic options
=============

--help                 Display this message and quit

-i | --input_file      Input file
-o | --output_file     Output file
--force_overwrite      Force overwriting of output file
--species [species]    Species to use [default: "human"]
                       
--everything           Shortcut switch to turn on commonly used options. See web
                       documentation for details [default: off]                       
--fork [num_forks]     Use forking to improve script runtime

For full option documentation see:
http://www.ensembl.org/info/docs/tools/vep/script/vep_options.html

```

If you have questions, please open an [issue](https://github.com/eilon-s/sherlock_vep/issues).
