# 0x01. Flutter - Flutter Intro

-   [Breaking Bad API](https://intranet.hbtn.io/rltoken/w1cwETXKifT1G7HMUf4AyQ "Breaking Bad API")
-   [List View Flutter](https://intranet.hbtn.io/rltoken/5PU_tKg7LU1AuK_ch4QJLA "List View Flutter")
-   [Grid View Flutter](https://intranet.hbtn.io/rltoken/axkCPqgfOWGleja6e6tiCg "Grid View Flutter")
-   [Future Builder](https://intranet.hbtn.io/rltoken/voTFRX2zsBlAcyR9FGRkEw "Future Builder")

## Setup Flutter

[Install Flutter](https://intranet.hbtn.io/rltoken/fRg3_57nW2Q4bthqxJVmnQ "Install Flutter")

[How to Install Flutter on Windows](https://intranet.hbtn.io/rltoken/338lXGJdtmI4xAidmkoByA "How to Install Flutter on Windows")

[How to Install Flutter on macOS](https://intranet.hbtn.io/rltoken/nyy_5fw3FYHkfavvuiTv1A "How to Install Flutter on macOS")

[Setup Flutter in Visual Studio Code](https://intranet.hbtn.io/rltoken/_tDILBGQmsOK4VSpG_Sxlg "Setup Flutter in Visual Studio Code")

## Tasks

### 0. My First Flutter Project

mandatory

Create a flutter project inside the task directory

Inside  `lib/main.dart`  paste the following code:

```
import 'package:flutter/material.dart';
import 'package:breaking_bad/home_screen.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: const HomeScreen(),
    );
  }
}

```

Create a new file  `lib/models.dart`. Inside the file create a new class  `Character`  with these attributes:

-   “name” : String
-   “imgUrl” : String
-   “id” : int

Create a new class constructor that accepts one argument  `json`  that initialises the class attributes with their corresponding values :

-   “name” : json[“name”]
-   “imgUrl” : json[“img”]
-   “id” : json[“char_id”]
    
-   Constructor prototype :  `Character.fromJson(Map<String, dynamic> json)`
    

Create a new file  `lib/home_screen.dart`  : Inside  `lib/home_screen.dart`  create a new StatelessWidget  `HomeScreen`.

Inside  `HomeScreen`: Create a function  `fetchBbCharacters()`  that returns a list of all Breaking Bad characters.

Override the  `build()`  function: Function prototype:  `Widget build(BuildContext context)`

Returns:  `Scaffold()`  Inside the scaffold add an appBar with text “Breaking Bad Quotes”

Set scaffold body to  `FutureBuilder()`  where the future argument is the data returned by  `fetchBbCharacters()`  and the builder argument is a function that accepts two arguments context and snapshot and returns:

-   If snapshot contains data :  `GridView.builder()`
-   If snapshot returns an error : center widget with text “Error”
-   If snapshot is still loading : center widget with  `circularProgressIndicator()`

Create a new file  `lib/character_tile.dart`: - Inside  `lib/character_tile.dart`  create a new StatelessWidget  `CharacterTile`:

Inside  `CharacterTile`: Add class attribute :

-   “character” : “Character()”

Override the  `build()`  function: Function prototype:  `Widget build(BuildContext context)`  Returns  `GridTile()`  Edit the  `GridView.builder()`  and the  `GridTile()`  widgets to look as follows:

![](https://holbertonintranet.s3.amazonaws.com/uploads/medias/2021/11/2d07c6415d650065f41ffccf2ba68c8c43aae84c.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIARDDGGGOU5BHMTQX4%2F20220729%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20220729T200121Z&X-Amz-Expires=86400&X-Amz-SignedHeaders=host&X-Amz-Signature=3efd60258e1c67ec8df25ffe5d550a1d1b8e3adf3d18dcd31e0efa73cbac458d)

**Repo:**

-   GitHub repository:  `holbertonschool-flutter_intro`
-   Directory:  `breaking_bad`

Done?  Help

### 1. Quote Screen

mandatory

Complete what you have built in the last task inside it:

Create a new file  `lib/quotes_screen.dart`:

-   Inside  `lib/quotes_screen.dart`  create a new StatelessWidget  `QuotesScreen`  with this attribute:

“id” : int

-   Inside  `QuotesScreen`:

Create a new function  `fetchQuote(id)`  that returns the quotes for the character corresponding to that id

-   Override the  `build()`  function :

Function prototype:  `Widget build(BuildContext context)`

Returns  `Scaffold()`

Set scaffold body to  `FutureBuilder()`  where the future argument is the data returned by  `fetchQuote(id)`  and the builder argument is a function that accepts two arguments context and snapshot and returns:

-   If snapshot contains data :  `ListView.Builder()`
-   If snapshot returns an error : center widget with text “Error”
-   If snapshot is still loading : center widget with  `circularProgressIndicator()`

Set the  `itemBuilder`  function inside  `ListView()`  to return a  `ListTile()`  with the title being the quote corresponding to that index

-   Inside  `CharacterTile`:

Wrap the image with a  `GestureDetector()`  and set it to navigate to  `QuotesScreen(id)`  while passing the selected character’s id when taped

Now when clicking on a character’s tile it will navigate to this screen:

![](https://holbertonintranet.s3.amazonaws.com/uploads/medias/2021/11/d6265da4206acd57b130340364abdc6e217c639f.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIARDDGGGOU5BHMTQX4%2F20220729%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20220729T200121Z&X-Amz-Expires=86400&X-Amz-SignedHeaders=host&X-Amz-Signature=7220872dfd99fea40ca7802aad8ccca4420bc944281ce8bcc664fa928e3ee3ad)

**Repo:**

-   GitHub repository:  `holbertonschool-flutter_intro`
-   Directory:  `breaking_bad`

