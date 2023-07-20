import 'dart:math';

import 'package:flutter/material.dart';

void main() {
  runApp(const FunnyQuotesApp());
}

class FunnyQuotesApp extends StatelessWidget {
  const FunnyQuotesApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Funny Quotes',
      theme: ThemeData(
        colorScheme: ColorScheme.fromSeed(seedColor: Colors.deepPurple),
        useMaterial3: true,
      ),
      home: const HomePage(),
    );
  }
}

class HomePage extends StatefulWidget {
  const HomePage({super.key});

  @override
  State<HomePage> createState() => _HomePageState();
}

class _HomePageState extends State<HomePage> {
  static const List<String> quoteList = [
    'หลายโลนะ เเต่ไม่หลายใจ',
    'ทุกการเติบโต ย่อมปวดหลังเสมอ',
    'อยากลองขัดใจ แต่หาสก็อตไบร์ทไม่เจอ',
    'คงมีแต่พระ ที่ต้องการฉัน',
    'แคปชั่นไม่รู้ แคปหมูไม่แน่',
  ];
  static const List<Color> colorList = [
    Colors.cyan,
    Colors.amber,
    Colors.deepPurpleAccent,
    Colors.pink,
    Colors.green,
    Colors.black,
    Colors.red,
  ];
  var quote = quoteList[0]; // state variable
  var colors = colorList[0];
  void handleClickGo() {
    setState(() {
      //Text
      var randT = Random();
      var randomIndex = randT.nextInt(quoteList.length);
      quote = quoteList[randomIndex];

      //Color
      var randC = Random();
      var randomColor = randC.nextInt(colorList.length);
      colors = colorList[randomColor];
      print(randomIndex);
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('คำคมกวนๆ')),
      floatingActionButton: FloatingActionButton(
        onPressed: handleClickGo,
        child: const Center(
          child: Text(
            'Next Quote',
            textAlign: TextAlign.center,
          ),
        ),
      ),
      body: Center(
        child: Padding(
          padding: const EdgeInsets.all(32.0),
          child: Text(
            quote,
            style: TextStyle(
              color: colors,
              fontSize: 50,
              fontStyle: FontStyle.italic,
              fontWeight: FontWeight.bold,
            ),
          ),
        ),
      ),
    );
  }
}
