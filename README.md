# Roaming Ralph – Panda3D Demo

A simple third-person character controller demo built with **Panda3D**.

This project showcases:

* Character movement and animation blending
* Collision detection with uneven terrain
* Terrain height adjustment using collision rays
* A fully rotatable third-person camera
* web deployment using `pygbag`

Based on the classic **“Roaming Ralph”** tutorial.

---

## 📸 Screenshots

![1](screenshots/1.png)
![2](screenshots/2.png)
![3](screenshots/3.png)

---

## 🎮 Controls

| Key   | Action              |
| ----- | ------------------- |
| `ESC` | Quit                |
| `←`   | Rotate Ralph left   |
| `→`   | Rotate Ralph right  |
| `↑`   | Run forward         |
| `↓`   | Walk backward       |
| `A`   | Rotate camera left  |
| `S`   | Rotate camera right |

---

## 🧠 Features Explained

### Character Movement

* Uses `Actor` for animation (`run` and `walk`)
* Animation state changes automatically depending on movement input
* Backward walking plays the walk animation in reverse

### Collision System

* Collision spheres prevent the character from walking through objects
* A `CollisionHandlerPusher` handles physical pushback
* Downward collision rays:

  * Keep Ralph aligned to terrain height
  * Keep the camera above ground level

### Camera System

* Third-person follow camera
* Maintains:

  * Minimum distance (5 units)
  * Maximum distance (10 units)
* Always looks at a floating node above Ralph’s head for stable tracking

---

## 📦 Project Structure

```
Ralph/
│
├── .github/
│   └── workflows/
│       └── pygbag.yml
│
├── main.py
├── models/
│   ├── ralph.egg
│   ├── ralph-run.egg
│   ├── ralph-walk.egg
│   └── world.egg
│
├── screenshots/
└── build/   (generated)
    └── web/   (pygbag output)
```

---

## ⚙️ Requirements

* Python
* Panda3D
* Pygbag

Install dependencies:

```bash
pip install panda3d pygbag
```

---

## ▶️ Running the Game

From the project root:

```bash
pygbag main.py
```

---

## 🕸️ Web Build (pygbag)

You can also install pygbag locally and build yourself:

```bash
pip install pygbag
python -m pygbag --build --ume_block 0 main.py
```

The generated web assets land in `build/web` and can be served by any static host.

---

## ⚠️ Build Warnings

You may see warnings such as:

* Missing `_posixsubprocess`
* Missing `_bootlocale`
* Missing `libcrypto.so.3`
* Missing `libmpdec.so.4`

These are common when building cross-platform bundles and typically **do not prevent the game from running**.

---

## 💡 How It Works (High-Level)

1. `ShowBase` initializes the engine.
2. The world model (`models/world`) is loaded with embedded collision meshes.
3. Ralph is loaded as an `Actor` with animations.
4. Collision spheres protect Ralph from obstacles.
5. Downward collision rays determine terrain height.
6. A task (`moveTask`) updates:

   * Movement
   * Animations
   * Camera positioning
   * Terrain alignment

---

## 📚 Learning Goals

This project demonstrates:

* Basic 3D character controllers
* Working with collision masks
* Terrain-following mechanics
* Third-person camera logic
* Packaging Panda3D games

---

## 👤 Credits

* Author: Ryan Myers
* Models: Jeff Styers, Reagan Heller
* Engine: Panda3D

---

## 📜 License

This project is intended for educational purposes.
Refer to Panda3D’s license for engine-specific terms.
