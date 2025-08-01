# Thread-Safe Singleton Pattern in C++

This repository demonstrates a thread-safe implementation of the Singleton design pattern using **double-checked locking** in C++.

## 🔧 Features

- **Thread Safety:** Uses `std::mutex` to ensure only one instance is created across threads.
- **Lazy Initialization:** Singleton instance is only created when first requested.
- **Double-Checked Locking:** Optimizes performance by avoiding unnecessary locking once the instance is initialized.

## 📄 Code Overview

```cpp
static Singleton* getInstance() {
    if (instance == nullptr) {
        lock_guard<mutex> lock(mtx);
        if (instance == nullptr) {
            instance = new Singleton();
        }
    }
    return instance;
}
