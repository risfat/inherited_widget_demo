# Inherited Widget Demo

This Flutter project demonstrates the use of `InheritedWidget` for managing and sharing state across the widget tree. It consists of a simple app where a widget's background color can be dynamically updated using an `InheritedWidget`.

## Table of Contents
- [Features](#features)
- [Project Structure](#project-structure)
- [Setup and Installation](#setup-and-installation)
- [Usage](#usage)
- [How it Works](#how-it-works)
- [Contributing](#contributing)
- [License](#license)

## Features

- Demonstrates Flutter's `InheritedWidget` for state management.
- A color block (`ColorCardWidget`) that responds to changes in state when a button is pressed.
- Centralized state management using an `InheritedWidget` to propagate changes to the widget tree.

## Project Structure

```plaintext
.
├── lib/
│   ├── inherited_widgets/
│   │   └── color_inherited_widget.dart   # Custom InheritedWidget for managing color state.
│   ├── screens/
│   │   └── home_screen.dart              # HomeScreen with button to change color.
│   └── main.dart                         # Main entry point of the app.
└── pubspec.yaml                          # Project configuration and dependencies.
```

### Main Components
- **`ColorWidget`**: An `InheritedWidget` that provides the current color state and a method to change the color.
- **`HomeScreen`**: The main screen that contains a button to change the color and displays the color card.
- **`ColorCardWidget`**: A widget that displays a card whose background color updates based on the current state provided by `ColorWidget`.

## Setup and Installation

1. **Clone the Repository**

   ```bash
   git clone https://github.com/risfat/inherited_widget_demo.git
   cd inherited-widget-demo
   ```

2. **Install Dependencies**

   Ensure you have Flutter installed on your machine. Then, in the project root directory, run:

   ```bash
   flutter pub get
   ```

3. **Run the App**

   Run the following command to launch the app on your preferred emulator or connected device:

   ```bash
   flutter run
   ```

## Usage

Once the app is running, you'll see a button labeled "Change Color" and a large card with a background color. By pressing the button, the card's background color will change from red to green.

The color state is managed by the `ColorWidget` (`InheritedWidget`), which propagates the color changes to its descendants (like `ColorCardWidget`).

## How it Works

The core of the app is the `ColorWidget`, which extends `InheritedWidget`. This widget allows you to share the color and color-changing logic across the widget tree without passing it explicitly via constructors.

- **`ColorWidget`**:
    - Holds the current `color` and `onColorChange` function.
    - Exposes its state to its child widgets through the `ColorWidget.of(context)` method.

- **`HomeScreen`**:
    - The screen where the button is located to change the color. It updates the color state by calling `onColorChange` provided by `ColorWidget`.

- **`ColorCardWidget`**:
    - A simple widget that reads the current color using `ColorWidget.of(context)` and updates its background color when the state changes.

The `InheritedWidget` ensures that whenever the color changes, any widget that depends on it is automatically rebuilt, providing a simple yet powerful way of managing state across widgets.

## Contributing

Contributions, issues, and feature requests are welcome! Feel free to check out the [issues page](https://github.com/your-username/inherited-widget-demo/issues) or submit a pull request.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more information.