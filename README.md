# 🧩 Philosophers

**Philosophers** is a 42 project that explores the **dining philosophers problem**, a classic exercise in concurrent programming.  
It’s all about managing threads, avoiding deadlocks, and making sure your philosophers don’t starve while they think about… forks 🥢.

---

## 🧠 Project Overview

You’ll simulate a group of philosophers sitting around a table.  
Each philosopher alternates between **thinking**, **eating**, and **sleeping** — but they need **two forks** to eat, and there’s only one fork between each pair.

The challenge:  
Make sure everyone eats **without deadlocks** or **data races**.  
No philosopher should starve, and the simulation should follow strict timing rules.

---

## 🍽️ The Scenario

Each philosopher is represented by a thread:
- 💭 **Thinks**
- 🍴 **Takes two forks** (mutexes)
- 🍝 **Eats for a specific amount of time**
- 😴 **Sleeps**
- Then repeats… until they die or the simulation ends.

---

## 🧾 How to Run

### 🔨 Compilation
```bash
make
```
This will create the executable philo.

## ▶️ Example Run
```bash
./philo 5 800 200 200
```
Where the arguments are:
```bash
./philo number_of_philosophers time_to_die time_to_eat time_to_sleep
```
Optionally, you can add a 5th argument:
[number_of_times_each_philosopher_must_eat]
Example with limit:
```bash
./philo 5 800 200 200 5
```
## 🧰 Example Output
    0 1 is thinking
    10 2 is thinking
    25 1 has taken a fork
    27 1 has taken a fork
    30 1 is eating
    31 2 has taken a fork
    33 2 has taken a fork
    35 2 is eating
    ...
    When a philosopher dies:
    2140 4 died
  
## ⚙️ Allowed Functions
You’ll mostly rely on:
pthread_create, pthread_join, pthread_mutex_init,
pthread_mutex_destroy, pthread_mutex_lock, pthread_mutex_unlock,
usleep, gettimeofday, write, malloc, free
No semaphores, no fancy libs — just raw POSIX threads and timing. ⏱️
💥 Error Handling
❌ Invalid arguments → print an error and exit.
🚫 Negative or zero values → invalid input.
💀 If a philosopher doesn’t eat within time_to_die → he dies and simulation stops.
🧹 Free everything and destroy all mutexes before exit (no leaks allowed).


## 🧩 Visualization (Concept)
          🍝 Philosophers 🍝

        [Fork]   [Philo 1]   [Fork]
           |                   |
        [Philo 2]          [Philo 3]
           |                   |
        [Fork]   [Philo 4]   [Fork]
Each philosopher must pick up two forks to eat,
but since the forks are shared, timing and synchronization are everything ⚖️.

## 🏁 Goal
All philosophers should:
Eat, sleep, and think correctly according to the rules.
Avoid deadlocks.
Avoid starvation.
And exit cleanly when the simulation ends.
If your philosophers can eat without chaos — congratulations, you’ve mastered multithreading 🧠💪

---
