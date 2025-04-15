## Descripción
Have you heard of Rust? Fix the syntax errors in this Rust file to print the flag! Download the Rust code [here](https://challenge-files.picoctf.net/c_verbal_sleep/3f0e13f541928f420d9c8c96b06d4dbf7b2fa18b15adbd457108e8c80a1f5883/fixme1.tar.gz).
## Solución
Primero compilamos el `main.rs` y nos dice esto
```
error: expected `;`, found keyword `let`
 --> main.rs:5:37
  |
5 |     let key = String::from("CSUCKS") // How do we end statements in Rust?
  |                                     ^ help: add `;` here
...
8 |     let hex_values = ["41", "30", "20", "63", "4a", "45", "54", "76", "01", "1c", "7e", "59", "63", "e1", "61", "25", "7f", "5...
  |     --- unexpected token

error: argument never used
  --> main.rs:26:9
   |
25 |         ":?", // How do we print out a variable in the println function?
   |         ---- formatting specifier missing
26 |         String::from_utf8_lossy(&decrypted_buffer)
   |         ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^ argument never used

error[E0432]: unresolved import `xor_cryptor`
 --> main.rs:1:5
  |
1 | use xor_cryptor::XORCryptor;
  |     ^^^^^^^^^^^ you might be missing crate `xor_cryptor`
  |
help: consider importing the `xor_cryptor` crate
  |
1 + extern crate xor_cryptor;
  |

error[E0425]: cannot find value `ret` in this scope
  --> main.rs:18:9
   |
18 |         ret; // How do we return in rust?
   |         ^^^ help: a local variable with a similar name exists: `res`

error: aborting due to 4 previous errors

Some errors have detailed explanations: E0425, E0432.
For more information about an error, try `rustc --explain E0425`.
```

1- El primer error se soluciona con un `;` 
```rust
let key = String::from("CSUCKS");
```
2- El segundo error que nos marcan es sobre imprimir variables
```rust
    println!(
        "{}", // How do we print out a variable in the println function? 
        String::from_utf8_lossy(&decrypted_buffer)
    );
```
3- El tercer error es escribiendo el return bien:
```rust
    if res.is_err() {
        return; // How do we return in rust?
    }
```
4- Ahora solo debemos hacer un `cargo build` y el `cargo run`
```shell
 $ cargo run
    Finished `dev` profile [unoptimized + debuginfo] target(s) in 0.01s
     Running `/home/tux/Documents/fixme1/target/debug/rust_proj`
picoCTF{4r3_y0u_4_ru$t4c30n_n0w?}
```
## Notas adicionales
- Para descomprimir el archivo usamos `$ tar -xvzf fixme1.tar.gz`
- Para instalar rust en WSL `curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh`
- Para instalar el compilador de rust `sudo apt install rustc`
## Referencias
- https://www.rust-lang.org/es/tools/install