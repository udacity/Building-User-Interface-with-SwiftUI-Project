Countdowns App
-----
# Project Instructions

## What am I building?

In this course, you'll embark on the development of the "Countdowns" app, a SwiftUI-based application designed to manage and countdown to your important events. But this isn't just any countdown app. Picture it as a practical space to get your hands dirty with the intricacies of SwiftUI.

Central to the app is the concept of events. You'll be adding, editing, and displaying them in an organized timeline. Through this process, you'll gain valuable experience in navigation, seamlessly moving between different views and ensuring a fluid user experience.

But the learning doesn't stop there. You'll delve into the world of state management, understanding how to keep your app's data in sync and respond dynamically to user interactions. And as you build, you'll also appreciate the power of SwiftUI's view composition, piecing together various components to construct a cohesive and interactive user interface.

By the time you wrap up, you'll not only have a fully operational Countdowns app but also a deeper understanding of SwiftUI's capabilities in crafting intuitive and dynamic iOS applications.

## Why am I building this?

Building the Countdowns app is more than just another project on your SwiftUI journey; it's an exploration into the depth and breadth of what SwiftUI has to offer, particularly focusing on its latest features and best practices.


* **View Modifiers**: Dive into the art of customization. Learn how to apply view modifiers effectively, enhancing the visual appeal and functionality of your views.

* **NavigationStack and NavigationLink**: Experience firsthand the power of the new `NavigationStack`. Seamlessly push and pop views in your navigation stack, ensuring a fluid and intuitive navigation experience for the users.

* **Parent-child Communication**: Unlock the potential of closures in SwiftUI. Understand how parent views can influence child views and vice versa, facilitating a two-way communication that's both powerful and efficient.

* **State and Observation**: Delve into the heart of SwiftUI's dynamic nature. Grasp how to use State properties and Swift's Observation framework to reactively update your UI in response to data changes.

* **Lists and Swipe Actions**: Get hands-on with the `List` component. Display arrays of data elegantly and introduce swipe actions, allowing users to interact with each row effectively.

* **Native SwiftUI Components**: Unleash the capabilities of native components like `ColorPicker`, `DatePicker`, and `ImagePicker`. These tools offer an out-of-the-box solution, ensuring consistency and reducing development time.

* **Date Formatting**: Discover the art of date presentation. Learn to use `DateFormatter` to tailor how dates are displayed, enhancing clarity and user comprehension.

In essence, while the Countdowns app will be a testament to your progress, the real gold is in the skills and techniques you'll acquire along the way. By the end of this journey, you'll be well-equipped to tackle more advanced SwiftUI challenges, having a firm grasp of its foundational and advanced concepts.

You're constructing this countdown management application for several reasons. Firstly, it offers an excellent way to grasp the advanced concepts of SwiftUI. Instead of grappling with abstract ideas, you'll see their real-world applications as you integrate them into your app.

By undertaking this project, you'll understand the significance of SwiftUI's declarative approach and how it changes the way we think about UI development. More than just constructing an app, you'll experience the best practices that professional SwiftUI developers apply daily.

In conclusion, while you'll have a full-fledged Countdowns app by the end, the real treasure is the profound comprehension of SwiftUI, setting you up for more intricate iOS projects.

## How should I build this?

### Creating a New Xcode Project

1. Launch Xcode and select "New" > "Project" from the "File" menu.
2. Choose the "App" template under the "iOS" tab.
3. Name your project "Countdowns" and ensure:
    * Interface: SwiftUI
    * Language: Swift
    * Storage: None
4. Choose a save location and optionally create a Git repository for version control.
5. Familiarize with the default structure: ContentView.swift for app code and CountdownsApp.swift as the app's entry point.

With your project set up, you're ready to start building the Countdowns app!

### Designing Your Data - The `Event` Struct

* Start by defining the `Event` struct, ensuring it has the necessary attributes: id (UUID), title (String), date (Date), and textColor (Color).
* Ensure the struct conforms to both the `Comparable` and `Identifiable` protocols. This ensures smooth integration with SwiftUI's `List` view and easy sorting of events based on their dates.

### Building The Views - EventsView, EventRow, and EventForm

#### EventsView: The Main View

* List of Events: Utilize SwiftUI's `List` component to dynamically display a list of `EventRow` views based on your events data.
* Swipe-to-Delete: Enhance user interaction by adding swipe gestures. Within the List, integrate `.onDelete` or `swipeActions` to enable users to swipe and delete events.
* Navigation & Toolbar: Embed your List within a `NavigationStackView` to enable navigation capabilities.
* Add a toolbar to your view and incorporate a "plus" button using `.toolbar` modifier. Tapping this should push the `EventForm` view in `add` mode, allowing users to create a new event.

#### EventRow: A Snapshot of Your Event

* View Composition: Structure your `EventRow` view using a VStack. This vertical stack will contain your event's title and its relative date.
* Styling and Coloring: Apply the event's `textColor` to the title to ensure dynamic text coloring.
* Utilize a `RelativeDateTimeFormatter` for the date, providing user-friendly relative time descriptions like "now", "tomorrow" or "5 minutes ago".

#### EventForm: Crafting and Editing Events

* Form Structure: Build your `EventForm` view using SwiftUI's `Form` component. This provides a structured layout optimized for data input.
* Sections & Fields: Within the Form, create a Section that houses the following:
    * Title: Integrate a `TextField` bound to your event's title.
    * Date: Incorporate a `DatePicker`, offering users a calendar interface to select the event date.
    * Text Color: Introduce a `ColorPicker`, enabling dynamic color selection for the event title color.
* Validation: Implement logic to check the title field. Ensure it's not empty before allowing users to save the event.
* Same View, Two Use Cases: The same view should be used for adding or editing events, consider using an enum, more about this in Rubrics.
* Communication: The form should have a callback closure `onSave: (Event) -> Void` that returns the added/updated event to the `EventsView`.

> By focusing on each view and its components, you'll methodically build a cohesive and interactive user interface for managing events in your Countdowns app.

### Going Beyond - Adding Images (Optional but Recommended)

* Expand the `Event` struct by adding an imageData (Data) property.
* In the `EventForm` view, incorporate an `ImagePicker` bound to `Event.imageData`.
* In the `EventRow` view, display the event's image if available.

### Embrace the Journey

Learning to code is both a fascinating journey and a rewarding skill. Remember, it's completely natural to face challenges, experience moments of frustration, and encounter "gotcha" situations along the way. These are all part of the learning curve. Don't let them discourage you; instead, view them as opportunities to grow and understand the subject matter deeply.

Throughout the Countdowns app project, you'll encounter various SwiftUI concepts and patterns. Should you find a topic challenging, remember we've equipped you with valuable resources. Use them to clarify doubts and broaden your understanding. Every challenge faced is a step forward in your development journey. Embrace the process, stay curious, and most importantly, enjoy the ride. Happy coding!

## What are the requirements?

### Event Structure
The Event struct should have these attributes:
* `id`: A unique identifier using `UUID`.
* `title`: A string to capture the event's essence.
* `date`: A `Date` object indicating when the event occurs.
* `textColor`: A `Color` attribute to customize the event's title color.

Conformance to both the `Comparable` and `Identifiable` protocols.

### EventsView
* Use of `NavigationStackView` bound to `NavigationPath` to manage navigation stack.
* A list displaying all events, each represented by an `EventRow` view.
* Events should be sorted by date, sooner to end on top.
* Ability to swipe to delete individual events.
* A toolbar with a "plus" button pushing the `EventForm` view for event creation.
* Tapping any `EventRow` should push the `EventForm` view for event editing, then, tapping "save" in the form should pop the form and update the list.

### EventRow
* Event's title should be colored by the associated `textColor`.
* Event's date should be formatted with a `RelativeDateTimeFormatter`.
* The row should utilize a private `Timer` to keep the date format correct.

### EventForm
* A `Form` layout with a `Section` containing:
    * `TextField` for the event's title.
    * `DatePicker` for selecting the event's date.
    * `ColorPicker` for choosing the title's display color.
* Selecting a color should update the title's `TextField` text color. 
* The same view is used for adding/editing events. Consider using an enum `enum Mode { case add, edit(Event) }`
* The view should have a closure `onSave: (Event) -> Void` that is used to update events in the `EventsView`.
* The view should have a toolbar with a save button that called the `onSave` closure.
* Dismissing the view without tapping "Save" should **not** update anything in the `EventsView`.
* The form's navigation title should be "Add Event" when adding, and "Edit (event title)" when editing.

### Going Above and Beyond (Optional)

While the core requirements lay a solid foundation for your Countdowns app, diving deeper and adding these enhancements will take your app to the next level and provide a richer experience:

**Integrate Images in Your Events**
* Expand the `Event` model by adding an imageData (Data) property.
* Enhance the `EventForm` with an `ImagePicker` row, allowing users to choose and attach images to their events.
* Modify the `EventRow` to display the chosen image alongside the event details, providing a visual context to each event.


**Implement Data Persistence**

Drawing from your previous project, introduce a caching mechanism to ensure events are saved and retrieved even after app restarts.

> This can be achieved using **UserDefaults** or file-based storage caching.

## Resources

|Resource Description|Link|
|---|---|
|Comparable \| Apple documentation|[https://developer.apple.com/documentation/swift/comparable](https://developer.apple.com/documentation/swift/comparable)|
|Identifiable \| Apple documentation|[https://developer.apple.com/documentation/swift/identifiable](https://developer.apple.com/documentation/swift/identifiable)|
|swipeActions \| Apple documentation|[https://developer.apple.com/documentation/swiftui/view/swipeactions(edge:allowsfullswipe:content:)](https://developer.apple.com/documentation/swiftui/view/swipeactions(edge:allowsfullswipe:content:))|
|DatePicker \| Apple documentation|[https://developer.apple.com/documentation/swiftui/datepicker](https://developer.apple.com/documentation/swiftui/datepicker)|
|ColorPicker \| Apple documentation|[https://developer.apple.com/documentation/swiftui/colorpicker](https://developer.apple.com/documentation/swiftui/colorpicker)|
|The SwiftUI cookbook for navigation \| WWDC '22|[https://developer.apple.com/videos/play/wwdc2022/10054/](https://developer.apple.com/videos/play/wwdc2022/10054/)|
|How to create a toolbar and add buttons to it|[https://www.hackingwithswift.com/quick-start/swiftui/how-to-create-a-toolbar-and-add-buttons-to-it](https://www.hackingwithswift.com/quick-start/swiftui/how-to-create-a-toolbar-and-add-buttons-to-it)|
|How to show a relative date and time using RelativeDateTimeFormatter|[https://www.hackingwithswift.com/example-code/system/how-to-show-a-relative-date-and-time-using-relativedatetimeformatter](https://www.hackingwithswift.com/example-code/system/how-to-show-a-relative-date-and-time-using-relativedatetimeformatter)|
|How to use a timer with SwiftUI|[https://www.hackingwithswift.com/quick-start/swiftui/how-to-use-a-timer-with-swiftui](https://www.hackingwithswift.com/quick-start/swiftui/how-to-use-a-timer-with-swiftui)|
