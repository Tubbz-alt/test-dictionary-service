Dummy Dictionary service for use in development of Concept Dictionary Manager at https://github.com/CDCgov/concept-dictionary-manager

# Running locally

To run this service locally, be sure to have the latest version of Go installed. Downloads are available [here](https://golang.org/dl/).

You will also need to install a local instance of [postgres](https://www.postgresql.org/). Running locally, the default user and database are `testservice` and `test_service` respectively, and need to be created in your postgres instance before running this service.

Then, clone this repository to your local system, or run `go get github.com/CDCgov/test-dictionary-service` to download the source to your `$GOPATH`.

Navigate to the directory of this repository, and run `go run server.go` to start the service. Alternatively, you can run `go build` to build a binary version of `server.go` and then run `./server` to start the service.

Once this service and the concept dictionary manager found [here](https://github.com/CDCgov/concept-dictionary-manager) are both running on your local system, you will be able to make http requests to the paths mentioned in the concept dictionary manager's readme to search the sample code set contained within this dummy service.

# Running in an OpenShift Cluster

To run this service in an OpenShift cluster, use a go source-to-image builder (see [here](https://github.com/openshift-s2i/s2i-go) for an example).

You will also need to have a postgres pod running within the project that you'd like to deploy this service in. Make note of the postgres pod's IP address, port, username, password, and database that you want the sample codes stored in.

Point the source-to-image builder at this repository's URL on github.

Edit the deployment of this service to include the following environment variables:

`POSTGRES_PORT_5432_TCP_ADDR` - the IP address of the postgres pod

`POSTGRES_PORT_5432_TCP_PORT` - the port that the postgres pod is serving on

`POSTGRES_USER` - postgres username

`POSTGRES_PASSWORD` - postgres password

`POSTGRES_DATABASE` - postgres database

The first two environment variables are named as such in the case that this service would be deployed within a standard Docker environment, assuming the postgres container was serving on port 5432.

Once OpenShift redeploys this build, it should connect to postgres and the service will be running.

##Public Domain: 
This project constitutes a work of the United States Government and is not subject to domestic copyright protection under 17 USC § 105. This project is in the public domain within the United States, and copyright and related rights in 
the work worldwide are waived through the [CC0 1.0 Universal public domain dedication](https://creativecommons.org/publicdomain/zero/1.0/). All contributions 
to this project will be released under the CC0 dedication. By submitting a pull request you are agreeing 
to comply with this waiver of copyright interest. 

##License
The project utilizes code licensed under the terms of the Apache Software License and therefore is licensed under ASL v2 or later.

This program is free software: you can redistribute it and/or modify it under the terms of the Apache Software License version 2, or (at your option) any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the Apache Software License for more details.

You should have received a copy of the Apache Software License along with this program. If not, see http://www.apache.org/licenses/LICENSE-2.0.html

##Privacy
This project contains only non-sensitive, publicly available data and information. All material and community participation is covered by the Surveillance Platform [Disclaimer](https://github.com/CDCgov/template/blob/master/DISCLAIMER.md) and [Code of Conduct](https://github.com/CDCgov/template/blob/master/code-of-conduct.md). For more information about CDC's privacy policy, please visit [http://www.cdc.gov/privacy.html](http://www.cdc.gov/privacy.html).

##Contributing
Anyone is encouraged to contribute to the project by [forking](https://help.github.com/articles/fork-a-repo) and submitting a pull request. (If you are new to GitHub, you might start with a [basic tutorial](https://help.github.com/articles/set-up-git).) 
By contributing to this project, you grant a world-wide, royalty-free, perpetual, irrevocable, non-exclusive, transferable license to all users under the terms of the [Apache Software License v2](http://www.apache.org/licenses/LICENSE-2.0.html) or later.

All comments, messages, pull requests, and other submissions received through CDC including this GitHub page are subject to the [Presidential Records Act](http://www.archives.gov/about/laws/presidential-records.html) and may be archived. Learn more at [http://www.cdc.gov/other/privacy.html](http://www.cdc.gov/other/privacy.html).

##Records
This project is not a source of government records, but is a copy to increase collaboration and collaborative potential. All government records will be published through the [CDC web site](http://www.cdc.gov.)

##Notices
Please refer to [CDC's Template Repository](https://github.com/CDCgov/template) for more information about [contributing to this repository](https://github.com/CDCgov/template/blob/master/CONTRIBUTING.md), [public domain notices and disclaimers](https://github.com/CDCgov/template/blob/master/DISCLAIMER.md), and [code of conduct](https://github.com/CDCgov/template/blob/master/code-of-conduct.md).

##Hat-tips
Thanks to [18F](https://18f.gsa.gov/)'s [open source policy](https://github.com/18F/open-source-policy) and [code of conduct](https://github.com/CDCgov/code-of-conduct/blob/master/code-of-conduct.md) that were very useful in setting up this GitHub organization. Thanks to CDC's [Informatics Innovation Unit](https://www.phiresearchlab.org/index.php/code-of-conduct/) that was helpful in modeling the code of conduct.
