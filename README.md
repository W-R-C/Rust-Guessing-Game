# Rust-Guessing-Game
My first Rust program

This is a simple Rust program that takes user input and compares it to the secretly generated number.
More information about the program can be found at the following link: https://doc.rust-lang.org/stable/book/ch02-00-guessing-game-tutorial.html


use rand::Rng;
use std::cmp::Ordering;
use std::io;

/// My first Rust program. Found at https://doc.rust-lang.org/stable/book/ch02-00-guessing-game-tutorial.html

fn main() {
    let secret_number = rand::thread_rng().gen_range(1..=100);

    println!("Guess the number!");
    loop {
        println!("Please input your guess.");
        let mut guess = String::new();

        io::stdin()
            .read_line(&mut guess)
            .expect("Failed to read line");

        let guess: u32 = match guess.trim().parse() {
            Ok(num) => num,
            Err(_) => continue,
        };

        println!("You guessed: {guess}");

        match guess.cmp(&secret_number) {
            Ordering::Less => println!("Too small!"),
            Ordering::Greater => println!("Too big!"),
            Ordering::Equal => {
                println!("You Win!");
                break;
            }
        }
    }
}
