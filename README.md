### Repository Description: CoreDataMVVMBootcamp

#### Overview
CoreDataMVVMBootcamp is a SwiftUI project that demonstrates a clean architecture approach using the **MVVM (Model-View-ViewModel)** design pattern for managing Core Data. This project showcases how to create and manage a Core Data stack, handle CRUD (Create, Read, Update, Delete) operations, and bind the data to the SwiftUI views via an observable view model.

The app provides a simple interface where users can add, update, and delete fruits in a list, while adhering to the MVVM principles for better scalability and maintainability.

---

#### Features
- **MVVM Architecture**:
  - **ViewModel**: Handles all Core Data operations, including fetching, adding, updating, and deleting data. The view model keeps the UI and Core Data in sync.
  - **View**: A SwiftUI view (`CoreDataView`) displays the list of fruits and provides user interaction features.
- **Core Data Integration**:
  - Custom `NSPersistentContainer` setup to load and manage the Core Data stack.
  - Operations on `FruitEntity` (a Core Data entity) with attributes like `name`.
- **Add Fruits**: Enter a fruit name in a text field and add it to the list.
- **Update Fruits**: Tap on any fruit in the list to update its name (appends a `!` to the name).
- **Delete Fruits**: Swipe to delete any fruit from the list.
- **Reusable Design**: Implements the Core Data logic in a separate view model (`CoreDataViewModel`) for reusability and separation of concerns.

---

#### How It Works
1. **Core Data Setup**:
   - The `CoreDataViewModel` initializes a `NSPersistentContainer` with the name `FruitsContainer`.
   - The Core Data stack is loaded during initialization, and an initial fetch retrieves all saved fruits.

2. **CRUD Operations**:
   - `fetchFruits()`: Fetches all `FruitEntity` objects from Core Data and updates the `savedEntities` array.
   - `addFruit(text:)`: Creates a new `FruitEntity` with the specified name and saves it.
   - `deleteFruit(indexSet:)`: Deletes a fruit from Core Data based on its index.
   - `updateFruit(entity:)`: Modifies a fruit's name (adds `!`) and saves the change.

3. **SwiftUI Binding**:
   - The `@StateObject` property wrapper is used to instantiate the view model and bind its data to the view.
   - The `@Published` property in the view model ensures that changes in Core Data are automatically reflected in the UI.

---

#### How to Use
1. Clone the repository.
2. Open the project in Xcode.
3. Run the app on the iOS Simulator or a physical device.
4. Use the text field to add a fruit name, tap a fruit to update its name, or swipe to delete it.

---

#### Technologies Used
- **SwiftUI**: Declarative UI framework for building the user interface.
- **Core Data**: Apple's framework for data persistence and management.
- **MVVM Architecture**: Clean separation of concerns:
  - `CoreDataViewModel`: Handles all Core Data operations.
  - `CoreDataView`: UI that binds to the view model.
- **State Management**:
  - `@State` for text input in the view.
  - `@StateObject` for observing changes in the view model.
- **Animations**: `withAnimation` is used for smooth UI updates during delete operations.

---

#### Project Structure
- `CoreDataViewModel.swift`: Manages the Core Data stack and CRUD logic. Publishes updates for binding to the view.
- `CoreDataView.swift`: A SwiftUI view that displays and interacts with the data.
- Core Data Model:
  - Entity: `FruitEntity` with the following attributes:
    - `name` (String): The name of the fruit.

---

#### Example Scenarios
1. Add "Apple" using the text field and click "Button" → "Apple" is added to the list.
2. Tap "Apple" → It updates to "Apple!".
3. Swipe "Apple!" → It is deleted from the list.

---

This project is ideal for developers looking to learn Core Data with MVVM in SwiftUI while building a functional and scalable app.
