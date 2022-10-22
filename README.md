# flutter_repo

A new Flutter project.

## Getting Started

This project is a starting point for a Flutter application.

Descriptive question :

Q: 1.   Can we nest the Scaffold widget? Why or Why not?
Answer: Yes, you can absolutely nest a Scaffold. Scaffold is just a widget, so you can put it anywhere a widget might go. By nesting a Scaffold, you can layer drawers, snack bars and bottom sheets.

Q: 2.   How to reduce the rebuilding of the widget?
Answer: Basically you can prevent unwanted build calling, using these way
        1. Use Provider library, so using it you can stop unwanted build method calling
        2. Create child Statefull class for individual small part of UI

Q: 3.   How can I access platform(iOS or Android) specific code from Flutter?
Answer: By using MethodChannel

Q: 4.   What is BuildContext? What is its importance?
Answer: BuildContext is actually the widget's element in the Element tree — so every widget has its own BuildContext.
        You usually use BuildContext to get a reference to the theme or to another widget. For example, if you want to show a material dialog, you need a reference to the scaffold. You can get it with Scaffold.of(context), where context is the build context. of() searches up the tree until it finds the nearest scaffold.


Q:      In the below code, list1 declared with var, list2 with final and list3 with const. What is
        the difference between these lists? Will the last two lines compile?
        var list1 = ['I', '💙', 'Flutter'];

        final list2 = list1;
        list2[2] = 'Dart';   // Will this line compile?

        const list3 = list1; // Will this line compile?

Answer: When using the var keyword,  its value can change. The following line is equivalent to the first line above, except that you explicitly declare the data type:
        List<String> list1 = ['I', '💙', 'Flutter'];

        With final and const, you can’t reassign a new value after the initial assignment. final values are assigned once at runtime and a const variable value has to be either known at compile time, set, or hard coded before you run your app.

        The third line will compile. You’re not reassigning the list2 list itself, but changing the value of an item in the third index position (remember, indexes start with 0). Lists are mutable by default in Dart.

        If you tried to do the following, though, it wouldn’t compile because you’re trying to reassign a final variable:

        list2 = ['I', '💙', 'Dart'];

        The fourth line will not compile because the value of list1 isn’t assigned until runtime. Read Dartlang’s article, Const, Static, Final, Oh my!, to learn more.

Q: 2    Identify the problem in the following code block and correct it?
        String LongOperationMethod() {
        var counting = 0;
        for (var i = 1; i <= 1000000000; i++) {
        counting = i;
        }
        return '$counting! Ready or not, here I come!';
        }
Answer: Expensive Task.It blocks your app because counting to big number is a computationally expensive task.
        Dart code runs inside its own area of memory called an isolate — also known as memory thread. Each isolate has its own memory heap, which ensures that no isolate can access any other isolate's state.

        Making it an async function wouldn't help, either, because it would still run on the same isolate.
        Future<String> makeSomeoneElseCountForMe() async {
        return await compute(LongOperationMethod, 10000000000);
        }

        String LongOperationMethod(int countTo) {
        var counting = 0;
        for (var i = 1; i <= countTo; i++) {
        counting = i;
        }
        return '$counting! Ready or not, here I come!';
        }

Q: 3.   What is the main difference between Mobx & Provider? Can we use both together?
        
Answer: So basically provider is used only for dependency injection with mobx. It is not used for state changes.

        Now when you are using mobx you don't need a stateful widget in most cases because you are handling your state changes inside your mobx store and if there is any changes in the state we use Observer to change ui.
        Yes we can use both together.






