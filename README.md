# Building a Path to Modern R Debugger Interfaces

_an ISC Proposal for Oct 2025_

[![build-status](https://github.com/dgkf/2025-10-isc-proposal-debug-adapter/actions/workflows/publish-proposal.yaml/badge.svg)](https://github.com/dgkf/2025-10-isc-proposal-debug-adapter/actions/workflows/publish-proposal.yaml)

Debugging from the R prompt provides many conveniences such as access to all the
dynamicism of the debugger frame, a persistent user session, full control of
where and how to enter the debugger and effective tools for resuming execution.

However, if you've used a development environment that provides a visual debugger,
you may have experienced the state falling out of sync, inconsistencies in the
visible environments or been constrained to only debugging a full R script in
isolation.

The experience that IDEs are able to expose have long suffered these challenges
and have made commendable progress while working around limitations of R's
existing debugger tools. However, these solutions have required undo engineering
effort and work around these limitations in fragile ways. With the advent of
some internal debugging hooks in R `devel`, there is potential for these
challenges to be smoothed over. Yet, exploration has proven that some friction
points remain that prevent a truly comprehensive solution.

This work aims to experiment with further changes that would allow for full
coverage of the execution points required by modern debugging tools.

## Background

Modern IDEs almost ubiquitously communicate with debuggers over a recent standard,
the debug-adapter protocol. This language-agnostic standard has matured over
recent years to provide a consistent and comprehensive debugging experience
regardless of IDE.

However, implementing this protocol requires that an implementation is capable of
executing code at key points within the evaluation loop of a debugging session.
To-date, there is only one hook available to developers. Although _possible_ to
implement a DAP server with only this hook, it is by no means convenient, requiring
considerable overhead to provide an interface that resembles the expected user
experience.

Following discussion with other developers who have deeply investigated the DAP,
particularly those working on Posit's `ark`, we've aligned on a common set of
minimal changes that would allow further exploration before committing to changes
in R's internals. We believe that this project provides a vehicle both for
exploring that implementation and simultaneously using them to implement a pilot
DAP server as a mechanism of vetting the proposed changes before they are
stabilized.

## License

<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons Licence" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" property="dct:title">ISC Boilerplate</span> by <a xmlns:cc="http://creativecommons.org/ns#" href="https://github.com/stephlocke" property="cc:attributionName" rel="cc:attributionURL">Stephanie Locke</a> is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>.<br />Based on a work at <a xmlns:dct="http://purl.org/dc/terms/" href="https://github.com/RConsortium/isc-proposal" rel="dct:source">https://github.com/RConsortium/isc-proposal</a>.
