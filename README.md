# KAIST CS431: Concurrent Programming

## Logistics

- Instructor: [Jeehoon Kang](https://www.fearless.systems/jeehoon.kang)
- Time: Mon & Wed 13:00-14:15 (2024 Spring)
- Place:
  + [Youtube channel](https://www.youtube.com/playlist?list=PL5aMzERQ_OZ9j40DJNlsem2qAGoFbfwb4).
    Turn on English subtitles on YouTube, if necessary.
- Websites: <https://github.com/kaist-cp/cs431>, <https://gg.kaist.ac.kr/course/19>
- Announcements: in the [issue tracker](https://github.com/kaist-cp/cs431/issues?q=is%3Aissue+is%3Aopen+label%3Aannouncement)
  + We strongly recommend you watch the repository.
  + Office Hours: Fri 9:15-10:15, Rm. 4432, Bldg. E3-1.
    If you want to come, do so by 9:30.
    See [below](https://github.com/kaist-cp/cs431#rules) for the office hour policy.
    <!-- Fri 9:00-12:00, [Zoom room](https://zoom.us/j/4842624821)(The passcode is same as the class). It is not required, but if you want to come, do so by 9:30. See [below](#communication) for office hour policy. -->

## Course description

### Context

I anticipate that in the next 700 years, computers will be **massively parallel**.
Humankind seeks to enhance computer performance in the era of big data.
This goal has become increasingly challenging following the breakdown of [Dennard scaling](https://en.wikipedia.org/wiki/Dennard_scaling) around 2005, indicating that the performance of sequential computers is unlikely to improve further.
Consequently, both servers and personal computers have adopted multi-core systems.
This challenge is compounded by the end of [Moore's Law](https://en.wikipedia.org/wiki/Moore%27s_law), which signifies our diminishing ability to benefit from denser electronic circuits.
It appears that the primary pathway to optimizing performance now lies in specialization, focusing on exploiting the parallelism in workloads.
Due to these technological trends, I foresee that future computers will be massively parallel.

However, we are not yet fully equipped for the era of massive parallelism.
The principal challenge is managing **shared mutable states**, a key aspect of concurrency.
Coordinating multiple cores and resources requires their inputs and outputs to be synchronized through shared mutable states like memory.
Yet, managing these states is inherently difficult, both in theory and practice.
For instance, with thousands or millions of cores, how can we efficiently synchronize concurrent access to shared memory?
In the face of nondeterministic thread execution interleaving, how can we ensure the safety of a concurrent program?
And considering compiler and hardware optimizations, what constitutes the correct specification of a concurrent data structure?

Fortunately, in the past ten years, the theory of shared mutable states has made significant advances, greatly facilitating the design and analysis of practical systems utilizing these states.
Therefore, in this course, we will explore recent theories of shared mutable states and their application in real-world systems.


### Goal

This course is designed for senior undergraduate or graduate students in computer science and related disciplines who have an interest in the contemporary theory and practice of parallel computer systems.
The course aims to equip students with the ability to:

- Understand the motivations and challenges of concurrent programming.
- Learn design patterns and principles for reasoning in concurrent programming.
- Design, implement, and evaluate concurrent programs.
- Apply their knowledge to real-world parallel systems.

### Textbook

- [Slides](https://docs.google.com/presentation/d/1NMg08N1LUNDPuMxNZ-UMbdH13p8LXgMM3esbWRMowhU/edit?usp=sharing)
- [Code Documentation](https://kaist-cp.github.io/cs431/cs431/)
- References
    + [The Art of Multiprocessor Programming](https://dl.acm.org/doi/book/10.5555/2385452)
    + [The Crossbeam Library Documentation](https://docs.rs/crossbeam/latest/crossbeam/)
    + Concurrent reference counting algorithm (TBA)
    + [Behaviour-Oriented Concurrency](https://dl.acm.org/doi/10.1145/3622852)
    + [C++ Concurrency in Action](https://www.manning.com/books/c-plus-plus-concurrency-in-action-second-edition)
    + [Rust Atomics and Locks](https://marabos.nl/atomics/)


### Schedule

- week 1: CS230/CS330 review on concurrent programming
- week 2: Rust
- week 3: lock-based concurrency (API)
- week 4: lock-based concurrency (implementation 1)
- week 5: lock-based concurrency (implementation 2)
- week 6: lock-based concurrency (application)
- week 7: behavior-oriented concurrency (API)
- week 8: midterm exam
- week 9: lock-free concurrency (concept)
- week 10: lock-free concurrency (data structures 1)
- week 11: lock-free concurrency (data structures 2)
- week 12: lock-free concurrency (data structures 3)
- week 13: lock-free concurrency (specification)
- week 14: lock-free concurrency (garbage collection)
- week 15: behavior-oriented concurrency (implementation)
- week 16: final exam


### Tools

Ensure you are proficient with the following development tools:

- [Git](https://git-scm.com/): Essential for downloading homework templates and managing your development process.
  If you're new to Git, please complete [this tutorial](https://git-scm.com/book/en/v2).

    + Follow these steps to set up your repository:
        * Clone the upstream repository directly without forking it:
          ```bash
          $ git clone --origin upstream git@github.com:2SpaceMasterRace/cs431.git
          $ cd cs431
          $ git remote -v
          upstream	git@github.com:2SpaceMasterRace/cs431.git (fetch)
          upstream	git@github.com:2SpaceMasterRace/cs431.git (push)
          ```
        * To receive updates from the upstream, fetch and merge `upstream/main`:
          ```bash
          $ git fetch upstream
          $ git merge upstream/main
          ```

- [Rust](https://www.rust-lang.org/): The programming language for homework assignments.
  Rust's ownership type system significantly simplifies the development of large-scale system software.

- [NeoVim](https://neovim.io/): Recommended for developing your homework, although you may use any editor of your preference [use the rust-analyzer lsp + lldb for debugging]

## Ignore

1830eaed90e5986c75320daaf131bd3730b8575e866c4e92935a690e7c2a0717
