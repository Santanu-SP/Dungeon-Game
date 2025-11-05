# 🐲 OOP Dungeon Game

Welcome to the dungeon.

It's not a very *fun* dungeon (yet), but it's an extremely *well-structured* one.

This project is a classic challenge to demonstrate the four pillars of Object-Oriented Programming (OOP). We don't just write code; we build a *system*.

And this system has knights, goblins, and spike pits.

## The Four Pillars (But With Goblins)

This project isn't just a file of code. It's a system built on these four core concepts.

### 1\. Abstraction

We don't define a vague "thing." We create blueprints.

  * `Entity` is an Abstract Base Class (ABC). You can't *make* a plain "Entity."
  * `Combatant` is also an ABC. You can't make a plain "Combatant."
  * They force their children (like `Player`) to implement methods like `attack()` and `take_damage()`. This is our contract.

### 2\. Inheritance

This is how we stop repeating code. We create a "family tree" of classes.

```
Entity (ABC)
 |
 +-- Combatant (ABC)
 |    |
 |    +-- Player (Concrete)
 |    |
 |    +-- Monster (Concrete)
 |
 +-- Trap (Concrete)
```

  * `Player` and `Monster` get all the "Entity" stuff (like `name`, `max_hp`) for free.
  * This makes our code clean and easy to change.

### 3\. Encapsulation

We protect our data.

  * Attributes like `_power`, `_max_hp`, and `_current_hp` are "protected" (using the `_` convention).
  * You can't just set a player's health to 999. You *must* call a method like `take_damage()`.
  * This prevents bugs and keeps our objects in a valid state.

### 4\. Polymorphism

This is the "magic" part. It means "many forms."

The `attack()` method can target *any* `Entity`. But the *result* is different depending on the object.

  * `hero.attack(goblin)`: The `Monster.take_damage()` method is called.
  * `hero.attack(spike_trap)`: The `Trap.take_damage()` method is called, which prints "The attack has no effect\!"

Same action. Different behaviors. That's polymorphism.

## Class Breakdown

Here's a quick look at every "blueprint" in the system.

### `Entity(ABC)`

  * **The Grandparent.** Everything in the game is an `Entity`.
  * **Abstract Methods:** `is_alive` (property), `take_damage(amount)`
  * **Concrete Method:** `get_health_percentage()`

### `Combatant(ABC)`

  * **The Parent.** Any `Entity` that can fight.
  * **Inherits from:** `Entity`
  * **Attributes:** `_power`
  * **Abstract Method:** `attack(target)`

### `Player(Combatant)`

  * **Our Hero.** A concrete class you can create.
  * **Inherits from:** `Combatant`
  * **Attributes:** `player_class` (e.g., "Knight")
  * **Implements:** `is_alive`, `take_damage(amount)`, `attack(target)`

### `Monster(Combatant)`

  * **The Baddie.** A concrete class for enemies.
  * **Inherits from:** `Combatant`
  * **Attributes:** `monster_type` (e.g., "Goblin")
  * **Implements:** `is_alive`, `take_damage(amount)`, `attack(target)`

### `Trap(Entity)`

  * **The Odd One Out.** A trap is an `Entity`, but it is **not** a `Combatant`.
  * **Inherits from:** `Entity`
  * **Implements:** `is_alive`, `take_damage(amount)` (which just prints "no effect")
  * **Special Method:** `spring_trap(target)`: This is how the trap deals damage and then deactivates itself.

## How to Run

This is a self-contained script. It uses the `random` library (for attack rolls) but nothing else.

1.  Make sure you have Python installed.
2.  Run the file from your terminal: python <your file_name.language>

<!-- end list -->

```
python Coding.py
```

(Or whatever you named the file)

### The Simulation

The code doesn't just define classes; it also runs a small test simulation at the bottom.

1.  It creates **Sir Bugsalot** (the Player).
2.  It creates **Grumble** (the Monster).
3.  It creates a **Spike Pit** (the Trap).
4.  It makes Sir Bugsalot attack Grumble.
5.  It makes the Spike Pit spring on Sir Bugsalot.
6.  It prints the final status to prove the whole system works.
