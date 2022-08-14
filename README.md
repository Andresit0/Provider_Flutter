# PROVIDER EXAMPLE


## CLass That Use Provider

    //ChangeNotifier Inside Class To notifyListeners() Providers
    class Counter with ChangeNotifier {
        int _counter = 0;
        get currentCounter => _counter;
        void add1ToCounter() {
            _counter++;
            notifyListeners();
        }
    }

## Defining List Of Providers

    class MyApp extends StatelessWidget {
    const MyApp({Key? key}) : super(key: key);
    @override
    Widget build(BuildContext context) {
        //Definig A List Of Providers
        return MultiProvider(
            providers: [
                ChangeNotifierProvider(create: (context) => Counter()),
            ],
            child: MaterialApp(
                title: 'Flutter Demo',
                theme: ThemeData(
                primarySwatch: Colors.blue,
                ),
                home: const MyHomePage(title: 'Flutter Demo Home Page'),
            ),
        );
    }
    }

## Widget That Creates Its Own Context

  Widget counterWidget() {
    return Consumer<Counter>(
      builder: (context, counter, _) => Text(
        counter.currentCounter.toString(),
      ),
    );
  }

  counterWidget(),

## Information Inside A Provider
    final counter = Provider.of<Counter>(context);
    Text('${counter.currentCounter}'),

  


