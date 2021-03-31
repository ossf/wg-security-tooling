# Web Application Definition 1.0.0
## Introduction
The Open Source Security Foundation is focused on making open source projects more secure.
Dynamic Application Security Testing (DAST) tools are very effective at finding certains types of vulnerabilities but are difficult to run at scale against open source projects as they require a running system to test against. There are currently no standard ways to define how to run a project.

The proposed Web Application Definition is a file that can be included in open source projects and which defines how the application can be run in a test environment. While the initial motivation for this is to help integration with DAST tools it could equally well be useful for any testing tool that requires a running instance of an application.

The initial definition is deliberately minimalist - it only defines how an application can be started and stopped in a very limited but cross platform way.

The proposed path and filename is:
`.config/webapp.yml`

An example of the file is:
```yaml
---
webapp: 1.0.0
apps:
- id: app1
  name: Application 1
  description: An app that provides a docker container
  control:
    type: docker
    registry: https://hub.docker.com/  # This is the default
    image: example/image
    port: 8080                         # The default port is 80
    path: /example                     # The default path is /
- id: app2
  name: Another application
  description: An app that provides a public FQN
  control:
    type: public
    url: https://www.example.com/example
```

The file can define multiple applications in order to cope with mono-repos which contain more than one application.
To start with the definition only supports applications with publicly available URLs and applications which provide public [docker](https://www.docker.com/) images. Support for other options may be provided based on feedback received, but it is important that security applications which support this definition should not need to know any other contextual information other than that provided in the file.

The publicly available URL option is intended for websites that are always available on a given public address. 
The docker option allows applications to be tested in a safer environment. The images should provide a running instance of the application set up and ready to use, including any test data required. At this stage it is recommended that the applications are run without any authentication so that tools can test them without additional configuration.

Based on conversations with industry experts and security tool developers (both open and closed source) it appears that an application definition could be very useful for defining a wide range of information that is very useful for security tools.
However the most important thing is to ensure that this definition is as widely supported by developers as possible. Adding a large amount of security related information will make the format appear much more complex and arduous to implement, even if the majority of it is optional.

## Semi Formal Definition
For this phase the Web Application Definition must be written in [YAML](https://en.wikipedia.org/wiki/YAML).

Every definition must include the version of the Web Application Definition that this definition is based on:
```yaml
webapp: 1.0.0
```

The `apps` section contains a list of one or more applications.

Each application must have:

* An `id` field which uniquely identifies the application in this file. It must only contain alphanumeric characters but no whitespace.
* A `name` field which any tools that consume this file should use for reporting purposes
* A `control` section described below.

An application may also include a longer description field which tools can also use if required.

* The `control` section must include a `type` field which must be one of:
  * `docker`
  * `public`

The `public` type value means that the application is always available on a publicly accessible URL. This URL must be given in the `url` field.
The `docker` type value means that the application can be run using a publicly available docker image. The image name must be specified in the `image` field. The registry to be used may be specified in the `registry` field, if it is not specified then `https://hub.docker.com/` will be used. The `port` field should be used to specify the port the application is listening on, but may be defaulted to `80`. The `path` field may be used if the application does not use the default path of `/`. 

## Plan
### Phase 1 - minimal PoC
* Define a minimal specification - as per this document
* Implement a simple tool for validating that a file is correct - for example by checking the file format, starting the application and accessing the specified path
* Implementing a working PoC using an open source DAST Tool
### Phase 2 - initial adoption
* Publicise the format via blog posts and social media posts
* Encourage open source hosting companies to adopt it as a standard
* Encourage security tool authors to implement support for it in their tools
* Encourage developers to define the file for their projects -  if necessary by submitting pull requests
* Solicit feedback to ensure that the definition is as widely adopted as possible
### Phase 3 - increase adoption
* Add support for any platform independent ways to run applications that will significantly increase adoption
* Add support for API definitions such as SOAP and OpenAPI

Future phases could allow applications to add more information which help security tools understand how they work, for example:

* Details of any anti-CSRF tokens are used
* How sessions are handling
* Authentication details

While this sort of information would be extremely useful to security tools it is proposed that support for them is put off until the format has gained traction and has been adopted by a significant number of open source projects.
Security information, especially authentication details, can be extremely complex and even just exposing this configuration could reduce adoption.
Instead developers are encouraged to ensure that their projects can be run in test environments with no authentication.
