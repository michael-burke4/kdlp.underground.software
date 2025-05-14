## Introduction to Linux Kernel Development: University of Texas San Antonio Spring 2025

| Week # | Class dates | Useful information |
| -- | -- | -- |
| 0 | 21/23 Jan | syllabus/policies/setup [L00](/course/spring2025-utsa/lectures/L00) |
| 1 | 28/30 Jan | [setup due](/course/spring2025-utsa/assignments/setup) barebones Linux [L01](/course/spring2025-utsa/lectures/L01) [L02](/course/spring2025-utsa/lectures/L02) |
| 2 | 04/06 Feb | [new_syscall due](/assignments/new_syscall.md) syscalls [L03](/course/spring2025-utsa/lectures/L03) [L04](/course/spring2025-utsa/lectures/L04) |
| 3 | 11/13 Feb | syscall [L05](/course/spring2025-utsa/lectures/L05) [L06](/course/spring2025-utsa/lectures/L06) |
| 4 | 18/20 Feb | [page_walk due](/assignments/page_walk.md) memory management [L07](/course/spring2025-utsa/lectures/L07) [L08](/course/spring2025-utsa/lectures/L08) |
| 5 | 25/27 Feb | [midpoint proposal due Thurs](/course/spring2025-utsa/assignments/midpoint) mm cont. [L09](/course/spring2025-utsa/lectures/L09) [L10](/course/spring2025-utsa/lectures/L10) |
| 6 | 04/06 Mar | [shell due](/course/spring2025-utsa/assignments/shell) VFS: open [L11](/course/spring2025-utsa/lectures/L11) [L12](/course/spring2025-utsa/lectures/L12) |
| 7 | 11/13 Mar | SPRING BREAK: no class |
| 8 | 18/19 Mar | [midpoint presentation due Thurs](/course/spring2025-utsa/assignments/midpoint) VFS: close [L13](/course/spring2025-utsa/lectures/L13) [L14](/course/spring2025-utsa/lectures/L14) |
| 9 | 25/27 Mar | VFS: read/write [L15](/course/spring2025-utsa/lectures/L15) [L16](/course/spring2025-utsa/lectures/L16) |
| 10 | 01/03 Apr | VFS: write/ioctl/seek [L17](/course/spring2025-utsa/lectures/L17) [L18](/course/spring2025-utsa/lectures/L18) |
| 11 | 08/10 Apr | modules [L19](/course/spring2025-utsa/lectures/L19) [L20](/course/spring2025-utsa/lectures/L20) |
| 12 | 15/17 Apr | modules/chardevs [L21](/course/spring2025-utsa/lectures/L21) [L22](/course/spring2025-utsa/lectures/L22) |
| 13 | 22/24 Apr | [final project](/assignments/final_project.md) chardevs [L23](/course/spring2025-utsa/lectures/L23) [L24](/course/spring2025-utsa/lectures/L24) |
| 14 | 29/01 Apr | final presentations [L25](/course/spring2025-utsa/lectures/L25) [L26](/course/spring2025-utsa/lectures/L26) |
| 15 | 06/08 May | final presentations [L27](/course/spring2025-utsa/lectures/L27) [L28](/course/spring2025-utsa/lectures/L28) |

#### [Frequently Asked Questions](faq.md)

### Course Summary and Purpose

We guide students into the depths of the Linux kernel, introducing the concepts, tools, and frameworks
necessary to become independent contributors to the Linux kernel in particular and open source software more broadly.

### Course Description

Linux is the most widely used operating system in the world.
It powers the world's top supercomputers, every Android phone,
and the servers that host the internet's most popular websites.
At the core of Linux is a software component called the kernel.
It performs critical roles including managing communication with
hardware, sharing system resources equitably, and enforcing
security constraints.
This course will introduce students to Linux kernel development
through hands-on experience working with internal Linux kernel
APIs and providing an overview of some of the core features
and components of the kernel.
Students will gain an invaluable perspective on how their computers
work behind the scenes. By grasping the inner workings of the operating
system and how to make changes to it, they will add a new layer of
understanding to their mental model of computation that will pay
dividends throughout their future in software engineering.

### Course Objectives

Students will:

* Develop Linux kernel internals knowledge, by:

    * Building up an understanding up of various kernel subsystems

    * Creating, developing, and testing interesting and creative Linux kernel modules

    * Stretching their C programming skills to the limit

* Develop the ability to autonomously participate in the open source software community

* Demonstrate the ability to explain technical topics in your own words

* Learn how to give and receive feedback on code patches

### Required Materials

* A computer that can run [`podman`](https://podman.io/)

* Patience, determination, and an ability to focus on a potentially frustrating task for sustained periods of time

* The ability to join a live video call with camera/microphone from that computer
  (i.e. the necessary equipment and a stable internet connection)

### Attendance Policy

Attendance is required.

### Late Work Policy

Late work will not be accepted.

### Automatic Course Failure

If a student fails to complete a task by a deadline or fails to attend class with no prior notice,
an instructor will reach out to you via direct message on matrix.

If we do not hear from the student within one week of an instructor reaching out,
we reserve the right to give the student a final course grade of F.

### Grading Breakdown and Letter Grade Conversion

| Category | Percentage |
|--|--|
| Assignments                           | 50% |
| Midpoint Project                      | 15% |
| Final Project                         | 35% |

|Percentage range|Letter grade|Grade points|
|--|--|--|
|90 ~ 100  |A |4.0|
|85 ~ 89.99|A-|3.7|
|80 ~ 84.99|B+|3.3|
|75 ~ 79.99|B |3.0|
|70 ~ 74.99|B-|2.7|
|65 ~ 69.99|C+|2.3|
|60 ~ 64.99|C |2.0|
|55 ~ 59.99|C-|1.7|
|50 ~ 54.99|D+|1.3|
|40 ~ 49.99|D |1.0|
|below 40  |F |0.0|
