## Scope

This document is not about the process of reporting a vulnerability itself or responsible disclosure. This document describe guidelines about what to do before reporting a vulnerability to an open source project and what kind of information the open source project would like to receive.

Each project could have their own guidelines, so please, check for specific project guidelines before reporting a vulnerability.

## Guidelines

* Include the name of the products and versions affected and why.
* Explicitly state which versions do you think are not affected and why.
* Include a brief description of the vulnerability.
* Explain where did you get the software and how you installed and configured it.
* Include step by step instructions about how to reproduce the vulnerability.
* If you are capable of doing it, include a reproducer. A reproducer is a piece of code that demonstrates the vulnerability.
* As we are talking about open source, indicate which lines of the code are responsible for the vulnerability.
* In the same sense than the reproducer, if you are able, include a potential patch for the vulnerability.
* Include information about how to contact you (e.g. email).
* Be ready to answer the maintainer's questions.
* State the vulnerability in a way that the risk for the user or organizatoin is clear. Avoid justifying that it is a security vulnerability because it is a security vulnerability (an SQL injection is not dangerous because it is a security vulnerability; it is dangerous because it allows an unauthorized user to see and change confidential data).
    * If it does not represent a risk or affects security pillars (confidentiality, integrity, availability, authenticity, accountability, non-repudiation or reliability), it might not be a security issue, but just a functionality issue.
* Include screenshots, crash reports, demo videos, or any other helpful material.
    * A crash report or a video is not a substitute for a good explanation, a reproducer or even a patch. Never send only a crash report or video.
* Be sure that the vulnerability you see is not a problem in your own configuration.
* If you know there is a vulnerability because the version of the package, be careful.
    * Just looking at the version number of a package will not tell us if they are vulnerable or not. For example, PHP 5.3 may be vulnerable or not to CVE-2014-3670, depending on where you have downloaded it from due to backporting (https://access.redhat.com/security/updates/backporting).
    * You can verify this by trying to exploit the vulnerability. If you cannot exploit it, please, think twice before reporting it.
* Use search engines in order to try to identify if other people have already identified what you have found, and it is a known functionality or issue.
* If you found the vulnerability by executing a tool, try to verify manually the existence of the vulnerability. Security tools give false positives sometimes.
* After you have researched the potential vulnerability, and gathered valuable information about it, it's time to report it.
    * Please, always look for information about how to report security vulnerabilities for each project.
    * Reporting it in a public list or repository (e.g. Github issue) is not a good idea since you may be putting at risk information assets.