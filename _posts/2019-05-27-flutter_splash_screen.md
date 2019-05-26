---
layout: post   
title: How to make Splash screen of Flutter.   
---

## simple Splash Screen ## 
``` 
class SplashScreen extends StatefulWidget {
  @override
  _SplashScreenState createState() => _SplashScreenState();
}

class _SplashScreenState extends State<SplashScreen> {

  @override
  void initState() {
    super.initState();
    //Change screen to main 
    Timer(Duration(seconds: 2), () => Navigator.pushReplacementNamed(context, '/main'));
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Stack(
        fit: StackFit.expand,
        children: <Widget>[
          Container(
            decoration: BoxDecoration(
              color: Color(0xffd38213),
              gradient: LinearGradient(
                colors: [Color(0xffffe1b7), Color(0xffd38213)],
                begin: Alignment.centerRight,
                end: Alignment.centerLeft
              ),
            ),
          ),
          Column(
            mainAxisAlignment: MainAxisAlignment.center,
            children: <Widget>[
              Text('I am a Splash',
              style: TextStyle(color: Colors.white,
              fontSize: 28.0,
              fontFamily: 'Poppins'),)
            ],
          )
        ],
      ),
    );
  }
}

``` 


## simple Main Screen ## 
``` 
void main() => runApp(MyApp());

var routes = <String, WidgetBuilder>{
  '/main':(BuildContext context) => HomePage('I am a Home')
};

/// This Widget is the main application widget.
class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: SplashScreen(),
      debugShowCheckedModeBanner: false,
      routes: routes,
    );
  }
}

class HomePage extends StatefulWidget {
  final String title;

  HomePage(this.title);

  @override
  _HomePageState createState() => _HomePageState();
}

class _HomePageState extends State<HomePage> {
  @override
  Widget build(BuildContext context) {
    return Text(widget.title);
  }
}

``` 
