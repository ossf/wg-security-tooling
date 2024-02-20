
<h2>Fuzzing Collaboration Sync - Public Notes</h2>


<h3>NOTE FROM metzman@: This is the correct link from now on.</h3>


Call is on Zoom: 

[https://zoom-lfx.platform.linuxfoundation.org/meeting/93759514749?password=299ebf08-1f60-4a4a-a2cb-5d80b8d0eb7d](https://zoom-lfx.platform.linuxfoundation.org/meeting/93759514749?password=299ebf08-1f60-4a4a-a2cb-5d80b8d0eb7d) 

_Antitrust Policy Notice_: Linux Foundation meetings involve participation by industry competitors, and it is the intention of the Linux Foundation to conduct all of its activities in accordance with applicable antitrust and competition laws. It is therefore extremely important that attendees adhere to meeting agendas, and be aware of, and not participate in, any activities that are prohibited under applicable US state, federal or foreign antitrust and competition laws. Examples of types of actions that are prohibited at Linux Foundation meetings and in connection with Linux Foundation activities are described in the Linux Foundation Antitrust Policy available at [http://www.linuxfoundation.org/antitrust-policy](http://www.linuxfoundation.org/antitrust-policy). If you have questions about these matters, please contact your company counsel, or if you are a member of the Linux Foundation, feel free to contact Andrew Updegrove of the firm of Gesmer Updegrove LLP, which provides legal counsel to the Linux Foundation.

OpenSSF Code of Conduct: [https://openssf.org/community/code-of-conduct/](https://openssf.org/community/code-of-conduct/)

This Group is part of the OpenSSF Security Tools Working Group, see: [https://github.com/ossf/wg-security-tooling](https://github.com/ossf/wg-security-tooling)


<h3>December 5, 2023</h3>




* [decoder (limited availability, 30 mins max due to TZ)] Update on Nyx and AFL++
* Production deployment
* AFL++ prototype for dynamic code coverage selection will be upstreamed (help wanted with Nyx issue)
* [Chris Ball] Just FYI – I added a multicore fuzzing benchmark to AFL++, to contribute:
* cd aflplusplus/benchmark && python benchmark.py` on latest aflplusplus `stable` branch,, then open a PR with the new line that’s added to `benchmark/COMPARISON.md`. Would be especially useful to get entries for recent Intel desktop CPUs.
* [Chris Ball] Does anyone know of an integration with concolic solvers that allows a researcher to choose specific file:line:column constraints, or regex patterns, to prioritize solving?
* eqv: Would suggest using selective instrumentation / extra counters for trying to increase priority.

<h3>November 7, 2023</h3>




* [kcc] MTE in Pixel 8: [https://googleprojectzero.blogspot.com/2023/11/first-handset-with-mte-on-market.html](https://googleprojectzero.blogspot.com/2023/11/first-handset-with-mte-on-market.html) 

<h3>October 3, 2023</h3>




* Standard output
* Can add to libFuzzer, test that it continues to behave as we expect
* But have a test
* AFL doesn’t update it’s stats file properly
* Don’t have to worry about atomicity when we have new lines
* Maybe look at what centipede already does
* Use the names
* WebP
* kcc: anyone came up with a minimized puzzle
* Safe buffers
* Cornelius: hard research
* Can human guide the fuzzer to it? custom feedback based on hashmap
* FuzzBench addition
* Good to see what people come up with.
* How fast did you find first bug
* Farzon:
* Full browser fuzzer
* 3rd party fuzzer opening a bunch of tabs
* Cov report from this is a problem, few million lines missing on Windows, not on Linux
* some processes write to disk when shut down gracefully others don’t
* Special LLVM flags to get things working
* Farzon: HWASAN for windows
* Put in touch with Chrome people working on this.
* Scott:
* Research on other metrics better than coverage
* [Hyperloglog](https://en.wikipedia.org/wiki/HyperLogLog)
* Peng li:
* nanopb fuzzing

<h3>September 5, 2023</h3>




* [tyson] [fuzzdata](https://github.com/MozillaSecurity/fuzzdata) is being decommissioned [https://github.com/google/fuzzbench/issues/1868](https://github.com/google/fuzzbench/issues/1868)
* Switch to [corpus-replicator](https://github.com/MozillaSecurity/corpus-replicator) if possible and open issues or PRs for unsupported formats (media only)
* [metzman] [Fuzz target generation](https://google.github.io/oss-fuzz/research/llms/target_generation/)
* Extensively at Facebook with mixed results, a couple of good bugs a bunch of useless bugs, all fudge-style tech. Moving toward partial aid
* Consider binary stuff don’t need to worry about build systems
* [https://github.com/thepudds/fzgen](https://github.com/thepudds/fzgen) is an extant example, definitely more useful for a starting point, it generates go native fuzz tests based off of the args/return types of functions []
* [kcc] FYI, slides from Centipede talk: [Rich coverage signal and consequences for scaling (slides)](https://docs.google.com/presentation/d/16Zov-QmGZjGrEoTr6Qh2fyp-bvgOa4cmqxPrXw4fNeE/)
* [cjb] FYI: working on a benchmarking tool to be able to compare cloud instance fuzzing performance (per dollar) in [https://github.com/AFLplusplus/AFLplusplus/pull/1853](https://github.com/AFLplusplus/AFLplusplus/pull/1853).
* Addison: Can be useful to look at user time vs. system time to see how bottlenecked the fuzzers are.
* eqv: You can use multiple KVM machines once you have so many threads that your kernel is bottlenecked on syscalls etc.
* [cjb]: Saw that libafl_libfuzzer was released, congrats! Is it a pure drop-in replacement?
* Addison: yes, except for the output text format
* eqv: We could really use a machine-readable output format shared between fuzzers, like JSON Lines.
* Should we use an RFC process to specify that and then add it to libafl?
* metzman will start a Google doc and email it out to the meeting for input.

<h3>Aug 1, 2023</h3>




* No topics

<h3>June 6, 2023</h3>




* Centipede
* Hybrid fuzzing
* Symbolic fuzzing
* We don’t have good experiments in fuzzbench?
* New experiment

<h3>May 2, 2023</h3>




* [metzman]: Need beta testers for [ClusterFuzz/CIFuzz’s SARIF implementation](https://github.com/google/oss-fuzz/issues/10090)
* [docs](https://google.github.io/oss-fuzz/getting-started/continuous-integration/)
* [bookholt] thought of a useful question
* could eqv please re-explain how nyx-fuzz depends on a specific version of KVM and potentially why it's hard/expensive to maintain
* A custom KVM module is required only for intel PT - snapshots work with any kernel > 5.10 out of the box.

Attendees:



* 
* Andres Orbe

<h3>April 4, 2023</h3>


Attendees:



* David Wheeler (Linux Foundation)
* Jonathan Metzman (Google)
* Marc Heuse
* Alex Gaynor
* Chris Bookholt (Google)
* Brendon Tiszka (Google)
* Christoph Diehl (Microsoft)
* Edward Qiu
* Ben Edgar
* Laszlo

Re. snapshot fuzzing, Chris Bookholt wonders...



* Background: I’m in browser land. It’s expensive to instantiate the browser each time, booting/shutting down takes a long time, ~20-30 seconds/test case. One obvious way: startup once; also faster moving
* David A. Wheeler: AFL has had for years a mechanism where its starts a process, breakpoints at the end of startup, then repeatedly forks & runs. That means you only pay startup costs once. The trick is to set the breakpoint in the “right” place, & I’m sure others know more, but that seems reasonable: [https://github.com/mirrorer/afl/blob/master/docs/technical_details.txt#L446](https://github.com/mirrorer/afl/blob/master/docs/technical_details.txt#L446)
* What comes out of our [Chrome] browser isn’t a “real” browser to test a feature set. Moving to Centipede, experimenting with a build that’s more like a “real” browser.
* [https://superuser.com/questions/654565/how-to-run-google-chrome-in-a-single-process](https://superuser.com/questions/654565/how-to-run-google-chrome-in-a-single-process)
* To use libfuzzer afl, don’t have a “real” browser
* David A. Wheeler: The old documentation for AFL’s fork server is here, and fork serving sounds like exactly what you want:
* [https://github.com/mirrorer/afl/blob/master/docs/technical_details.txt](https://github.com/mirrorer/afl/blob/master/docs/technical_details.txt)
* [https://github.com/mirrorer/afl/blob/master/docs/technical_details.txt#L446](https://github.com/mirrorer/afl/blob/master/docs/technical_details.txt#L446)
*  [http://lcamtuf.blogspot.com/2014/10/fuzzing-binaries-without-execve.html](http://lcamtuf.blogspot.com/2014/10/fuzzing-binaries-without-execve.html)
* I presume AFL++ retained this capability from AFL but I haven’t checked.
* Anyone using large language models (LLMs) for fuzzing?
* Possibly could give an LLM an interface & see if it could write a fuzzing driver/harness. Seem plausible/promising.
* Of course, you could also just try pasting the function and ask it to tell you where the vulnerabilities are.
* Also, could ask it for an input to cover it – “I am in function X with input Y and I am missing coverage of line Z, what input should I provide to get there?”
* Chris Ball: LLMs are not great at this kind of computation in my experience, so perhaps a more effective idea is “write me some Z3 or Angr code that will return an input that reaches line Z”, perhaps with automated running and returning the output back to the LLM for improvement.
* What about for a “real sized” program?
* Marc Heuse had a brief try:
* write a libfuzzer harness for the following function prototype:
* int my_api_call(int a, int b, char*foo, char*bar);
* 
* Here's an example libFuzzer harness for the given function prototype:
* 
* c
* 
* #include <stddef.h>
* #include <stdint.h>
* 
* // Prototype of the function to be fuzzed
* int my_api_call(int a, int b, char* foo, char* bar);
* 
* // LibFuzzer entry point
* extern "C" int LLVMFuzzerTestOneInput(const uint8_t *data, size_t size) {
* // Ensure that the input data is large enough to hold two integers and two null-terminated strings
* if (size < sizeof(int) * 2 + 2) {
* return 0;
* }
* 
* // Extract the input values from the data buffer
* int a = *reinterpret_cast<const int*>(data);
* int b = *reinterpret_cast<const int*>(data + sizeof(int));
* const char* foo = reinterpret_cast<const char*>(data + sizeof(int) * 2);
* const char* bar = reinterpret_cast<const char*>(data + sizeof(int) * 2 + strlen(foo) + 1);
* 
* // Call the function to be fuzzed with the input values
* my_api_call(a, b, foo, bar);
* 
* Existing GPT has a limited number of tokens for this purpose.
* The upcoming GPT will handle many more 8000 tokens, and thus will be able to handle MUCH larger code & possibly far more useful.
* Some companies seem to be building LLMs which can answer questions about your codebase, not sure how they’re solving the context limits.
* One way to solve the context limit might be to continue training of the base model on your context.
* Generative Adversarial Training (GANs) may be better. Has a generator. Again, the problem is tokens / token dependencies. A big problem is attention - long-range dependencies.
* We found the current nyx-fuzz coverage reporting mechanism is best aligned with a single-process target. Are there any strategies to support multi-process targets, or is that an area for future work? 
* What is it that creates the nyx-fuzz dependency on a specific version of kvm? We had modest success running nyx-fuzz on an unmodified GCP Linux kernel over the summer of 2022. Did we get lucky? Is it feasible to update (and maintain) nyx-fuzz to support the most recent version of kvm, or is a custom kernel effectively required in perpetuity? 
* LLMs
* Ask LLM to write z3 to cover code you missed
* Has anyone tried out Centipede? Especially its new coverage mechanism? It uses the same APIs so easy to port over, nearly 0 cost. For that you get a supported fuzzing harness. He’s paid to maintain it, & ergonomic. Low effort to port to it.
* See: [https://github.com/google/centipede](https://github.com/google/centipede)
* For us in OSS-Fuzz, it’s been usually easy to switch to centipede, but not always. E.g., libc++ came with the program, but now you DO need libc++. Google doesn’t normally use the “normal” C compiler (except the Linux kernel), so need to specially link.
* 

<h3>Mar 7, 2023</h3>


Attendees:



* David A. Wheeler (Linux Foundation) [had to leave early]
* Chris B (Google)
* Addison Crump (CISPA)
* Carl Smith (Google)
* David Korczynksi (Ada Logics)
* Adam Korczynski (Ada Logics)
* Jonathan Metzman (host)
* Joe Ranweiler (Microsoft)
* Caleb Jasik (Astro / Defined Networking)
* Kostya Serebryany (Google)
* Cory Duplantis (AWS)

Discussion topics:



* Jonathan M.: Fuzzing competition - still in process
* There were 1-2 bugs on our end that needed fixing, they appear “at least somewhat fixed”
* Results so far: [https://www.fuzzbench.com/reports/experimental/2023-03-06-sbft23-cov/index.html](https://www.fuzzbench.com/reports/experimental/2023-03-06-sbft23-cov/index.html)
* Chris B wanted to ask some questions…
* Mozilla not here!
* Caleb Jasik: What OpenAPI sourced fuzzers are there available in OSS
*  [https://github.com/microsoft/restler-fuzzer](https://github.com/microsoft/restler-fuzzer)
* Original paper oriented towards a systematic exploration of the search space
* [https://github.com/Endava/cats](https://github.com/Endava/cats) (This has been simplest to execute and receive *some* useful feedback with - Caleb Jasik)
* [https://github.com/matusf/openapi-fuzzer](https://github.com/matusf/openapi-fuzzer)
* [https://github.com/microsoft/restler-fuzzer/blob/main/docs/user-guide/Compiling.md](https://github.com/microsoft/restler-fuzzer/blob/main/docs/user-guide/Compiling.md) 
* Obvious answer is to fuzz the individual endpoint handlers via a standard fuzzing harness for bugs, but a general comprehensive tool is useful
* PHP fuzzer w/ feedback? [https://adamdoupe.com/publications/witcher-oakland2023.pdf](https://adamdoupe.com/publications/witcher-oakland2023.pdf) 
* directed symbolic execution for basebands, around [https://github.com/fgsect/JMPscare](https://github.com/fgsect/JMPscare) 
* Google Group: [https://groups.google.com/g/fuzzing-collaboration](https://groups.google.com/g/fuzzing-collaboration) 
* [https://gts3.org/assets/papers/2023/fu:autofz.pdf](https://gts3.org/assets/papers/2023/fu:autofz.pdf) 
* [https://arxiv.org/abs/1803.02130](https://arxiv.org/abs/1803.02130) 
* [https://arxiv.org/pdf/2202.13114.pdf](https://arxiv.org/pdf/2202.13114.pdf) 
* [https://mboehme.github.io/paper/ICSE23.Effectiveness.pdf](https://mboehme.github.io/paper/ICSE23.Effectiveness.pdf) 

<h3>Feb 7, 2023</h3>


Attendees:



* David A. Wheeler (Linux Foundation)
* Chris Bookholt (Google)
* Joe Ranweiler (Microsoft)
* Jonathan Leitschuh (OpenSSF / Alpha-Omega Project)
* Caleb Jasik (Astro / Defined Networking)
* Jonathan Metzman (Google)
* Addison Crump
* Dominik Maier
* Chris Ball (Zoom)
* Edward Qiu

Discussion topics:



* Chirs Bookholt: Adventures in fuzzing - maybe we can ID some lessons learned
* Chrome has done a lot of fuzzing, has learned a lot
* We’ve written a lot of fuzzers & learned much, trying to figure out what we do next regarding fuzzers.
* Multi-threaded fuzzing can be a sticking point!
* We’ve written 2 libfuzz-based fuzzing, esp. IPC layers because there’s a lot going on.
* Due to quirks of Chrome testing infrastructure, we tend to write fuzzers that are in-process, and the fuzzers are single process yet Chrome itself is NOT a single process. As a result, the fuzzer fuzzes only something that “looks like Chrome” instead of actual Chrome, leading to fuzzing results that don’t match the real thing.
* Libfuzzer is really helpful, don’t want to dump on that, it’s been useful.
* **One learning: When testing, test a system that is close as possible to the real thing - every difference (e.g., threading) can make the results less helpful.**
* **Another: There are sharp edges when trying to do multi-threaded fuzzing with libfuzzer**. There’s a queue of tasks that the fuzzer doesn’t know about. Then the fuzzer says “test case 10 crashed” but in fact “test case 5” is what failed, leading to false info.
* **The general approach is to keep a queue of the environment, then restart from a clean environment & recreate mostly the state. Or use snapshot fuzzing, where most such problems go away.**
* Chris: I’ll look into providing a queue to record a series of test cases, so we can have a better chance of triggering. In the longer term we’ll need to look at snapshot fuzzing, that’s more real-world.
* What about green threads (so you have more control)?
* Then you’re not at the mercy of the OS, you can control the threading schedules, then you can reproduce.
* That works in some cases, but I suspect it breaks in corner cases
* Mozilla rr /  Pernosco
* Code with timetravel debugging, e.g., rr - [https://github.com/rr-debugger/rr](https://github.com/rr-debugger/rr) - recoding overhead is large (think 10-100x), so not great during fuzing.
* You could track a queue during normal fuzzing, then rerun a queue using rr or similar many times until you find the threading conditions that cause it, then you can reproduce it, debug, etc.
* i believe rr collapses threading to a single core interleaving in the trace, which is the motivation for its "chaos mode": [https://robert.ocallahan.org/2016/02/introducing-rr-chaos-mode.html](https://robert.ocallahan.org/2016/02/introducing-rr-chaos-mode.html)
* [https://learn.microsoft.com/en-us/windows-hardware/drivers/debugger/time-travel-debugging-overview](https://learn.microsoft.com/en-us/windows-hardware/drivers/debugger/time-travel-debugging-overview)
* “Full system emulation is the only way to get nondeterminism right”
* Anyone else want to share something cool they’re working on?
* Jonathan Leitschuh: Openrewrite - lets you create recipes to generate new code from old code that matches the format of the original code. This could enable creating variations that go back to the maintainer. They support Java, working on Kotlin. Could use that to easily generate a fuzz harness.
* It’d be great to improve how we create fuzz harnesses, so that a fuzzer can test that code (that isn’t immediately invokable from the command line).
* Experience on DFSan (DataFlow Sanitizer)?
* [https://clang.llvm.org/docs/DataFlowSanitizerDesign.html](https://clang.llvm.org/docs/DataFlowSanitizerDesign.html) 
* In C++, when passing moving into a vector, that's nondeterministic & probably not right. Constructor accepts vector AND a separate vector size moves into a final value. The problem is that the vector.size evaluation may occur after the vector has been moved, and order of evaluations in a call isn’t specified. In short, in f(a,b), there’s no guarantee if “a” or “b” is calculated first. This hits many. E.g.
* void foo(size_t some_size, std::vector<int> x){ ... }
* foo(some_vec.size(), std::move(some_vec));
* Note: GitHub does have its own mechanism for mass detection (give CodeQL query), but that’s for detection not for reporting to those with the vulnerability.
* Jon: I don’t think there’s a way to create PR to fix, just detection.
* Unofficially we often chat via Discord. https://discord.gg/kYbGr2Jv
* Plan to add Centipede as “opt-out” for OSS-Fuzz for cases where it seems useful.
* [fast-check](https://github.com/dubzzz/fast-check/tree/main): property testing for Typescript / Javascript: first stable integration with the Vitest test runner released ([https://github.com/dubzzz/fast-check/releases/tag/vitest%2Fv0.0.1](https://github.com/dubzzz/fast-check/releases/tag/vitest%2Fv0.0.1))
* Does anyone have a modern coverage gathering/display tool they like?  Lots of 90s .html output in the classic tools.
* I think we demo'd some of that here: [https://youtu.be/Wy7qY5ms3qY?t=1974](https://youtu.be/Wy7qY5ms3qY?t=1974)
* A sad thing we’ve ran into is that the golang race detector requires CGO compilation enabled, which means we choose between not having race detection in tests, or having an unused dependency on libc in prod
* “If you’re not testing with ASAN, you’re leaving bugs on the table, but don’t use in production”. UBISan is good but harder to use.
* Any suggested C/C++ compiler flags?
* I saw that Fedora added frame pointers across the distro last week, not directly a security control but pretty helpful
* 

<h3>Jan 3, 2023</h3>


Discussion topics



* We’re expecting this to be lightly attended, many are still on vacation
* [metzman] I plan to try Tsan (thread sanitizer) fuzzing, build fuzzing - first time using that tool
* I’d love to see tsan results for imagemagick, cryptofuzz
* What about “Dav1d” (videoLan group)/VLC
* [https://www.videolan.org/projects/dav1d.html](https://www.videolan.org/projects/dav1d.html) 
*  wonders about differential fuzzing between Dav1d and [https://github.com/xiph/rav1e](https://github.com/xiph/rav1e) as a useful and effective oracle for implementation errors
* Dav1d is a decoder
* Rav1e is an encoder
* Mozilla found tsan had serious overhead & had some false+ in external libraries, though they weren’t hard to resolve.
* [https://bugzilla.mozilla.org/show_bug.cgi?id=tsan](https://bugzilla.mozilla.org/show_bug.cgi?id=tsan) 
* ?: Not as useful for unit-test style tests.
* -ffastmath
* gcc and not clang
* Maybe OpenSSL
* (Alex Gaynor) I'm not sure the OpenSSL devs regularly run TSAN. The rust-openssl author has reported a number of bugs in OpenSSL because he runs _his_ test suite with TSAN [https://github.com/openssl/openssl/issues?q=is%3Aissue+author%3Asfackler+](https://github.com/openssl/openssl/issues?q=is%3Aissue+author%3Asfackler+)
* 
* [to metzmann] please provide more information on [https://sbft23.github.io/tools/fuzzing](https://sbft23.github.io/tools/fuzzing)
* Marc Heuse: Confused about dates in fuzzing competition.
* And rewards
* Per web page: Express your interest here (Deadline: AoE Friday 13 Jan 2023).
* This is the correct date - metzman
* Caleb Jasik is interested in [https://github.com/CodeIntelligenceTesting/jazzer.js](https://github.com/CodeIntelligenceTesting/jazzer.js) working on bringing easy integration of fuzzing to TS/JS libraries, to the level of [https://github.com/dubzzz/fast-check](https://github.com/dubzzz/fast-check)
* Planned for CodeIntelligence to create this integration; waiting for them (but planned for soon!)

Attendees



* David A. Wheeler, Linux Foundation
* Navid Emamdoost (Google)
* Alex Gaynor 
* Vranken
* Caleb Jasik (Defined Networking, Astro)
* Marc “vanHauser” Heuse
* Addison Crump (CISPA)
* Tyson
* Chris Ball (Zoom)
* Metzman (Google)
* Jason Kratzer
* Peng Li (ByteDance)
* Max Moroz (ByteDance)

<h3>Dec 6, 2022</h3>


Agenda:



* [0xedward] Is there libfuzzer support for Chromium on Android arm64 target?	
* Chris Bookholt is trying to repro momentarily...


$> gn args out/arm64.fuzz
Waiting for editor on "/opt/chromium/clank/src/out/arm64.fuzz/args.gn"...
# Build arguments go here.
# See "gn args <out_dir> --list" for available build arguments.
#use_goma = true
target_os = "android"
target_cpu = "arm64"
check_always_on = false
enable_nacl = false
ffmpeg_branding = "Chrome"
is_asan = true
is_component_build = true
is_debug = false
optimize_for_fuzzing = true
pdf_enable_xfa = true
proprietary_codecs = true
use_libfuzzer = true

Generating files...
ERROR at //third_party/libprotobuf-mutator/fuzzable_proto_library.gni:24:7: Assertion failed.
assert(current_toolchain == host_toolchain ||

See //third_party/libprotobuf-mutator/BUILD.gn:62:1: whence it was called.
fuzzable_proto_library("lpm_test_fuzzer_proto") {

See //third_party/blink/common/BUILD.gn:490:7: which caused the file to be included.
"//third_party/libprotobuf-mutator",



* I took out the asset for the sake of experimentation, which led to a bunch of build issues about dependency visibility violations. I squashed those by making (inappropriately) generous visibility adjustments. Then there was a random build failure due to a warning about an unused function, which I squashed by (inappropriately) deleting the function. Now there's another build failure about use of an undeclared member variable, and I'm at the point where it's becoming non-trivial to continue squashing errors. 
* My takeaway so far is that none of these build failures should exist and none seem inherently due to libfuzzer. These build failures should be getting caught automatically by our build bots as developers introduce changes that break fuzzers, but they're not and I would _guess_ that's because our build bots don't include an Aarch64 target with these fuzzer-friendly gn flags, meaning this is more or less untested code for Chromium. 

<h3>Nov 1, 2022</h3>




* [metzman] Centipede: minor updates
* [metzman] OpenSSL vulnerability hot takes.
* [https://storage.googleapis.com/oss-fuzz-coverage/openssl/reports/20221031/linux/src/openssl/crypto/x509/x509_vfy.c.html#L221](https://storage.googleapis.com/oss-fuzz-coverage/openssl/reports/20221031/linux/src/openssl/crypto/x509/x509_vfy.c.html#L221)
* too hard for fuzzer to get past this
* Fuzzer competition [Https://twitter.com/sbftworkshop/status/1585022593480167424](Https://twitter.com/sbftworkshop/status/1585022593480167424)
* XSS fuzzer
* coverage from javascript J2cl for java fuzzer

<h3>Oct 4, 2022</h3>


Attendees



* Navid Emamdoost
* Jonathan Metzman
* Max Moroz
* peng.li@bytedance.com
* Chris Bookholt
* Cornelius Aschermann
* Laszlo Szekeres (Google)
* Jesse Schwartzentruber (Mozilla)

[bookholt] Quick update on snapshot fuzzing in Chrome



* coverage across multiple processes
* non-determinism
* performance?
* always willing to chat more - [bookholt@google.com](mailto:bookholt@google.com)

[bookholt] Is anyone aware of work to increas7e determinism of a snapshot fuzzer harness?



* MSFT have an emulator based on Bochs
* Minimize sources of non-determinism in the OS
* e.g. use a minimal Linux build
* artificially inflate priority of the target, i.e. Chromium process tree

[lszekeres] Heads up on new fuzz testing / property-based testing framework from Google



* Not officially launched yet, but we started open sourcing: 

[https://github.com/google/fuzztest](https://github.com/google/fuzztest)

* Please stay tuned for our official launch announcement later this year!
* In the meantime, feel free to reach out if you're interested in being an early adopter or if you'd like to collaborate: [lszekeres@google.com](mailto:lszekeres@google.com)

[metzman] SystemSan



* [https://security.googleblog.com/2022/09/fuzzing-beyond-memory-corruption.html](https://security.googleblog.com/2022/09/fuzzing-beyond-memory-corruption.html)
* 

[kcc] will join the second 30 minutes

<h3>Sep 6th, 2022</h3>


Attendees:



* David A. Wheeler (Linux Foundation)
* Metzman
* Chris Bookholt
* Chris Ball
* Navid Emamdoost
* Cornelius Aschermann (Meta)
* Kostya Serebryany
* Alex Bulekov
* Vranken
* [Alex Gaynor] possibility of adding corpus-as-code APIs to libFuzzer? (ala [https://pkg.go.dev/testing#F.Add](https://pkg.go.dev/testing#F.Add))
* Maybe for purpose of similar snapshot fuzzing in mutating arguments to unittests.
* Kcc not here for discussion.
* Kcc will join in ~ 5 min
* kcc arrived
* libFuzzer is minimalistic interface
* Google is about open source rich interface for C++ - it needs to be added there
* [kcc] will join the second 30 minutes, if you are still there
* chris ball: Impressive for small fuzzer
* Wanted to rewrite 2 dozen different things in libFuzzer (main one is in-process)
* Scale - many more edges
* Current engines stuck because they minimize corpus
* Centipede doesn’t try this -> allows hitting longer tail
* trying bounded paths - quadratic/cubic/exponential with size of binary
* [kcc] [github.com/google/centipede](https://github.com/google/centipede) : _early_ adopters and feedback is welcome. 
* Centipede is a new distributed fuzzing engine
* compiler wrapper
* Different model: -fsanitize=cenitpede from distribution but not planned currently
* .so
* fake callbacks in sanitizer runtime
* shouldn’t need it to run
* [bookholt] Chrome Mojo IPC & snapshot fuzzing at Google Summer of Code '22
* Chromium’s fuzzing system built into the process, it’s quite different from the “real” software delivered to users
* Enter Snapshot fuzzing! It’s 80% there.
* Thanks to Mozillans for help/etc. It’s gone surprisingly well!
* Nyx - code derived from QEMU. Environment is Google Cloud. Nested virtualization - could have problems.
* David: Is there a key resource you need?
* Don’t know of one (yet).
* Fuzzing Chrome is disappointingly slow because it’s big.
* Another team is interested in improving clusterfuzz, might help.
* Going to be trouble with docker.
* metzman: CF probably shouldn’t be using docker.
* David: What about using multiple snapshots so you don’t have to start from beginning each time? It’d be faster if you don’t have to start at the same point every time
* Eqv (I’m on facebook & worked on nyx): Nyx can snapshot, multiple levels, can use that so don’t have to start from beginning but in fact can restart fuzzing “much deeper in”
* Haven’t investigated, that might help.
* David A. Wheeler: OpenSSF will have an “OpenSSF EU Day” in Dublin on September 13, 2022. Any announcements we could make there about major events/successes of the last few months (since June 20 OpenSSF Day in Austin)?
* Nothing specific.
* (See Alex Gaynor note above)
* Some links
* https://www.fuzzbench.com/reports/experimental/2022-08-13-centipede/index.html
* https://storage.googleapis.com/centipede/2022-08-17-11-06-1d-dongge/index.html
* [https://github.com/google/centipede/blob/ab462e3ca457a2380e3692d41405ae4d1a1d84af/runner.h#L72](https://github.com/google/centipede/blob/ab462e3ca457a2380e3692d41405ae4d1a1d84af/runner.h#L72)

<h3>Aug 2nd, 2022</h3>




* ClusterFuzzLite adoption
* Proxygen is interesting
* Is already integrated into OSS-Fuzz though https://github.com/google/oss-fuzz/tree/master/projects/proxygen
* Crypto - guido
* Hard for me to get visibility, limited influence
* Centipede
* are there any writeups?

<h3>July 5th, 2022</h3>




* Discussion on blind fuzzing and it’s advantages/disadvantages over coverage-guided fuzzing.
* Research ideas on how to improve the seed distribution created by generator fuzzers
* Current structure-aware fuzzers provide biased corpus generation, there is an opportunity to improve this.
* Reference to John Regehr style fuzzing (CSmith (I think) [https://embed.cs.utah.edu/csmith/](https://embed.cs.utah.edu/csmith/))
* Why is this relevant, i.e. why move away from coverage-guided fuzzing? Because of the cases where there is no/limited possibility for coverage collection, e.g. embedded systems and similar. 
* For grammar-fuzzing there is some level of control over the distribution. However, for freeform data there isn’t the same.
* Attendees:
* 12 people attended in zoom (fyi This was on holiday for many as many regulars were not present).

<h3>June 7th, 2022</h3>




* David A. Wheeler: I’ll ask Jory Burson to check out the calendar issues, will cc Jonathan Metzman (Google)
* bookholt@chromium.org wonders about the state of snapshot fuzzing for browsers, e.g. current projects & observations from past experiments like [this one](#bookmark=kix.1px6jxjk7wi4). 
* bookholt@chromium.org is particularly interested in examples of status signaling between fuzzer and target, e.g. when target process crashes.
* (decoder) Will provide an update soon on snapshot fuzzing efforts in Firefox. tl;dr: We are successfully using Nyx to fuzz IPC in Firefox.
* Fuzz introspector is having some successes. [https://github.com/ossf/fuzz-introspector](https://github.com/ossf/fuzz-introspector)
* David Korczynski: It does more than id coverage blockers, but that’s part of it. The key questions fuzz-introspector tries to answer are “is my fuzzing good enough for this project” and if the answer is “no” then fuzz-introspector furthers tries to help answer questions e.g. “should I implement a new fuzz driver” or “should I modify an existing fuzz driver”.
* Many reported that symbolic execution doesn’t helpfully figure out how to work around a blocker. Often there are earlier preconditions necessary. The solution is to get a human involved to figure out how to work around it, often by changing the code harness.
* If you’re doing a 1-shot test, you can simply create special call that isn’t maintained. But if this is something going into the CI test, it needs to keep working over time through changes.
* Often the solution is simple such as adding a special dictionary entry, output a special format, etc.
* Timing leaks?
* Use fuzzers to find timing leaks?
* Fuzzers don’t generally do that, don’t see why they couldn’t do it in principle
* David W: That was a big topic in 80s (Orange Book), but computers were very expensive. Today’s CPUs leak a lot of data via timing, if you REALLY care, spend a few cents to get another CPU instead of trying to fix it in software. Crypto libraries try to prevent the worst, but it’s more of “don’t have your loops depend on keys & don’t leak during encryption” than trying to prevent all timing leaks. That is, there’s a more narrow focus on preventing unintentional side-channel leaks from a crypto library than the general (very hard) problem.
* One tool: [https://github.com/Fraunhofer-AISEC/DATA](https://github.com/Fraunhofer-AISEC/DATA)
* Marcel: Side channel sanitizer
* David: Thanks. A student of mine used such a tool, but I’m having trouble finding that work. It ran code a whole bunch of times to detect timing variances IIRC - perhaps that will help you find it?
* Marcel: Measuring would be the classical way of discovering timing side-channels. Our approach would be to identify the optimization-induced leakage via the optimized computation. If anyone is interested in more details and potential impact, you are welcome to reach out (mboehme.github.io)

Attendees (29 in total in Zoom):



* Jonathan Metzman (Google)
* David Korczynski (Ada Logics)
* Adam Korczynski (Ada Logics)
* David A. Wheeler (Linux Foundation)
* Tyson Smith (Mozilla)
* Max Moroz (ByteDance)
* Navid Emamdoost (Google)
* Chris Bookholt (Google),
* Marcel Böhme (MPI-SP)

<h3>May 3rd, 2022</h3>


Agenda:



* Max: question about fuzzing stateful programs. We used to avoid it in the past. Are there any new developments? Tools or techniques to efficiently fuzz stateful targets?
* [https://github.com/RUB-SysSec/nyx-net](https://github.com/RUB-SysSec/nyx-net)
* ForAllSecure
* [https://github.com/cncf/cncf-fuzzing/blob/main/projects/cri-o/fuzz_server.go](https://github.com/cncf/cncf-fuzzing/blob/main/projects/cri-o/fuzz_server.go)
* Follow-up: restart the program for every input or not?
* Consider resetting the state somehow else, without a full restart
* Can do some limited sequence of message between restarts
* Check envoy proxy fuzz targets, they have some stateful targets and combine state resetting with continuous running without state resent (can ask Harvey and Ashra – reportedly they liked the targets that didn’t reset the state, for the sake of performance)
* [https://github.com/envoyproxy/envoy/blob/main/test/integration/h2_fuzz.cc](https://github.com/envoyproxy/envoy/blob/main/test/integration/h2_fuzz.cc)
* “These are the lines in the Bazel build where you see the same fuzzer compiler for persistent vs non-persistent: [https://github.com/envoyproxy/envoy/blob/4d177008ab5e43f1fbe6dfd52d83af106cf277d0/test/integration/BUILD#L1486-L1499](https://github.com/envoyproxy/envoy/blob/4d177008ab5e43f1fbe6dfd52d83af106cf277d0/test/integration/BUILD#L1486-L1499)” – but the same fuzzer -- persistent without reset
* eqv mentioned some other target that rarely reset the state (as it’s expensive) and suffers a high percentage of non-reproducible cases
* In persistent mode of AFL++ you can set a reset for every N iterations and capture log messages including all the inputs that were sent prior to the reset
* the record env in afl++ is AFL_PERSISTENT_RECORD
* Discussed the idea of re-running the whole fuzzing session (starting from the same seed value) in order to imitate and reproduce the state mutation sequence. The collective response is that there are more factors affecting the state and thus the idea isn’t very promising.
* [https://github.com/fgsect/FitM](https://github.com/fgsect/FitM)
* [https://arxiv.org/pdf/2110.06253.pdf](https://arxiv.org/pdf/2110.06253.pdf)
* NSFuzz: Towards Efficient and State-Aware Network Service Fuzzing
* Navid: Fuzz Introspector [experience](https://github.com/ossf/fuzz-introspector/blob/main/doc/CaseStudies.md) on how it improved coverage
* [https://github.com/ossf/fuzz-introspector](https://github.com/ossf/fuzz-introspector)
* metzman: brief summary of [FUZZING’22 Workshop](https://fuzzingworkshop.github.io/)
* metzman:
* Dumb structure aware fuzzers beating coverage guided?
* nyxnet gives some of the best of both worlds. Cornelius thinks it’s really the solution for this
* Ask carl smith about code cov on jitted code
* [https://github.com/llvm/llvm-project/blob/main/compiler-rt/lib/fuzzer/FuzzerTracePC.cpp#L383](https://st1.zoom.us/web_client/1q1nf58/html/externalLinkPage.html?ref=https://github.com/llvm/llvm-project/blob/main/compiler-rt/lib/fuzzer/FuzzerTracePC.cpp#L383)
* [https://hexgolems.com/2020/08/on-measuring-and-visualizing-fuzzer-performance/](https://st1.zoom.us/web_client/1q1nf58/html/externalLinkPage.html?ref=https://hexgolems.com/2020/08/on-measuring-and-visualizing-fuzzer-performance/)
* [https://github.com/andreafioraldi/libafl_quickjs_fuzzing](https://st1.zoom.us/web_client/1q1nf58/html/externalLinkPage.html?ref=https://github.com/andreafioraldi/libafl_quickjs_fuzzing) 
* [https://github.com/sslab-gatech/winnie](https://st1.zoom.us/web_client/1q1nf58/html/externalLinkPage.html?ref=https://github.com/sslab-gatech/winnie)
* What to focus function?
* Guido has seen a case that took OSS-Fuzz years to find but he found much quicker using focus function.
* Optimized ASM is good to target
* Fuzzing effectiveness goes down as Q grows focus function fights back against this.
* IJON let you ignore coverage on certain areas.
* libafl inspired by vrankenfuzz

Attendees (20):



* David Korczynski (Ada Logics)
* Jonathan Metzman (Google)
* Kcc (Google) will join the second half
* Max Moroz (ByteDance)
* Navid Emamdoost (Google)
* Laszlo Szekeres (Google)

<h3>April 5th, 2022</h3>


Attendees:



* David A. Wheeler (Linux Foundation)
* David Korczynski (Ada Logics)
* Marcel Boehme (MPI-SP)
* Kostya Serebryany (Google)
* Cornelius Aschermann (Meta)
* Alison Huffman (Microsoft)
* Christoph Diehl (Microsoft)
* Navid Emamdoost (Google)
* Moshe Kaplan (personal capacity)
* Abdulrahman Alqabandi (Microsoft)
* Adam Korczynski (Ada Logics)
* Stephen Magill (Sonatype)
* Guido Vranken
* Tyson Smith (Mozilla)

Agenda:



* Guido Vranken presenting on differential fuzzing.
* Cryptofruzz ([https://github.com/g uidovranken/cryptofuzz](https://github.com/guidovranken/cryptofuzz)) is a library for fuzzing cryptographic libraries, he keeps finding new bugs
* Cryptofuzz is a libFuzzer front-end for differential fuzzing of various cryptographic libraries.  Once built, the cryptofuzz executable behaves like a standard libFuzzer interface.
* For each crypto library, for each interface, must create a C++ header for it.
* Cryptofuzz then creates a bunch of random inputs for each
* It checks some invariants on each call (called “static” checks, but they’re run dynamically)
* Specialized tests for each interface. E.g., checks if the inverses work on symmetric key encryption.
* Has a large amount of specialized code for each interface.
* Each target to fuzz is essentially implemented separately, it’s not hard but it’s a lot of work to add a new target
* Often compare the results between different libraries if they’re supposed to be the same answers (making it differential)
* Has anyone added this to their CI pipeline? Don’t know about CI pipeline, but did have someone ask to have a module created.
* An alternative: OSS-Fuzz could use this also when a relevant module is fuzzed.
* “Ci-fuzz” is brief (shallow) instead of running 24 hours+, but that means it provides faster feedback to developers. Systemd is happy with CI-fuzz, ci-fuzz finds the defects first & OSS-fuzz doesn’t end up finding them later.
* Kostya Serebryany: In my fuzzing runs I use ~16,000 processors, allows us to explore different multiple extremums
* Swarm testing paper by Groce et al: [https://www.cs.utah.edu/~regehr/papers/swarm12.pdf](https://www.cs.utah.edu/~regehr/papers/swarm12.pdf) - “In swarm testing, the usual practice of potentially including all features in every test case is abandoned. Rather, a large “swarm” of randomly generated configurations, each of which omits some features, is used, with configurations receiving equal resources.”
* David Korczynski, if time permits, a minor update on fuzz-introspector, to give insight into fuzzing activities
* Time permitted. [ossf/fuzz-introspector](https://github.com/ossf/fuzz-introspector)
* Trying to make it more user-friendly. Have added high-level conclusions, e.g., # functions reachable
* 

<h3>March 1st, 2022</h3>


Attendees:



* David A. Wheeler (Linux Foundation)
* László Szekeres (Google)
* Jonathan Metzman (Google)
* Marcel Böhme (MPI-SP)
* Jason Kratzer (Mozilla)
* Adam Korczynski (Ada Logics)
* David Korczynski (Ada Logics)
* Alex Gaynor
* Amir Montazery (OSTIF)
* Bilal Gonan
* Farzon Lotfi
* Hanain Lakhani
* Jason Kratzer
* Jeffrey Borek
* Jesse Schwartzentruber
* Kevin Stephens
* Laurent
* Marc (Mobil)
* Marcel Boehme
* Max Moroz (ByteDance)
* Navid Emamdoost (Google)
* Peng Li (ByteDance)
* Seth Hinze
* Tyson Smith (Mozilla)
* Yotam Perkai

Notes:



* [metzman] ddfuzz/dataflow instrumentation ([https://www.s3.eurecom.fr/docs/eurosp22_mantovani.pdf](https://www.s3.eurecom.fr/docs/eurosp22_mantovani.pdf))
* Who is employing heuristics to decide which strategies.
* Marcel: Equally works well, or dynamically learn, multi-armed bandit.
* [lszekeres] [FUZZING’22 workshop](https://fuzzingworkshop.github.io/)
* [https://fuzzingworkshop.github.io/](https://fuzzingworkshop.github.io/)
* Papers without “evaluation section” are submitted, so workshop evaluation only evaluates “nobility of hypothesis” not the actual results.
* “We feel that the incentive structures are off” in many other forums - often there is questionable methodology, e.g., unsound. They want to publish first the process for the experiment to be done (pre-registration), THEN have the work done.
* One positive of this approach: If something seems like a good idea but doesn’t work in practice, it’ll still be published
* See this, for the explanation of the advantages of preregistration: [http://fuzzbench.com/blog/2021/04/22/special-issue](http://fuzzbench.com/blog/2021/04/22/special-issue/)
* Looking for people to help with artifact evaluation.
* If interested, reach out to: [lszekeres@google.com](mailto:lszekeres@google.com), [marcel.boehme@mpi-sp.org](mailto:marcel.boehme@mpi-sp.org)
* David: Preregistration is often mentioned re: reproduction crisis [https://en.wikipedia.org/wiki/Replication_crisis](https://en.wikipedia.org/wiki/Replication_crisis)
* Free discussion
* What about fuzzing go programs?
* https://adalogics.com/blog/fuzzing-istio-cve-CVE-2022-23635
* https://adalogics.com/blog/the-importance-of-continuity-in-fuzzing-cve-2020-28362
* https://github.com/cncf/cncf-fuzzing
* I might have a question for everyone on experiences with automated debugging and repair.
* https://blog.ethereum.org/2020/11/12/geth_security_release/
* The Istio CVE was a simple null-pointer dereference
* It’s also very threat-model specific.

<h3>Feb 1st, 2022</h3>




* Afl++ 4.0c released with nyx_mode, llvm iselect instrumentation, etc.
* [tyson] metzman had a TODO to contact taviso regarding the NSS bugs he logged. Any update?
* [kcc] did anyone try the new SanitizerCoverage load/store callbacks? 
* [https://clang.llvm.org/docs/SanitizerCoverage.html#tracing-data-flow](https://clang.llvm.org/docs/SanitizerCoverage.html#tracing-data-flow)
* 

<h3>January 4th, 2022</h3>




* Meeting has moved to OpenSSF.
* Meeting now conducted over zoom. Not Google Hangouts.
* New members introduction
* [Fuzz Introspector](https://github.com/ossf/fuzz-introspector) demo

<h3>December 7th, 2021</h3>




* Meeting is moving to OpenSSF, starting January 2022
* Available on [OpenSSF community calendar](https://calendar.google.com/calendar/u/0?cid=czYzdm9lZmhwNWk5cGZsdGI1cTY3bmdwZXNAZ3JvdXAuY2FsZW5kYXIuZ29vZ2xlLmNvbQ)
* New project in incubation stage - [Fuzz Introspector](https://github.com/ossf/fuzz-introspector), demo in Jan 2022
* [decoder, only first 30 mins] MSan status?
* MSan builder link is 404
* Used with Chrome?
* [kcc] [Tavis’s blog](https://googleprojectzero.blogspot.com/2021/12/this-shouldnt-have-happened.html): I still don't understand whether there was (or, is now) a fuzz target that exercises this code. 
* What can we do better ? Stack coverage - [https://twitter.com/andreafioraldi/status/1466163396248846337](https://twitter.com/andreafioraldi/status/1466163396248846337), [https://twitter.com/metzmanj/status/1466487569294794756](https://twitter.com/metzmanj/status/1466487569294794756) ?
* David A. Wheeler:
* When I read this, it reminded me of past discussions about coverage-guided testing. Coverage-guided fuzz testing is *remarkably* effective - people were surprised how effective it was when it was first tried.
* However, coverage-guided fuzz testing has a fundamental weakness: it can only notice when different counts of _existing_ code paths are tried. Just like coverage coverage metrics, while it’s useful, coverage-guided fuzzing typically can’t notice when there is _missing_ code - only when different counts branches of _existing_ code is taken.
* Perhaps coverage-guided fuzzers could be modified to insert “likely missing code” (like checks on maximum lengths in a loop), for purposes of coverage, and then notice when the count became different. This is speculation on my part, but it’d be great is coverage-guided fuzzers could be modified to overcome this historical weakness of the approach (that they don’t do a good job in noticing _missing_ code).
* TODO([metzman](https://who.corp.google.com/metzman)): Follow up with Tavis on this?
* he told kcc he used a binary in the nss build for fuzzing, so it seems likely that the primary issue is that fuzz targets cannot hit this code  
* [kcc] early results with (weak) data flow signal.
* Using [__sanitizer_cov_load1() & co](https://clang.llvm.org/docs/SanitizerCoverage.html#tracing-data-flow)
* Coverage signal (“feature”) is “a global at address X is loaded at PC Y”
* [metzman] OSS-Fuzz breakage being fixed
* [decoder] Links for Snapshot Fuzzing
* [https://bugzilla.mozilla.org/show_bug.cgi?id=1738278](https://bugzilla.mozilla.org/show_bug.cgi?id=1738278)
* [Example Target](https://phabricator.services.mozilla.com/D130161) (just for demo purposes, and slightly outdated)
* Intel PT can be used, but won't work in Cloud (can work in AWS bare metal or custom clouds though)

<h3>November 2nd, 2021</h3>




* [Marc Heuse]
* llvm optimizing and fuzzing
* Redqueen found bug in O2 but not O1 or O0
* Laszlo thinks sanitizers would make this unnecessary
* Integer operations especially
* Cornelius likes random
* Coverage loss due IR “select”
* Non-llvm targets (gcc only targets)
* [Jonathan Metzman]
* ClusterFuzzLite launch

<h3>October 5th, 2021</h3>




* [decoder (have to leave after 30 mins)] Experimental snapshot-based testing for Firefox IPC
* prototype from cornelius and sergej
* finding sandbox escapes. Already 2 bugs?
* Gives coverage of things they wanted for years.
* Uses beyond just IPC
* Tool: nyx
* This is running on dedicated hardware because hypervisor needs to run on baremetal for good performance.
* It uses intelpt tracing.
* future version should work with just KVM and not
* should work with kernel 5.11
* FF starts up. Content process signals it’s ready, then sends some stuff from fuzzer to the parent. Parent synchronizes. Resets when the parent aborts or signals it’s done.
* Current performance: About 25 iterations per sec per core (Intel i9-9900K)
* Currently based on intercepting sendmsg/recvmsg. Better implementation inside FF IPC layer, including shmem support, is on the roadmap.
* [metzman] “Analysis” of fuzzers on CF.
* Try to get coverage numbers
* kcc: cpu fuzzing paper to arxiv

<h3>August 3, 2021</h3>




* [Marc Heuse] results of the analysis what concolic execution engines can help with additional coverage to afl++’s cmplog/redqueen (eclipser, symqemu, fuzzolic)
* [mhl] Normalizing results when analysing clusterfuzz strategies results
* [Marc Heuse] minimizing a corpus can throw back the fuzzing progress
* …
* Next call: Analysis of fuzzers on CF

<h3>July 12, 2021</h3>




* [Laurent] do we need some sort of program diversity metric when selecting programs for benchmarking fuzzers? If so, what are good metrics - both micro- (instructions) and macro- (higher-level constructs)?
* Andrea: parsers missing
* Maybe add a way to select benchmarks
* Laurent, maybe try to pass json target more files to test.
* Andrea Fioraldi is invited and will present on his paper “The Use of Likely Invariants as Feedback for Fuzzing”

<h3>June 1, 2021</h3>




* [decoder] Would like to invite Andrea Fioraldi for next meeting
* Talk on “The Use of Likely Invariants as Feedback for Fuzzing” ([preprint](http://www.s3.eurecom.fr/docs/usenixsec21_fioraldi.pdf))
* [decoder] Random flags on custom JS fuzzing
* [Marc] How to measure fuzzer features on saturated corpus runs?
* [Marc] afl++ 3.13c released today :)
* Binary fuzzing on mac (using frida)
* AI: Jonathan - try 0 corpus subset.

<h3>April 6, 2021</h3>




* Welcome Antonio Morales Maldonado from GitHub. Share idea on other ways of fuzzing feedback (other than coverage).
* [https://github.com/rohanpadhye/FuzzFactory](https://github.com/rohanpadhye/FuzzFactory)
* Also, check [https://www.syssec.ruhr-uni-bochum.de/media/emma/veroeffentlichungen/2020/02/27/IJON-Oakland20.pdf](https://www.syssec.ruhr-uni-bochum.de/media/emma/veroeffentlichungen/2020/02/27/IJON-Oakland20.pdf) [from Cornellius]
* AFL++ has longer path feature.
* AFL++ has branch, 1) number of loops on path, 2) count of malloc/frees
* [https://www.fuzzbench.com/reports/experimental/2021-03-12-aflpp-bug/index.html](https://www.fuzzbench.com/reports/experimental/2021-03-12-aflpp-bug/index.html)
* Has anyone tried IPT with success?
* [https://blog.trailofbits.com/2021/03/19/un-bee-lievable-performance-fast-coverage-guided-fuzzing-with-honeybee-and-intel-processor-trace/](https://blog.trailofbits.com/2021/03/19/un-bee-lievable-performance-fast-coverage-guided-fuzzing-with-honeybee-and-intel-processor-trace/) 
* amazon bare metal support intel pt, not available in azure, google cloud?
* not much perf gain if source/compiler instrumented 
* [alex_gaynor] Java uncaught exceptions are being filed as bug-security in oss-fuzz
* [https://bugs.chromium.org/p/oss-fuzz/issues/list?q=Type%3DBug-Security%20exception&can=1](https://bugs.chromium.org/p/oss-fuzz/issues/list?q=Type%3DBug-Security%20exception&can=1) 
* Hasnain(Facebook): e.g. sqlexception can have security implications
* More general question: How much do folks rely on automated tooling for severity assessments vs. manual?
* [AFL++ CL for fuzzing strategies support in ClusterFuzz](https://github.com/google/clusterfuzz/pull/2293/files)

<h3>March 2, 2021</h3>




* (syl) Tom Ritter (Mozilla) [made a big spreadsheet of every browser exploit 2018-present](https://docs.google.com/spreadsheets/d/1FslzTx4b7sKZK4BR-DpO45JZNB1QZF9wuijK3OxBwr0/edit#gid=0) 
* Don’t hesitate to share it internally 
* [tyson] We released a blog post on our browser fuzzing pipline [https://hacks.mozilla.org/2021/02/browser-fuzzing-at-mozilla/](https://hacks.mozilla.org/2021/02/browser-fuzzing-at-mozilla/) 
* [jesse] Working on a patch to our copy of libFuzzer to return instead of exit() (in most cases). [https://phabricator.services.mozilla.com/D106831](https://phabricator.services.mozilla.com/D106831) 
* [metzman] Java/JVM fuzzing with Jazzer
* [https://github.com/CodeIntelligenceTesting/jazzer](https://github.com/CodeIntelligenceTesting/jazzer) 

<h3>February 2, 2021</h3>




* [metzman] afl++ early results in oss-fuzz
* [vanhauser-thc] what would/could be important characteristics for coverage/state collection that are useful for fuzzing?
* [decoder/saelo] Update on Fuzzilli vs. SpiderMonkey bug

<h3>January 19, 2021</h3>




* Marc "van Hauser" Heuse, author of AFL++ will give a quick overview of the current state of afl++, benefits over afl and future plans!
* [decoder] We would like to tackle the runtime allowlist feature at some point this year
* [decoder] Relaying a question on gwp-tsan: Is there more information on it available beyond the LLVM talk? Is it being used already?
* [decoder] Investigating why Fuzzilli is not hitting a rather simple issue in our JS engine - could be related to coverage (general note: coverage might also make things worse, still investigating the details on this one).
* [saelo] Wrote up [How Fuzzilli Works](https://docs.google.com/document/d/1GEAq8gubYnPk177ZPBHZCO-AyzyuX1yxnt7Rv6QWfaA/edit?usp=sharing&resourcekey=0-r0v_M3_20GLXKdjUms7pQA) (might need to request access). Feedback welcome!
* [aarya] Talk about bug based benchmarking issues
* [Alex_Gaynor] regular expressions and other interpreter-shaped libraries
* State based coverage
* [https://www.syssec.ruhr-uni-bochum.de/media/emma/veroeffentlichungen/2020/02/27/IJON-Oakland20.pdf](https://www.syssec.ruhr-uni-bochum.de/media/emma/veroeffentlichungen/2020/02/27/IJON-Oakland20.pdf) 

<h3>December 1st, 2020</h3>




* [Andrei, Everest] - From FuzzBuzz - Creating a common fuzzing education / training platform.
* Fuzzing discourse existing  - invitation in the chat
* [ipudney] - Python fuzzing with Atheris - [https://github.com/google/atheris](https://github.com/google/atheris), OSS-Fuzz example - [ujson](https://github.com/google/oss-fuzz/tree/master/projects/ujson), OSS-Fuzz [documentation](https://google.github.io/oss-fuzz/getting-started/new-project-guide/python-lang/) [some hacks around disabling leaks, LD_PRELOAD].
* [decoder] gwp-asan still being used? Current status/success?
* One of the biggest success 
* [Alex_Gaynor] how useful are folks finding fuzzing efforts on memory-safe languages (python, go, safe rust, etc.)?
* Hasnain - E.g. find file not found, subprocess exceptions to catch RCEs

<h3>November 10th, 2020</h3>




* (sylvestre) Would it be possible to reschedule this meeting earlier for European? (Decoder and myself). It is currently from 10 to 11pm
* Switched to 10.30AM PST.
* [decoder] (just fyi) Collaborating with 5ael0 on extending Fuzzilli to do differential testing
* [metzman] [AArch64 cross-compilation in OSS-Fuzz?](https://github.com/google/oss-fuzz/pull/4591)/Usefulness of ARM generally?
* Mozilla’s main usecase for ARM is for JavaScript/WebAssembly
* [decoder] We use AWS c6g.* instances (Graviton 2)
* Alex says not much ARM specific code in his projects.
* ARM vms on AWS are much cheaper than x86.
* [metzman] 5-day long Halloween experiment in FuzzBench - [https://www.fuzzbench.com/reports/2020-10-31-hlwn-long/index.html](https://www.fuzzbench.com/reports/2020-10-31-hlwn-long/index.html) (error before finish, but coverage graphs are usable).
* [aarya] [Security scorecards for open source software launched](https://opensource.googleblog.com/2020/11/security-scorecards-for-open-source.html). What metrics would you like to see?
* People (e.g. Cornellius) think Symcc is interesting to explore. 
* [decoder] connect with startup on libFuzzer for java.

<h3>October 6th, 2020</h3>




* [aarya] MS OneFuzz <-> OSS-Fuzz integration hooks ?
* [aarya] What are your critical OSS dependencies ? Any thoughts on how you define critical OSS ? Share some stats generated with github api - [here](https://docs.google.com/spreadsheets/d/1YWGhKggO43IVtfxjRlO_pF7RZIP4o1eZeonnPfSYvJs/edit#gid=0).
* MS and FB folks with check with their OSS depts and see if such a list can be shared.
* fyi, entropic is now default in libfuzzer - [https://reviews.llvm.org/D87476](https://reviews.llvm.org/D87476) 
* [Alex_Gaynor] How do we promote sanitizers more in college courses, many of which still use valgrind for teaching students?
* [Max] Microsoft might push it through their student programs / university relationships.
* [Alex_Gaynor] noticed some OSS-Fuzz bugs mention they originate with autofuzz. Can you say more about how autofuzz is approaching OSS projects (using upstream targets, same engines as OSS-Fuzz, etc.)?
* Mystery. Bug example: [https://bugs.chromium.org/p/oss-fuzz/issues/detail?id=26148](https://bugs.chromium.org/p/oss-fuzz/issues/detail?id=26148)
* Generalization
* machine readable outputs as per Brian
* fuzzing engines hooks, no need to know libfuzzer vs afl. (from Hasnain)
* crashes and json are sufficient (as per Hasnain)
* deduplication detached from infras (abhishek)
* which input caused which coverage
* better crash reports from all tools, down to where bug happened (Mike)
* Fuzzer benchmarking
* Ensemble fuzzing - e.g. [https://github.com/google/fuzzbench/pull/159](https://meet.google.com/linkredirect?authuser=0&dest=https%3A%2F%2Fgithub.com%2Fgoogle%2Ffuzzbench%2Fpull%2F159) - maybe we should bring it back as a fuzzer (for [core fuzzers](https://github.com/google/fuzzbench/blob/master/service/core-fuzzers.yaml))
* Differential coverage - see “Unique coverage plots” and “Coverage reports for each fuzzer on this benchmark” in [https://www.fuzzbench.com/reports/2020-09-28/index.html](https://www.fuzzbench.com/reports/2020-09-28/index.html)
* [Related work](https://www.syssec.ruhr-uni-bochum.de/media/emma/veroeffentlichungen/2020/09/22/ACSAC20-CollabFuzz.pdf)

<h3>September 1, 2020</h3>




* <add your agenda items here>
* [mascasa] Talk about recent libFuzzer/entropic improvements - [context](https://www.fuzzbench.com/reports/2020-08-30/index.html)
* [metzman] What is after [https://www.microsoft.com/en-us/security-risk-detection/](https://www.microsoft.com/en-us/security-risk-detection/)
* [decoder] js_fuzzer ideas
* Can we separate test preprocessing / dependencies from the fuzzer?
* We should try a persistent test execution approach with js_fuzzer
* [aarya] [OpenSSF](https://openssf.org/) and the need for participation in the security tool working group (needs company level signup).
* [Alex_Gaynor] expected that it’s no longer possible to compile libFuzzer just from the .cc files in that directory/build.sh? ([https://github.com/rust-fuzz/libfuzzer/issues/65](https://github.com/rust-fuzz/libfuzzer/issues/65))

<h3>August 4, 2020 - cancelled</h3>




* [decoder, not here for the meeting] We have upgraded libFuzzer to the latest version and are running with entropic on one target to see if the coverage increases noticeably. We will most likely switch all targets in our infrastructure to entropic afterwards.

<h3>July 14, 2020</h3>




* [Alex_Gaynor (will be late to meeting)] It looks like the new libFuzzer logic + HonggFuzz is finding quite a few vulnerabilities that _years_ of previous libFuzzer+AFL fuzzing didn’t find in ImageMagick!
* [https://oss-fuzz.com/testcase-detail/5716327751483392](https://oss-fuzz.com/testcase-detail/5716327751483392)
* [https://oss-fuzz.com/testcase-detail/5639044129357824](https://oss-fuzz.com/testcase-detail/5639044129357824)
* [https://oss-fuzz.com/testcase-detail/5736942228733952](https://oss-fuzz.com/testcase-detail/5736942228733952)
* [decoder] libFuzzer proposal for better usage of compile-time information
* [aarya] Question for Hasnain - Are you doing any CI fuzzing ?
* [Alex_Gaynor] metrics for whether fuzzing of memory-safe languages (Go, Rust) is as useful as fuzzing C/C++?

<h3>June 2, 2020</h3>




* [mhl] Is there an API to access oss-fuzz issues?
* [https://github.com/google/oss-fuzz/issues/3925](https://github.com/google/oss-fuzz/issues/3925)
* [Alex_Gaynor] Better tooling to identify info-leaks with MSAN?
* From kcc@: 
* __msan_test_shadow() from <sanitizer/msan_interface.h>
* [https://github.com/llvm/llvm-project/blob/master/compiler-rt/include/sanitizer/msan_interface.h](https://github.com/llvm/llvm-project/blob/master/compiler-rt/include/sanitizer/msan_interface.h)
* [Alex_Gaynor] Not fuzzing, but if we have time I’m curious how the Chromium Rust experiments are going?

<h3>April 7, 2019</h3>




* [decoder] Random libFuzzer questions 
* [tyson] ARM64 fuzzing on oss-fuzz? Any updates?
* Probably Q3, starting with QEMU, helps with bug reproduction for devs
* [mhl] ASAN stack-traces when dereferencing a null pointer
* [aarya] two fuzzing engines updates public mailing lists - [fuzzing-discuss@googlegroups.com](mailto:fuzzing-discuss@googlegroups.com) and [fuzzbench-users@googlegroups.com](mailto:fuzzbench-users@googlegroups.com) 

<h3>March 17, 2019</h3>




* [metzman] FuzzBench demo, discuss key results.
* [mpherman] Fuzzing strategies effectiveness in finding new bugs.
* [jkratzer] Explanation of benefits of metzmans work on “Fuzzing Native Code in Web Browsers using WASM”?

<h3>February 4, 2019</h3>




* [decoder] Deploying TSan in CI at Mozilla (quick summary)
* [decoder] Does TSan work on Android?
* [mbarbella] How is Peach used at Mozilla? Have you tried combining it with libFuzzer/AFL/anything else?
* Abandoned at Mozilla (Christoph). Not used for years anywhere. Peach community is unmaintained, since most code is ported to C#.
* ANTLR is a better choice (Christian), esp context-free grammar.
* [jkratzer] Old peach pits - [http://www.flinkd.org/projects/peach-pits/](http://www.flinkd.org/projects/peach-pits/)
* [mbarbella/mpherman] Radamsa custom mutator for use in libFuzzer.
* In-process custom mutator that can be run in libFuzzer are available.

<h3>December 10, 2019</h3>




* Welcome [mkrzywicki@apple.com](mailto:mkrzywicki@apple.com)
* [metzman] - present fuzzer benchmarks UI, get feedback on requirements

<h3>November 5, 2019</h3>




* [tsmith] Checkout Pernosco 
* Paid service that provides web session to rr traces
* Potentially integrate into oss-fuzz? But also useful elsewhere.
* We have started providing Pernosco sessions for fuzzing bugs to devs
* Demo video: [https://www.youtube.com/watch?v=LR0pms_mQuY](https://www.youtube.com/watch?v=LR0pms_mQuY)
* Not-yet-public documentation: [https://pernos.co/do_not_tweet](https://pernos.co/do_not_tweet)
* Info is being previewed via twitter @_pernosco_
* [gkw] rr as-is needs to be rewritten for macos, aka no macos support now:
* [https://github.com/mozilla/rr/issues/2335#issuecomment-475128041](https://github.com/mozilla/rr/issues/2335#issuecomment-475128041) 
* [aarya] Do people care about other languages to fuzz - Go, Java, Python ?
* [aarya] Which ubsan flags do you enable ? 
* [tsmith] Firefox ASan + UBSan builds enable bool, bounds and vla-bound atm.
* Object-size, pointer-overflow and shift are inbound
* Null, nonnull-attribute are likely next
* [aarya] Has anyone tried other fuzzing engines like Redqueen, Angora ? Results?
* [kcc] we’ve implemented asan option max_allocation_size_mb, please try. 
* [metzman] Mozilla’s Skia replacement
* No clue
* [kcc] any interest in HWASAN on Android? 
* On device only (not emulator), only recent kernels (Pixel 2 or higher).
* [kcc] auto-init?
* [https://bugzilla.mozilla.org/show_bug.cgi?id=1514965](https://bugzilla.mozilla.org/show_bug.cgi?id=1514965) 
* Please add agenda items...

<h3>October 1, 2019</h3>




* [JNorm] Overview and Demo of TKOFuzz 
* [decoder] ASan stack unwinding bug reported upstream [https://bugs.llvm.org/show_bug.cgi?id=43339](https://bugs.llvm.org/show_bug.cgi?id=43339)
* [decoder] ASan + Rust, eyes/comment on [https://github.com/rust-lang/rust/issues/64629](https://github.com/rust-lang/rust/issues/64629) appreciated
* [syl] PHC - Implemented on the Windows, Linux & Mac [https://bugzilla.mozilla.org/show_bug.cgi?id=1523268](https://bugzilla.mozilla.org/show_bug.cgi?id=1523268) 
* Enable on most platforms for fx nightly 
* [aarya] New OSS-Fuzz features - Golang support, X86 support, FDP.

<h3>September 10, 2019</h3>




* [kcc] any updates from Mozilla’s gwp-asan (PHC)? 
* Chrome has 54 reports, 34 fixed. 
* Several bugs are in the MacOS platform code (reported to Apple)
* [decoder] No updates yet, we are still figuring out what parameters to modify in our current setup (e.g. number of slots, lifetime, etc).
* [aarya] AFL contributions
* [decoder] Discussion about adding allocation size limits to ASan
* [decoder] libFuzzer stability patch
* Revert of Google’s attempt to do that: [https://reviews.llvm.org/D56730](https://reviews.llvm.org/D56730)
* [decoder] Whitelist in libFuzzer possible similar to focus function?
* [decoder] Blog post about Angora coming from CISPA
* [tsmith] oss-fuzz disclosure date on bugs

<h3>August 20, 2019</h3>




* AFL is now hosted on GitHub - [https://github.com/google/afl](https://github.com/google/afl)
* (decoder) Discussion about libFuzzer OOM handling (see email)
* FIle an issue at [https://github.com/google/sanitizers/issues](https://github.com/google/sanitizers/issues), Kostya’s team will reply.
* (decoder) libFuzzer + wasm-builder (canceled)
* (decoder) PHC (our version of gwp-asan) landed on Linux and Windows
* GWP-ASan status in Chrome: mostly UI interaction required UAFs, bugs that require a specific configuration (whether a host or being a member of a new experiment), timing dependent (e.g. network conditions) UAFs.
* (decoder) libFuzzer focus_function question
* Dfsan build and use it automatically:
* Design doc / tracking issue: [https://github.com/google/oss-fuzz/issues/1632](https://github.com/google/oss-fuzz/issues/1632)
* Enabling it on CF: [https://github.com/google/clusterfuzz/issues/503](https://github.com/google/clusterfuzz/issues/503)
* Max: not even sure how it will work without an auxiliary DFSan build. Probably  will prioritize the units that reach the given function, but with DFSan it focuses mutations on certain bytes and that is expected to be quite efficient.
* (al, abhishek) OSS-Fuzz vendor policy for third party bugs (see [this](https://github.com/google/oss-fuzz/pull/2703#issuecomment-521769772))
* For now we will add a vendor field
* basically the same as auto_cc
* [https://github.com/google/clusterfuzz/pull/869](https://github.com/google/clusterfuzz/pull/869) 
* Considered a vendor list to delegate bug sharing
* Considered some feature for early sharing of existence of bugs and fix.	
* (tyson) Default ASAN_OPTIONS on Android (log_path=’...’ does not seem to work)
* Start an email or file an issue: [https://github.com/google/sanitizers/issues](https://github.com/google/sanitizers/issues)
* [https://github.com/google/sanitizers/issues/1135](https://github.com/google/sanitizers/issues/1135)
* (metzman) virgo updates? 
* posidron: Currently cancelled

<h3>June 11, 2019</h3>




* (decoder) Demo of CovManager (Managing Fuzzing Coverage)
* (decoder) libFuzzer + wasm-builder (canceled)
* (adetaylor, aarya) Rust usage, success stories, how to convince devs to convert, how did you prioritize areas to convert ?

<h3>May 7, 2019</h3>




* Kcc would like to hear an update on asan nightly (very curious!) 
* aarya@: how do you prioritize new fuzzer writing ? Do you focus on items that can add big w.r.t coverage or only more privileged code ? Need to know past experience in this, how many fuzz targets you have now ?
* (decoder) wasm fuzzing with libfuzzer
* Missed [Bug 1545086](https://bugzilla.mozilla.org/show_bug.cgi?id=1545086)
* Kcc: reproduced, investigating

<h3>April 2, 2019</h3>




* [alex] Lots of JIT bugs at pwn2own! (Don’t have a particularly thing to talk about, just an observation)

<h3>March 12, 2019</h3>




* [aarya]: have folks looked at open-sourced ClusterFuzz code, any questions / feature requests, ways to cross-collaborate ?
* [alex] support for other bug trackers? - Github, bugzilla, ….
* [alex] GWP-ASAN status? (I’ve had two non-Mozilla bugs in the last few weeks where a production-ready sampling debug allocator with stack-trace recording would have been **_hugely_** helpful, so I’m starting to want this to become a generally popular idea)
* [mmoroz]: Last time promised to give an update on ML RNN usefulness in ClusterFuzz ([code](https://github.com/google/clusterfuzz/tree/master/src/python/bot/fuzzers/ml/rnn)).

<h3>February 5, 2019</h3>




* [aarya, metzman]: Some x86 libfuzzer fuzzing results from Chromium, what is needed for OSS-Fuzz?
* Mozilla has same experience on x86
* Limited memory space means less recursion and other things
* Less registers
* 
* [posidron] @JonathanNorman: Can you talk a bit about the "Distributed Fuzzing Framework" (DFF) made by David Conger? Like, is it still in use or part of SAGE / main obstacles / architecture. I never found much public info about it. 
* [jnorm]  DFF is like 11 years old :) it died not long after the public stuff not sure why but i can detail what is floating around MS today
* [alex] “the Bugs-- team incorporated Machine Learning in ClusterFuzz infrastructure using[ RNN model](https://en.wikipedia.org/wiki/Recurrent_neural_network) to improve upon corpus quality and code coverage” can you say more about this? Is it happening for OSS-Fuzz automatically?
* [metzman] GPU bugs. Many seem to be found through canvas on our end. Can we use mozilla’s framboise fuzzer for WebGL they gave us.
* [posidron] The WebGL and Canvas modules in Framboise are kinda obsolete but yes, you can build up on that Shader generator I shared, it was not really part of Framboise but an independent module. Though, it is a few years old and will generate only V/F shader code. I can share the WebGL/Canvas modules if interested.
* [kcc] asking feedback on [https://github.com/google/fuzzer-test-suite/blob/master/tutorial/structure-aware-fuzzing.md](https://github.com/google/fuzzer-test-suite/blob/master/tutorial/structure-aware-fuzzing.md), and maybe let’s find some way to collaborate 
* [alex] I wonder how hard it’d be to generate protobufs for our entire IPC schema…
* [kcc] an alternative is to implement a specialized mutator for that schema 
* [decoder] We can probably port the Python bridge code from our AFL fork to allow modules to be written in Python instead ([code](https://github.com/choller/afl/blob/master/afl-fuzz.c#L397), [docs](https://github.com/choller/afl/blob/master/docs/mozilla/python_modules.txt))
* AFLSmart: [https://github.com/aflsmart/aflsmart](https://github.com/aflsmart/aflsmart), paper: [https://arxiv.org/abs/1811.09447](https://arxiv.org/abs/1811.09447)
* [LibFuzzer Interface](https://github.com/llvm-mirror/compiler-rt/blob/master/lib/fuzzer/FuzzerInterface.h#L54) for Custom Mutators
* 
* [alex] How is GWP-ASAN going?

<h3>October 9, 2018</h3>


<h3>Discussion items:</h3>




* [tyson] Enabling UBSan ‘bounds’ check causes a SIGILL when triggering a forced crash by writing to NULL: [https://bugzilla.mozilla.org/show_bug.cgi?id=1494207](https://bugzilla.mozilla.org/show_bug.cgi?id=1494207)
* [https://godbolt.org/](https://godbolt.org/) Useful to observe the issue
* Somewhat relevant Issue we had on OSS-Fuzz: [https://github.com/google/oss-fuzz/pull/573#issuecomment-300466442](https://github.com/google/oss-fuzz/pull/573#issuecomment-300466442), ended up using `array-bounds` check only
* [aarya] Did anyone explore static analysis tools like Clang Static Analyzer, Semmle.
* Coverity used extensively at Mozilla.
* Clang plugins - Anthony Jones, Engineering Lead, Mozilla
* Semmle - unsafe enum cohersion across ipcs. Couple of hours to write one. Data analysis portion is way more sophisticated.
* Static Analysis keyword, look for meta bug.
* Coverity [https://bugzilla.mozilla.org/show_bug.cgi?id=1230156](https://bugzilla.mozilla.org/show_bug.cgi?id=1230156)
* Meta static analysis [https://bugzilla.mozilla.org/show_bug.cgi?id=1287757](https://bugzilla.mozilla.org/show_bug.cgi?id=1287757)
* Semmle https://bugzilla.mozilla.org/show_bug.cgi?id=1458117
* Christian idea - combine static with dynamic.
* [https://blogs.technet.microsoft.com/srd/2018/08/16/vulnerability-hunting-with-semmle-ql-part-1/](https://blogs.technet.microsoft.com/srd/2018/08/16/vulnerability-hunting-with-semmle-ql-part-1/) 
* [aarya] Try libfuzzer on Windows [thanks to Jonathan :)]
* [mmoroz] Memory sampling in regular nightly builds? Did you try? (Was suggested by kcc@ on July 24th).
* Requires allocator changes that need to be done by another team :)
* Can try to re-use a shim for the system malloc (will be landed soon in Chromium)
* [decoder] Hack2Win Exploits for Firefox
* 2 JS tests, long time bugs. One bug is just 6 lines, really old bugs.
* Cc [ochang@chromium.org](mailto:ochang@chromium.org), [inferno@chromium.org](mailto:inferno@chromium.org) 
* Info leak: [https://blogs.securiteam.com/index.php/archives/3766](https://blogs.securiteam.com/index.php/archives/3766) 
* Chrome fuzzer program - [https://www.google.com/about/appsecurity/chrome-rewards/#fuzzerprogram](https://www.google.com/about/appsecurity/chrome-rewards/#fuzzerprogram)
* [mmoroz] Hack2Win Exploit for Chrome (bugs are still private)
* Renderer RCE: [https://bugs.chromium.org/p/chromium/issues/detail?id=888923](https://bugs.chromium.org/p/chromium/issues/detail?id=888923)
* Sanbox escape: [https://bugs.chromium.org/p/chromium/issues/detail?id=888926](https://bugs.chromium.org/p/chromium/issues/detail?id=888926)
* [aarya] What are your fuzzing priorities ? What do you find most interesting atm ?
* Fuzzing with x86 emulator is working great.
* UBSan integration: [https://bugzilla.mozilla.org/show_bug.cgi?id=1474488](https://bugzilla.mozilla.org/show_bug.cgi?id=1474488)
* Coverage works nicely. 
* Weekly aggregate
* Diffs across files level, not file content. See directory dropped.
* Statistics.
* Demo in next meeting.

<h3>September 4, 2018</h3>


<h3>Discussion items:</h3>




* [alex] IPC fuzzing? It’s mentioned in the latest Chrome security quarterly, would be interesting to trade notes
* [al] Any questions for Google based on Mozilla’s recent work getting our fuzzing up on Android?
* [tyson] 32-bit build fuzzing - any developments?
* Does Docker run as 32-bit?
* Not officially but you can [build](https://dzone.com/articles/docker-daemon-for-32-bit-architecture) by yourself.
* Or use built 32 bit [images](https://github.com/docker-32bit/).
* Compilation questions.
* Firefox build in oss-fuzz (and Pdksnk as a phenomena)
* Christian is examining the issues that are coming up and requests from Pdksnk
* Pdksnk is adding things to oss-fuzz from Mozilla code
* Should only need access to one directory under /dev/shm, not the whole thing: [https://searchfox.org/mozilla-central/source/security/sandbox/linux/broker/SandboxBrokerPolicyFactory.cpp#530](https://searchfox.org/mozilla-central/source/security/sandbox/linux/broker/SandboxBrokerPolicyFactory.cpp#530) (in case blocking /dev/shm is for sandboxing reasons?)
* [christian] ASAN Nightly update to Google

<h3>July 24, 2018</h3>


<h3>Discussion items:</h3>




* How successful are ASan builds pushed to users? Any cool bugs reported so far? (Max)
* Blog post for reference: [https://blog.mozilla.org/security/2018/07/19/introducing-the-asan-nightly-project/](https://blog.mozilla.org/security/2018/07/19/introducing-the-asan-nightly-project/)
* [Bug 1386297](https://bugzilla.mozilla.org/show_bug.cgi?id=1386297) - AddressSanitizer Nightly Project
* Windows Build
* Disable stack instrumentation to unblock frequent crasher for now(?)
* ASan Win64 common crasher -  [https://bugs.chromium.org/p/chromium/issues/detail?id=783296](https://bugs.chromium.org/p/chromium/issues/detail?id=783296) 
* Try electric fence + ASan? (kcc)
* Add memory sampling to regular nightly builds? (kcc)
* Recommendations for making ASan perform better (memory-wise) in the Nightly situation (e.g. settings, other ideas?) (decoder)
* kcc@: ASan’s memory usage sucks, and is going to suck no matter what. You can reduce it at the expense of worsening the bug detection (e.g. reducing quarantine and redzones). HWASAN (memory tagging) should be much better.  Does mozilla have any communication channels with Intel, AMD, and/or ARM to request [memory tagging](https://arxiv.org/pdf/1802.09517.pdf) support? 
* kcc@: try to understand where the RAM is used. In some cases lots of RAM is spent for storing stack traces, this can be tuned with ASAN_OPTIONS=malloc_context_size=<SMALL_VALUE>
* kcc@: are you using fresh LLVM? We’ve made some improvements in the ASan allocator this year (not all possible improvements, but still)
* 32-bit fuzzing on oss-fuzz are there any plans to encourage it? (Tyson)
* Oliver - there may be a bug open already
* Building is not supported by docker images
* [https://github.com/google/oss-fuzz/issues/643](https://github.com/google/oss-fuzz/issues/643) 
* Targets
* aom
* Brotli
* expat
* FreeType
* FFmpeg
* Harfbuzz
* icu
* Libjpeg-turbo
* Libpng
* opus
* ots
* nss
* qcms
* Skia
* Speex
* SQLite
* Vorbis
* woff2
* Any recommended UBSan flags to add to default ASan+UBSan build (Tyson)
* Overall goal is to add UBSan flags overtime
* Initially add flags that find potential security issues that do not create a lot of extra noise (signed-integer overflow for example)
* bool, bounds and vla-bound are the first set we plan to add
* [https://github.com/google/oss-fuzz/blob/master/infra/base-images/base-builder/Dockerfile#L25](https://github.com/google/oss-fuzz/blob/master/infra/base-images/base-builder/Dockerfile#L25) 
* [oss-fuzz firefox](https://github.com/google/oss-fuzz/pull/1546) status?
* @alexgaynor to review and approve.

<h3>June 5, 2018</h3>


<h3>Discussion items:</h3>




* oss-fuzz firefox native fuzzing interface integration
* **[Bug 1466021](https://bugzilla.mozilla.org/show_bug.cgi?id=1466021)** - oss-fuzz firefox native fuzzing interface integration
* **firefox micro-targets #1462**: [https://github.com/google/oss-fuzz/issues/1462](https://github.com/google/oss-fuzz/issues/1462)
* _Suggestion_: Use Mozilla’s own fuzzing builds pulled via fuzzfetch?
* Modify fuzzfetch to have an option to rename builds (Tyson)
* [https://github.com/MozillaSecurity/fuzzos/blob/master/images/libfuzzer/](https://github.com/MozillaSecurity/fuzzos/blob/master/images/libfuzzer/)
* Add stub binary which re-execs firefox with the right env vars. Compiled one of these for each libFuzzer target we want. [https://github.com/google/oss-fuzz/issues/1462#issuecomment-394852119](https://github.com/google/oss-fuzz/issues/1462#issuecomment-394852119) Maybe Google could build it?
* Fuzzing at scale on different platforms
* Android work is upcoming for Mozilla fuzzing team, tip, tricks and pitfalls would be great
* Windows & OSX (have we talked about this?) Any way to decrease or avoid cost with Windows VMs?
* Notes:
* Android:
* Google does Chrome fuzzing on Android. Does **not** have LibFuzzer targets.
* Google uses Google Compute (?) Android x86 images. Does not use the Android emulator.
* ASan is available for Android. Android Security team uses this.
* Windows:
* Nothing unusual here. Costs are focused around licensing, etc.
* Can we re-use our enterprise license on ec2 to help with cost?
* Mac
* Running on Mac servers with VMs of OS X on top of it
* WebAssembly fuzzing - libFuzzer or traditional fuzzers ?
* Benjamin Bouvier wrote one wasm-focused fuzzer with its own harness
* Harness can be run standalone
* [bbouvier@mozilla.com](mailto:bbouvier@mozilla.com)
* Rolled onto langfuzz
* Packet.net arm64 hardware

<h3>April 3, 2018</h3>


<h3>Questions for Google</h3>




* [decoder] LibFuzzer Enhancements
* LibFuzzer strategy when finding new PC
* libFuzzer is biased towards recently discovered inputs, but may be bias is not strong enough
* On-the-fly corpus reduce (self-merge) while running (implemented in our harness)
* ClusterFuzz / OSS-Fuzz runs fuzzing sessions no longer than 1hr each

<h3>Questions for Mozilla</h3>




* Fuzzing over websockets?
* Is not being maintained anymore and likely is not used
* Framboise: [https://github.com/MozillaSecurity/framboise](https://github.com/MozillaSecurity/framboise) - uses the websockets code
* Traditional fuzzers:
* Grizzly-based fuzzers should be a relatively small effort to run against other browsers
* Please contribute the pwn2own fuzz target to [https://github.com/google/fuzzer-test-suite](https://github.com/google/fuzzer-test-suite) (when the buggy input can be made public) 

<h3>Area for Potential Collaboration</h3>




1. Corpus for fuzzing from Commoncrawl.org ?
2. Sharing Grizzly harness and ffpuppet to make Chrome puppet? 
1. To improve OSS-Fuzz?
3. Evaluate value profile for corpus, monitor growth.
4. libFuzzing fuzzing for larger targets (not just mozilla, but also for chrome).
2. Ask for Mozilla to get a “juicy target” for OSS-Fuzz using LibFuzzer added in Q2.
5. Partial coverage for large targets, might need more research / experiments
6. 


---

<h3>March 1, 2018</h3>


<h3>Questions for Google</h3>




* It would be nice to know if they do any fuzzing on Windows & OSX and how they scale it? (rforbes)
* Plans to improve support for fuzzing large targets with LibFuzzer (decoder)
* How crash resilient / stable is the new Mojo implementation against fuzzing, especially with the integrated message validation? (posidron)

Questions to Mozilla



* Kcc would like to hear Mozilla’s feedback on the “memory tagging” whitepaper [https://arxiv.org/pdf/1802.09517.pdf](https://arxiv.org/pdf/1802.09517.pdf). Tl;DR: This is low-overhead always-on asan-in-hardware. We need to jointly push the major hardware vendors to implement it (currently, this is available on SPARC only)


---

<h3>Mozilla Tools Overview</h3>


The following is an overview of the tools in use by Mozilla’s fuzzing team

<h4>General Purpose Harness & Tools</h4>


[FFpuppet](https://github.com/MozillaSecurity/ffpuppet): A Python module that aids in the automation of Firefox at the process level

[Grizzly](https://github.com/MozillaSecurity/grizzly):  A general purpose browser harness primarily used to target Firefox

_*** All fuzzers targeting Firefox at this time leverage both FFpuppet and Grizzly_

<h4>Grammar Generators/Mutators</h4>


[Avalanche](https://github.com/MozillaSecurity/avalanche): Avalanche is a document generator which uses context-free grammars to generate randomized outputs for fuzz-testing



* Available Grammars: HTML, CSS, SVG, MathML, XSLT, Canvas, WebGL(2), WebAnimations

[LangFuzz](https://github.com/MozillaSecurity/LangFuzz): Grammar-based compiler/interpreter fuzzing code in Java



* Primarily used to target JavaScript via JSShell

FuzzIDL: An abstraction layer for converting WebIDLs into a grammar



* Targets DOM accessible objects and attributes

<h4>Fuzzing Frameworks</h4>


[FunFuzz](https://github.com/MozillaSecurity/funfuzz/): A general purpose JavaScript engine fuzzer

Domino: A general purpose DOM/WebAPI fuzzer (successor to DOMFuzz)



* Currently covers about 80% of WebIDL
* Support for most WebAPIs (WebGL, WebRTC, WebCrypto, WebAudio, WebPayment, WebAuth, etc)

<h4>Additional Fuzzers</h4>




* [Faulty](https://bugzilla.mozilla.org/show_bug.cgi?id=fuzzing-ipc-ipdl): IPC Fuzzer (IPC, Shmem, MsgMgr)

<h4>Misc. Tools</h4>




* [Octo](https://github.com/MozillaSecurity/octo): A shared fuzzing library in JS
* [Lithium](https://github.com/MozillaSecurity/lithium/): General purpose testcase reducer
* [Grizzly.reduce](https://github.com/MozillaSecurity/grizzly): An automated testcase verifier/reducer built on Lithium
* CrashExplorer: A testcase mutator

<h4>3rd Party Tools</h4>




* AFL, LibFuzzer, Domato, Radamsa

<h3>Fuzzing Infrastructure at Mozilla</h3>


Custom AWS infrastructure making use of spot instances managed by the [FuzzManager](https://github.com/MozillaSecurity/FuzzManager) command and control software, which collects data from fuzzers running in instances and bucketizes crashes.

FuzzManager is comprised of multiple modules:

<h4>CrashManager</h4>


This module is responsible for receiving all fuzzing results, both from machines managed by FuzzManager itself (by another module) and machines configured statically. It features a library (shared between its client and server) that features multiple frontends to process crash data from different sources (e.g. GDB traces, ASan output, Minidump traces, etc.). Crash data is translated into an internal representation and can be matched by arbitrary [Crash Signatures](https://wiki.mozilla.org/Security/CrashSignatures) written in JSON. These signatures are used to bucket multiple crashes that are considered duplicates. The module also features server-side logic to semi-automatically optimize (broaden) signatures in an intelligent way to capture variations in duplicates without overzealously matching unrelated crashes. Another, similar feature is similarity search between an unbucketed crash and existing signatures. Once a bucket is created, the system has the ability to file a bug in a configured bug tracking system or allows the user to simply link a bucket to an existing issue. The system also tracks the state of each linked bug (e.g. fixes and duplicate markings on bugs) and acts accordingly. It also features a rich REST API and a client library for automating tasks around downloading existing crashes/tests for further processing and (re)submitting them. Signatures can also be downloaded to perform local matching before submitting to reduce the server load in case of frequent issues (each client can see if an issue is marked as frequent or what the best testcase currently known to the system is and decide about submitting based on this information).

<h4>EC2SpotManager</h4>


The purpose of this module is to schedule EC2 spot instances on AWS according to preconfigured pools. Each pool is a set of machines responsible for fuzzing with a certain configuration. Pool configurations are hierarchical and feature inheritance to avoid duplication. The system starts the machines for each pool, monitors their state (if necessary, adds more machines if others have been terminated) and restarts machines based on configured intervals. It also chooses the best zone allocation based on configured regions and their current prices. 

Internally, the module uses [Laniakea](https://github.com/MozillaSecurity/laniakea/tree/cloudbridges/laniakea) on top of Boto to interact with AWS EC2.

<h4>CovManager</h4>


The latest addition to FuzzManager is this module for receiving code coverage information. On the client side, we post-process the output of [grcov](https://github.com/marco-c/grcov), a tool that can work with gcc or clang gcov output. Our storage format is a tree-based structure holding line coverage information per file and  therefore allows easy and fast displaying of sub-directory coverage. Source code for viewing the line-based information is fetched automatically from the associated repository. We also prototyped experimental features such as detecting if a security patch from a bug has coverage according to the data in the system.

<h4>Misc</h4>


FuzzManager also contains some misc helper scripts, including a [new harness](https://github.com/MozillaSecurity/FuzzManager/tree/master/misc/afl-libfuzzer) to run LibFuzzer and AFL and submit their results back to the server. For both tools, the queue is also synchronized to AWS S3 and merged back into a new corpus by a build server periodically. For LibFuzzer, we also implemented direct S3 queue sharing, so several machines directly share their new coverage findings.

<h4>[Laniakea](https://github.com/MozillaSecurity/laniakea/tree/cloudbridges/)</h4>


It's utility for spawning a cluster and managing instances at cloud providers. At the moment we have support for EC2 but we added now interfaces to support multiple cloud providers and are working on a module for Microsoft Azure to support more fuzzing on Windows.

<h4>[FuzzOS](https://github.com/MozillaSecurity/fuzzos)</h4>


This project is in development and in a private repository. The aim is minimizing set-up time of fuzzing environments and run these environments anywhere instantly. There is no dependency to the cloud provider we are going to use. This is mainly important for the build servers where TaskCluster is running. There where we want to run fuzzers after the builds jobs of our core products are finished. The thousands of hours of IDLE time which gets accumulated in a month, can be used for fuzzing but at zero costs for the fuzzing team. The infra-structure is similar OSS-Fuzz.

<h3>Planned Future Fuzzers</h3>




* ArbitrageFuzzing - Using IDLE time of spot instances in TaskCluster for fuzzing.

<h3>Other Projects</h3>




* Unified Fuzzing Interface (for LibFuzzer and AFL) in mozilla-central
* Partial instrumentation and Python support for AFL (see [docs](https://github.com/choller/afl/tree/master/docs/mozilla) in fork)
* ASan Nightly Project


---

<h3>Google Tools Overview</h3>


<h4><span style="text-decoration:underline;">OSS-Fuzz</span></h4>


For fuzzing open-source projects. Github repo is the place for project submissions, filing issues with infrastructure, etc. Repo hosts [scripts](https://github.com/google/oss-fuzz/blob/master/infra/helper.py) for reproducing any crash locally. Repo also hosts all the scripts that build every project in different sanitizer configs (asan, msan, [some features](https://github.com/google/oss-fuzz/issues/232) of ubsan without false positives) and fuzzing engine configs (afl, libfuzzer; honggfuzz not supported yet).

ClusterFuzz backend code is still all in internal codebase. We want to open-source it, only issue we see here is it it is very closely tied to Google technologies - Google Appengine, GCS storage, Google Compute Engine, etc.

<h4><span style="text-decoration:underline;">ClusterFuzz</span></h4>


See [https://github.com/google/oss-fuzz/blob/master/docs/clusterfuzz.md](https://github.com/google/oss-fuzz/blob/master/docs/clusterfuzz.md) for description and UI examples on various parts of ClusterFuzz. A lot of work has went recently on generating fuzzer statistics, performance analyzer tables and performance visualizations by timeseries (numerous problems indicator like bad instrumentation, startup crash, corpus crash, timeout, oom, excessive logging, slow units, etc). Currently, we are working to deprecate sanitizer coverage in favor of clang source based code coverage (has full block highlighting, frequency hit counts, correctness in cases of compiler optimizations).

<h4><span style="text-decoration:underline;">JS Fuzzer</span></h4>


Closed source fuzzer, plan to open source it sometime. This fuzzer is running on OSS-Fuzz on all JS engines. We include most JS tests from different JS engines as corpus. It is very productive since it is able to understand grammar and generate mutations in an error resilient way. It converts JS to AST using Babel framework and then does easy mutations at json level. Then it uses babel again to convert that AST json back to JS.

<h4><span style="text-decoration:underline;">MSAN instrumented libraries for 16.04</span></h4>


Builder code public in OSS-Repo [here](https://github.com/google/oss-fuzz/tree/master/infra/base-images/base-msan-builder). This builds all system libraries with MSAN instrumentation (in both origins and no-origins configs). There are some false positives that we need to fix from time-to-time. E.g. llvm side fixes ([1](https://reviews.llvm.org/D42630), etc), build side fixes ([1](https://github.com/google/oss-fuzz/commit/22b932b62006c128bf7cc061c3a06219c571387f), [2](https://github.com/google/oss-fuzz/commit/a306a95093b2892a4c120e2b396500fa33209e90), etc)

<h4><span style="text-decoration:underline;">IPC Fuzzer</span></h4>


[https://chromium.googlesource.com/chromium/src/+/lkcr/docs/ipc_fuzzer.md](https://chromium.googlesource.com/chromium/src/+/lkcr/docs/ipc_fuzzer.md) 

Needs a lot of grooming from time to time, but need to declare new message types as they are added to codebase or update their format.
