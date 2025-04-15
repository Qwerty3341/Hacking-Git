## Descripción
Have you heard of Rust? Fix the syntax errors in this Rust file to print the flag! Download the Rust code [here](https://challenge-files.picoctf.net/c_verbal_sleep/dcdaf491b35c1d0f5075e9583edbbb7aaea1dffb6ad32bc000e4d87b5200ff7b/fixme3.tar.gz).
## Solución
Al parecer en Rust existe un lenguaje oculto "Unsafe Rust" que permite: 
- Desreferenciar un puntero sin procesar
- Llamar a una función o método inseguro
- Acceder o modificar una variable estática mutable
- Implementar un rasgo inseguro
- Acceder a los campos de una unión

Si vamos hacemos un cargo run nos sale este error:
```
$ cargo run
   Compiling rust_proj v0.1.0 (/home/tux/Documents/fixme3)
error[E0133]: call to unsafe function `std::slice::from_raw_parts` is unsafe and requires unsafe function or block
  --> src/main.rs:31:31
   |
31 |         let decrypted_slice = std::slice::from_raw_parts(decrypted_ptr, decrypted_len);
   |                               ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^ call to unsafe function
   |
   = note: consult the function's documentation for information on how to avoid undefined behavior

For more information about this error, try `rustc --explain E0133`.
error: could not compile `rust_proj` (bin "rust_proj") due to 1 previous error
```
Al parecer estamos llamando a una unsafe function sin la sintaxis adecuada.

Si vamos al código nos encontramos que la declaración del bloque "unsafe" está comentada, así que que le quitamos los "//":
```rust
unsafe {
	// Decrypt the flag operations 
	let decrypted_buffer = xrc.decrypt_vec(encrypted_buffer);

	// Creating a pointer 
	let decrypted_ptr = decrypted_buffer.as_ptr();
	let decrypted_len = decrypted_buffer.len();
	
	// Unsafe operation: calling an unsafe function that dereferences a raw pointer
	let decrypted_slice = std::slice::from_raw_parts(decrypted_ptr, decrypted_len);

	borrowed_string.push_str(&String::from_utf8_lossy(decrypted_slice));
}
println!("{}", borrowed_string);
```
Ahora si hacemos el `cargo run` nos sale esto:
```shell
$ cargo run
   Compiling rust_proj v0.1.0 (/home/tux/Documents/fixme3)
    Finished `dev` profile [unoptimized + debuginfo] target(s) in 0.93s
     Running `/home/tux/Documents/fixme3/target/debug/rust_proj`
Using memory unsafe languages is a: PARTY FOUL! Here is your flag: picoCTF{n0w_y0uv3_f1x3d_1h3m_411}
```
## Notas adicionales
En la documentación de rust nos dicen esto:
"Rust has a second language hidden inside it that doesn’t enforce these memory safety guarantees: it’s called _unsafe Rust_ and works just like regular Rust, but gives us extra superpowers."
## Referencias
https://doc.rust-lang.org/book/ch20-01-unsafe-rust.html#dereferencing-a-raw-pointer