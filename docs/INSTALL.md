[//]: <> (Copyright 2015, Jesper Derehag <jesper.derehag@ericsson.com> for Ericsson AB)
[//]: <> (All rights reserved.)

[//]: <> (Redistribution and use in source and binary forms, with or without modification,)
[//]: <> (are permitted provided that the following conditions are met:)

[//]: <> (1. Redistributions of source code must retain the above copyright notice, this list of conditions)
[//]: <> (and the following disclaimer.)

[//]: <> (2. Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the)
[//]: <> (following disclaimer in the documentation and/or other materials provided with the distribution.)

[//]: <> (THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED)
[//]: <> (WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A)
[//]: <> (PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE FOR ANY)
[//]: <> (DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES INCLUDING, BUT NOT LIMITED TO,)
[//]: <> (PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER)
[//]: <> (CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT, INCLUDING NEGLIGENCE)
[//]: <> (OR OTHERWISE, ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF)
[//]: <> (SUCH DAMAGE.)

#Install
[TOC]  


## General installation
### requirements
####python requirements
   1. [>=Python 2.7.10](https://www.python.org/downloads/)  
   2. [pip](https://www.python.org/downloads/)  
      Pip should be installed together with Python as of 2.7.9
   3. Install additional python requirements by doing:

        $>pip install -r pip-requirements.py  


### project configuration
1. Create **project.config**  
   Copy ROOT/project.config.template -> ROOT/project.config  
   Follow the comments in the file to make sure everything is configured properly.

2. Configure **MAINTAINERS**  
   This file contains a list of all subsystems (a list of inclusion/exclusion pattern rules).

## Creating a database and doing analysis of repo
Creating a database is done through the script **ROOT/analyze.py**  
You can either cumulatively update, or analyze everything as defined in project.config.
If you are analyzing a git repo, you should also define the repo_root in the project.config file (under 
db_update section). 

## Running the www frontend
The www frontend is based on the [django web framework](https://www.djangoproject.com/)
You first need to configure django to be able to run the development server, you do that by:

1. Copy **ROOT/www/MetricsViewer/MetricsViewer/local_settings.py.example** -> **ROOT/www/MetricsViewer/MetricsViewer/local_settings.py**  
   Follow the comments inside that file on how to properly configure it.  
2. Start the server  
   It will use whatever database as defined in **project.config::[MetricsViewer][engine_url]**

        $>python ROOT/www/MetricsViewer/manage.py runserver  

   By default, the development server will start to listen on http://localhost:8000

For more information:  
1. [Usability](/docs/frontends/django_usability.md)  
2. [Implementation details](/docs/frontends/django_implementation.md)
