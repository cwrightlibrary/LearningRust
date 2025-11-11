# 🦀 Learning Rust

Learning Rust using Jupyter notebooks and [The Rust Programming Book](https://doc.rust-lang.org/book/).

## 🪄 Step-by-Step Setup Guide (for macOS M1)

### 1. Install Rust

Open **Terminal** and run:

```bash
curl https://sh.rustup.rs -sSf | sh
```

Then follow the prompts (press `1` to proceed with default install).

After installation, **restart your terminal** and verify it works:

```bash
rustc --version
cargo --version
```

> 🧩 Tip: On M1 Macs, rustup automatically installs the correct `aarch64-apple-darwin` toolchain.

---

### 2. Install Python and Jupyter

If you already have Python 3, skip the first command.

```bash
brew install python
pip3 install jupyterlab
```

Test it:

```bash
jupyter notebook
```

That should open a local notebook in your browser — just to confirm Jupyter is working.

Press `Ctrl+C` to quit.

---

### 3. Install the Rust Jupyter Kernel

Now, install the **Evcxr Jupyter** kernel — it’s what lets you run Rust code in `.ipynb` files:

```bash
cargo install evcxr_jupyter
```

Then register it with Jupyter:

```bash
evcxr_jupyter --install
```

You should see something like:

```
Installed evcxr_jupyter v0.x.x
Added kernel "Rust" to Jupyter.
```

---

### 4. Test it in Jupyter

Try this in Terminal:

```bash
jupyter notebook
```

Then create a **New Notebook → Rust**.

Type and run:

```rust
let x = 42;
println!("x = {}", x);
```

If it prints output, you’re good ✅

---

### 5. Set Up VS Code

#### Install Extensions:

In VS Code, install the following from the Extensions Marketplace:

* 🧩 **Jupyter** (by Microsoft)
* 🦀 **Rust Analyzer** (by The Rust Foundation)
* 🧠 **CodeLLDB** (for debugging, optional but useful)

> You can search by name in the Extensions panel (`⇧⌘X`).

---

### 6. Open a Rust Notebook in VS Code

You can now:

1. Open VS Code
2. Create a new file: `test.ipynb`
3. In the top-right corner (kernel selector), click and choose **“Rust (evcxr)”**

Then test a cell:

```rust
fn greet(name: &str) {
    println!("Hello, {name}!");
}
greet("world");
```

🎉 It should run right inside VS Code!

---

## 🧰 (Optional) Update and Troubleshoot

* Update Rust:

  ```bash
  rustup update
  ```
* If VS Code doesn’t detect your Rust kernel:

  ```bash
  jupyter kernelspec list
  ```

  You should see something like:

  ```
  rust    /Users/yourname/Library/Jupyter/kernels/rust
  ```

  If missing, re-run:

  ```bash
  evcxr_jupyter --install
  ```

---

## 🦾 Bonus Tips

* You can run **Cargo commands** inside cells:

  ```rust
  :dep rand = "0.8"
  use rand::Rng;

  let x: i32 = rand::thread_rng().gen_range(1..=100);
  println!("Lucky number: {}", x);
  ```

  (`:dep` tells evcxr to add a Cargo dependency on the fly!)

* Use **`Shift+Enter`** in VS Code to run a cell, just like in Python notebooks.

---

## ✅ Summary

| Step | What You Did    | Command(s)                                               |     |
| ---- | --------------- | -------------------------------------------------------- | --- |
| 1    | Install Rust    | `curl [https://sh.rustup.rs](https://sh.rustup.rs) -sSf  | sh` |
| 2    | Install Jupyter | `pip3 install jupyterlab`                                |     |
| 3    | Add Rust kernel | `cargo install evcxr_jupyter && evcxr_jupyter --install` |     |
| 4    | Open Notebook   | `jupyter notebook` or in VS Code                         |     |
| 5    | Select Kernel   | Choose “Rust (evcxr)” in VS Code                         |     |
