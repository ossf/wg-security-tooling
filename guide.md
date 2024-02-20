# Guide to Security Tools

This is a brief guide for software developers on security tools,
including definitions of key security tool types.
We intend to eventually develop specific guidance for common circumstances
but they will all refer back to this quick guide.

By security tools, we mean tools that you can use,
after creating a design or code, to verify that they are reasonably secure.
"Verification" can be defined as determining whether or not something
complies with its requirements. Testing is one verification approach,
but verification is more than testing. We want to verify (to some
reasonable level) that our software is secure, just like we want
to verify that our software does other things it is supposed to do.

## Overview

### No tool is perfect

No tool is perfect.
All have false positives (report "problems" that
are not problems), false negatives (fail to report some problems you might
expect them to report), or both (and it's almost always both).
Therefore:

* You must *think* about tool reports about potential vulnerabilities,
  not just blindly follow tool recommendations.
  In many cases, it is best to fix something based on the report;
  people are often wrong when they say something “can’t” happen,
  and the software or its environment may change in the future (so
  fixing it will future-proof the software).
* Over time you should try to maximally add many tools, including different
  kinds of tools.
* Tools must be *part* of developing secure software, not the only thing.
  For example, all software developers should learn how to
  develop secure software in the first place.
  If you haven't, consider taking the free
  [Secure Software Development Fundamentals Courses](https://openssf.org/edx-courses/) provided by the OpenSSF.

### Two main tool categories

There are two main technical categories of verification tools:

* Static analysis is any approach for verifying software (including finding defects) without executing software. This includes tools that examine source code looking for vulnerabilities (e.g., source code vulnerability scanning tools). It also includes humans reading code, looking for problems.
* Dynamic analysis is any approach for verifying software (including finding defects) by executing software on specific inputs and checking the results. Traditional testing is a kind of dynamic analysis. Fuzz testing, where you send many random inputs to a program to see if it does something it should not, is also an example of dynamic analysis.

Some people also use a category called hybrid analysis for approaches that combine both, while others will include hybrid approaches in the dynamic analysis category. For our purposes we'll consider hybrid analysis part of static analysis.

### How to apply tools

If you are adding a tool to an existing project, you may want to configure tools to greatly limit what they report, and focus just on the vulnerabilities you are most concerned about. This gives you time to learn how to tune the tool and understand its results. Then, once those results are addressed, increase the sensitivity of your tools or add more tools to detect more issues. There is no point in trying to detect more issues than you can deal with.

If you are adding tools to a newly-started project, you are often better off configuring your tools to be very sensitive. In a new project, you will not be overwhelmed by the reports, and you will immediately get feedback on the issues your tools can detect.

Where do you add these tools? In short, maximally add these tools to at least your continuous integration (CI) pipeline. That way, incremental changes will be repeatedly analyzed and security issues will be reported early.

Some tools are open source software (OSS), while others are proprietary. Some of the proprietary tools are expensive, but if you are using them to develop OSS, many tools and/or services are free to use or are available at a substantial discount.

## Types of Tools

This section will cover some of the most common application security tools including linters, SAST, SCA, DAST, Fuzzers, Hard Coded Secrets Detectors, and SBOM generators. 

### Quality scanners (linters)

Quality scanners, also called "linters", examine source code,
byte code, or machine code to look for generic “quality” problems.
For example, they may look for misleading indentation,
combinations of constructs that usually indicate a defect,
or overly-long methods that may be hard to understand later.
There are a large variety of these, including
style checkers and external type checkers.

For our purposes we will include compiler warning flags in this category.

These tools often don’t focus on security, but using them can still help improve security:

1. Some defects they find are security vulnerabilities.
2. There are reports that clean code is easier for other tools and humans to understand... so fixing the reported problems can make other approaches more effective.

### Security Code Scanners (Static Application Security Testing (SAST) Tools)

Some tools analyze code specifically looking for vulnerabilities. They go by a variety of names, such as security code scanners, Static Application Security Testing (SAST) tools, security source code scanners (if they examine source code), binary code scanners (if they only examine executables), or sometimes just static code analyzers. Some people use the term SAST only when the tool analyzes source code.

The idea behind these tools is that many vulnerabilities have specific patterns. A tool designed to look for those patterns can report similar kinds of vulnerabilities.

The patterns are generally heuristic, and different tools generally look for different patterns. So one tool can find some vulnerabilities, but don’t make the mistake of thinking that any one of these tools finds all vulnerabilities. In addition, each tool will only look for patterns relevant to a particular set of languages/environments. That means these tools are only good for languages/environments they are designed to support, and in addition, a tool might be better at one language than another. Even given multiple tools designed to support a given language, different tools will often find vulnerabilities that others miss.

### Secret scanning tools

Secret scanning tools look for secrets (passwords, stored keys, etc.), typically in a repository's
code and/or configuration. These are typically static analysis tools. These tools typlically detect the secrets in code by grepping (simple text based searching) or regex searches. 

Some secret scanning is automatically done on projects hosted on
[GitHub](https://docs.github.com/en/code-security/secret-security/about-secret-scanning) and
[GitLab](https://docs.gitlab.com/ee/user/application_security/secret_detection/).


### Software Bill Of Materials (SBOM) tools

A Software Bill Of Materials (SBOM) is an artifact that may accompany the release of a software package. The SBOM includes an inventory of the software components and dependencies that are included in a parent software. This may include both open source and proprietary components and dependencies. It may also include additional information such as more in-depth package information, file information, licensing, authors, contributors, security checksums or references, copyright information, as well as their hierarchical relationships.

Machine-readable formats for SBOMs grant the opportunity for this information to be shared throughout the software supply chain; thus increasing transparency of and confidence in the final delivered software artifact. The machine readable formats for SBOMs currently include [SPDX](https://spdx.github.io/spdx-spec/), [CycloneDX](https://cyclonedx.org/), and SWID.

SBOMs are quickly becoming a necessity for software products and services to include in their software delivery practices. SBOMs are being recommended by several security frameworks, organizations, and security requirements such as the [White House Executive Order 14028](https://www.whitehouse.gov/briefing-room/presidential-actions/2021/05/12/executive-order-on-improving-the-nations-cybersecurity/), [NIST](https://www.nist.gov/itl/executive-order-14028-improving-nations-cybersecurity/software-security-supply-chains-software-1), [NTIA](https://www.ntia.gov/SBOM),the [OpenSSF Mobilization Plan](https://openssf.org/oss-security-mobilization-plan/), and [SLSA](https://slsa.dev/). 

For tooling, there are different SBOM tool classifications as outlined by the [NTIA](https://www.ntia.gov/files/ntia/publications/ntia_sbom_tooling_taxonomy-2021mar30.pdf). There are tools that produce, consume, and transform SBOMs. The taxonomy outlines specific types of activities in each category thus allowing for the comparison of SBOM tool coverage.  

Tools that produce SBOMs may build, analyze, and/or edit. 
Tools that consume SBOMs may view, diff, and/or import.
Tools that transform SBOMs may translate, merge, and/or tool support.

Tools may have a combination of categories and action types to provide multiple SBOM functions. 

### Software Component Analysis (SCA)/Dependency Analysis tools

Software component analysis (SCA) tools, also called
dependency analysis or origin analysis tools,
determine the reused components used by code (source code or executable).
To be security-relevant, these tools also determine which of those
reused components have publicly-known vulnerabilities (CVEs).

So, all an SCA tool has to do, in theory, is figure out what components (and their versions) are present, look up each one in one or more databases, and report on matches. Even detecting the components is not always easy; sometimes reused components are not obvious (e.g., because they were copy and pasted in, instead of being properly handled using a package manager). Even more fundamentally, however, databases are constantly updated as new vulnerabilities are found. That means that reused software that had no known vulnerabilities earlier might now have a known vulnerability. Even if the vulnerability was publicly known earlier, that fact might not have been recorded in earlier versions of the database(s) used by the tool. So these tools must be periodically rerun, or have the comparisons rerun, so that you become aware of newly-found vulnerabilities.

You should avoid some bad behavior to make these tools more useful. Some developers copy reused code from other packages into their application, instead of using a package manager to automate identifying and updating reused packages. Even worse, developers sometimes modify these copies and/or check in these copies (creating a fork). Some SCA tools can actually examine code line-by-line, identify such likely copies, and connect them back to their sources (to help identify vulnerabilities). But such SCA tools are more complex, often expensive to buy and use, and trying to update that software is often quite difficult because everything is being done manually. In addition, such SCA tools must necessarily use heuristics to detect such situations, which may miss such components anyway.

It is far better to apply some good practices. First, when reusing software, use a package manager to manage it, one that records the specific version numbers in a standard format that you can record in your version control system. By using a standard format, you can use far simpler SCA tools, and the data will be more accurate. By using a package manager you can trivially cause a software update and check that the new set of components works.

Like all tools, SCAs are prone to false positives. In particular, a component may have a vulnerability, but only when certain methods are used or only in certain configurations. If you don’t use the component in a way that the vulnerability can be exploited, then of course you don’t need to update the component. But this is a little misleading. It is often hard to be certain that you don’t need to do the update. In addition, if you have a proper process where you can easily update components ― and you need to ― then it often takes more time to determine (for sure) that the vulnerability is not exploitable than to just do the update. What’s more, time spent to figure this out may give an attacker time to exploit it if it is a real vulnerability. So it is often better to just update, even if it is not certain to be exploitable.

There are lots of SCAs available. If you use GitHub or GitLab, they provide some basic SCA reporting of known vulnerabilities in many components for free (assuming that you use a standard package management format they can process). Linux Foundation projects can use [LFX Security](https://lfx.linuxfoundation.org/tools/security/) which provides this service. There are a variety of suppliers that provide or sell such tools. This includes OWASP Dependency Check (which is OSS), Sonatype’s Nexus products, Synopsys’ Black Duck, Ion Channel Solutions, and Snyk. Some package managers include this capability or have a plug-in for it (e.g. Ruby’s bundler has bundle-audit). This is definitely not a complete list, and no doubt you will want to compare the options.


### Dependency Updating & Hygiene Tools

SCA tools help identify the known vulnerable OSS components used in your project, but other tools exist to help ensure that OSS hygiene becomes an automated process. As required in the OpenSSF Secure Supply Chain Consumption Framework (S2C2F) maturity level 2, tools such as Dependabot or Renovate bot will auto-submit Pull Requests (PRs) to update your known-vulnerable dependencies. All a developer has to do is choose to accept the PR to keep their dependencies up-to-date.

There are other tools that can help prevent developers from introducing a new dependency with a known vulnerability. This can be accomplished by tools that show vulnerabilities as comments in PRs, such as Dependency Review in GitHub. Assuming the repo has two-person code review enabled, this helps the reviewer realize that the submitter is introducing a dependency with known vulnerabilities, enabling the team to address the issue before the code is merged. 

Each of these tools helps your developers improve their Mean Time To Remediate (MTTR) to update known vulnerable dependencies. If your team embraces tools with these capabilities, then there's a good chance that you can update faster than the adversaries can craft exploits. 

### Traditional testing

The best-known dynamic analysis approach is traditional testing. You select specific inputs to send to a program, and check to see if the result is correct. You can test specific parts of a program, such as a method or function (this is called unit testing). You can also send sequences of inputs to the system integrated as a whole (integration testing). Most people combine unit and integration testing. Unit testing is fast and it can be easy to test many special cases, but unit testing often misses whole-system problems that integration testing is much more likely to detect. Since computers are much faster than they were decades ago, it is often best to focus on integration testing over unit testing, but both approaches have their place. The testing literature describes other kinds of testing, but for our purposes, these two approaches are enough to understand the issues.

If your software needs to work correctly, it is critically important that you have a good test suite of automated tests and apply that test suite in your continuous integration pipeline. By good we mean “relatively likely to detect serious problems in the software”. While this does not guarantee there are no errors, a good test suite greatly increases the probability of detection, and is especially important for detecting problems when you upgrade a reused component.

If you deliver software, and a defect is later found and fixed, for each fix you should think about adding another test for that situation. Often, defects that escape to the field indicate a kind of subtle mistake that might reoccur in a future version of the system. In that case, add test(s) so if that problem recurs, will be detected before releasing another version.

#### Traditional testing for security

From a security perspective, it is important to include tests for security requirements. In particular, test both “what should happen” and “what should not happen”. Often people forget to test what should not happen (aka negative testing). For example, where it applies, you should have a test to check “Can I read/write without being authorized to do so?” (the answer should be “no”) and “Can I access the system with an invalid certificate or no certificate at all?” (again, that should fail). It is very common for programs’ security to fail because they don’t properly check for authentication (2017 OWASP Top 10 #2) or authorization (2017 OWASP Top 10 #5), so make sure you have tests for that!

One approach to developing software is called test-driven development (TDD). To over-summarize, in TDD the tests for a new capability are written before the software to implement the capability. This has some advantages, in particular, it encourages writing useful tests that actually check what they are supposed to check, and it also encourages developing testable software. One potential problem with TDD is that many TDD practitioners fail to write negative tests. Some TDD guidance even argues that you should only write tests for the new capability and nothing else. This is terrible guidance, because sometimes some things should simply never be allowed to happen, and you still need to test for them. You can definitely write secure software using TDD, but you must include negative tests (tests for what the software must not do) if you apply TDD.

#### Test Coverage

You can always write another test; how do you know when you have written enough tests? It takes time to create and maintain tests, and tests should only be added if they add value. This turns out to be a hard question, and much depends on how critical your software is.

Two simple measurements that can help you answer this question are statement coverage and branch coverage:

Statement coverage is the percent of program statements that have been run by at least one test.
Branch coverage is the percentage of branches that have been taken by at least one test. In an if-then-else construct, the then part is one branch and the else part is the other branch. In a loop, the run the body part is one branch and do not run the body is the other branch. In a switch (case) statement, each possibility is a branch.

Statement coverage and branch coverage combine dynamic analysis (test results) with static analysis (information about the code), so it is sometimes considered a hybrid approach. But no matter what you call it, these measurements do provide some information about how well a program is tested.

One potential problem with statement coverage and branch coverage is that some statements and branches may be unreachable for a variety of reasons. If a statement cannot be reached, you may want to insert the equivalent of “assert(false)” to inform tools and humans that this statement should never be reached. What you really want to know is the percent of possible branches and statements that were covered by tests.

As a rule of thumb, we believe that an automated test suite with less than 90% statement coverage or less than 80% branch coverage (over all automated tests) is a poor test suite. But this is merely a rule of thumb. Some experts think that larger numbers should be expected (some argue anything less than 100% of possible statements and branches is unacceptable). All other things being equal, larger numbers are good, but it is often much costlier to get those last few percent, and whether or not it is worth it depends on how important the software is. In many cases some statements or branches cannot be executed, and there may not be a way to indicate that to the measurement tools.

These test coverage measures warn you about statements and branches that are not being tested, and that information can be really valuable. From a security standpoint, coverage measures warn you about statements or branches that are not being run in tests, which suggests that either there are some important tests missing or the software is not working properly. Don’t just add a test; make sure you understand why something is not being covered.

For example, we earlier mentioned a dangerous vulnerability in many versions of Apple’s operating systems, formally named CVE-2014-1266 and informally called the “goto fail; goto fail;” vulnerability. The problem was that due to a duplicated goto statement, some code vital for checking security certificates was skipped. A statement coverage measure would have trivially detected that this security-critical code was not being run by any test, and that should have been enough warning to look into the problem.

A big problem with statement and branch coverage measures is that they can warn you about some bad automated test suites, but a bad test suite could still get 100% perfect scores. For example, a test suite might exercise all the branches and statements but not check if any of the answers were correct. That test suite would have 100% branch and statement coverage, and would also be a bad test suite. In addition, while they can tell you about whether or not existing code was tested, they cannot detect missing code. For example, if there is a special case that needs special handling, but nothing checks for that special case, typically these coverage measures cannot detect that.

In short: these coverage measures can be useful for warning about some problems, but they do not warn about all testing problems.

### Fuzzers

A fuzzer is a tool that implements a dynamic analysis approach called
fuzz testing or fuzzing.
In fuzz testing, you generate a large number of inputs, run the
program, and see if the program behaves badly (e.g., crashes or
hangs). A key aspect of fuzzing is that it does not generally check
if the program produces the correct answer; it just checks that
certain reasonable behavior (like “does not crash”) occurs.

An important subclass of fuzzer is a coverage-guided fuzzer. These fuzzers instrument the software under test (SUT, the program being tested) so that the fuzzer gets information about what code is covered when each input is executed (including, in many cases, how often various parts of the code are executed). This information is then used to determine the next inputs to be generated.

If you manage an OSS project, you might consider participating in Google’s OSS-Fuzz project.

### Web Application Scanner

A web application scanner (WAS), also called a web application vulnerability scanner, essentially pretends it is a simulated user or web browser and tries to do many things to detect problems. Think of a WAS as a frenetic and malicious web browser user; the WAS will try to click on every button it finds, enter bizarre text into every text field it finds, and so on. In short, it attempts simulated attacks and odd behavior to try to detect problems. This means that WASs often build on fuzzers internally, but they are specifically designed to analyze web applications.

You will want to use a WAS in a test environment, not a true production environment, since it will intentionally attempt to cause problems. You may want to start with just running the WAS as-is, but you will soon want to create a bogus account and give the WAS the bogus account information. Otherwise, if your login system is built correctly, the WAS will only be able to test for vulnerabilities for someone without valid login credentials.

There are many of these tools. OSS tools include OWASP ZAP, W3AF, IronWASP, Skipfish, and Wapiti. Proprietary tools include IBM AppScan, HP WebInspect, and Burp Suite Pro. If you have no idea, you might check out OWASP ZAP at least; it is easy to use, and it can find many things. But tools change over time, and it is best to look at your options before picking one (or several).

The term Dynamic Application Security Testing, or DAST, is often seen in literature. However, the meaning of DAST has a lot of variation:

* For some, DAST is dynamic analysis for finding vulnerabilities in just web applications, making DAST the same as a web application scanner.
* For others, DAST includes web application scanners and fuzzers for programs other than web applications.

## Other tool types and categorizations

There are many other kinds of tools that can be used for security.
We have intentionally selected the most common kinds that are widely
applicable, so that you can get started.

There are many ways to categorize tools.
Here are a few such lists:

* [*Secure Software Development Fundamentals* course materials](https://github.com/ossf/secure-sw-dev-fundamentals) [Fundamentals]
* [State-of-the-Art Resources (SOAR)](https://www.ida.org/research-and-publications/publications/all/s/st/stateoftheart-resources-soar-for-software-vulnerability-detection-test-and-evaluation-2016)
  including its [appendix E](https://www.ida.org/-/media/feature/publications/s/st/stateoftheart-resources-soar-for-software-vulnerability-spreadsheet/p-8005-soar-app-e.ashx?la=en&hash=EA54CA1AD767003FB71FFAA2653978D3) with
  guidance on which tools are better for which objectives [SOAR]
* [NIST “Classes of tools & techniques” [NIST Tools]](http://samate.nist.gov/index.php/Tool_Survey.html)
* [OWASP's "Free for Open Source Application Security Tools" list](https://owasp.org/www-community/Free_for_Open_Source_Application_Security_Tools)
  [OWASP Tools]

## Bibliography

Much of this material is from the
*Secure Software Development Fundamentals* course materials [Fundamentals].

[CAS]
[CAS Static Analysis Tool Study -Methodology](https://samate.nist.gov/docs/CAS%202012%20Static%20Analysis%20Tool%20Study%20Methodology.pdf)

[Fundamentals]
[*Secure Software Development Fundamentals* course materials, 2020](https://github.com/ossf/secure-sw-dev-fundamentals)

[NIST Tools]
[“Classes of tools & techniques”](http://samate.nist.gov/index.php/Tool_Survey.html)

[OWASP Tools]
[OWASP's "Free for Open Source Application Security Tools" list](https://owasp.org/www-community/Free_for_Open_Source_Application_Security_Tools)

[SOAR]
[State-of-the-Art Resources (SOAR) for Software Vulnerability Detection, Test, and Evaluation 2016 (aka “Software SOAR”) by David A. Wheeler and Amy E. Henninger, Institute for Defense Analyses (Report P-8005), November 2016](https://www.ida.org/research-and-publications/publications/all/s/st/stateoftheart-resources-soar-for-software-vulnerability-detection-test-and-evaluation-2016),
including its
[Appendix E](https://www.ida.org/-/media/feature/publications/s/st/stateoftheart-resources-soar-for-software-vulnerability-spreadsheet/p-8005-soar-app-e.ashx?la=en&hash=EA54CA1AD767003FB71FFAA2653978D3)

[NISTIR 8397] NISTIR 8397 Guidelines on Minimum Standards for Developer Verification of Software, Oct 2021
https://doi.org/10.6028/NIST.IR.8397
