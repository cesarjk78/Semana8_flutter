# Semana8_flutter




import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Calendar',
      theme: ThemeData(primarySwatch: Colors.blue),
      debugShowCheckedModeBanner: false,
      home: SafeArea(
        child: Scaffold(
          appBar: AppBar(title: const Text('Calendario Tecsupniano')),
          body: Column(
            children: <Widget>[
              calendarWidget(),
            ],
          ),
        ),
      ),
    );
  }

  // Widget que genera el calendario simple
  Widget calendarWidget() {
    const double size01 = 16.0;
    const double size02 = 20.0;

    return Column(
      children: <Widget>[
        // Título del mes
        Container(
          padding: const EdgeInsets.all(8),
          color: Colors.blueAccent,
          child: const Center(
            child: Text(
              "Mayo del 2025",
              style: TextStyle(fontSize: size02, color: Colors.white, fontWeight: FontWeight.bold),
            ),
          ),
        ),

        // Días de la semana (lunes a domingo)
        Container(
          color: Colors.blue[50],
          child: Row(
            mainAxisAlignment: MainAxisAlignment.spaceEvenly,
            children: const <Widget>[
              _DayBox(day: "Lun."),
              _DayBox(day: "Mar."),
              _DayBox(day: "Mié."),
              _DayBox(day: "Jue."),
              _DayBox(day: "Vie."),
              _DayBox(day: "Sab."),
              _DayBox(day: "Dom."),
            ],
          ),
        ),

        // Días del mes
        Container(
          color: const Color.fromARGB(255, 248, 248, 248),
          child: Column(
            children: <Widget>[
              _DayRow(days: ["", "", "1", "2", "3", "4", "5"]),  // Primera fila
              _DayRow(days: ["6", "7", "8", "9", "10", "11", "12"]), // Segunda fila
              _DayRow(days: ["13", "14", "15", "16", "17", "18", "19"]), // Tercera fila
              _DayRow(days: ["20", "21", "22", "23", "24", "25", "26"]), // Cuarta fila
              _DayRow(days: ["27", "28", "29", "30", "31", "", ""]), // Quinta fila
            ],
          ),
        ),
      ],
    );
  }
}

// Widget para los días de la semana y los días del mes
class _DayBox extends StatelessWidget {
  final String day;
  const _DayBox({required this.day});

  @override
  Widget build(BuildContext context) {
    return Container(
      padding: const EdgeInsets.all(10),
      width: 50,  // Aumentado para dar más espacio a los textos largos
      height: 50, // Aumentado para dar más espacio a los textos largos
      alignment: Alignment.center,
      decoration: BoxDecoration(
        color: Colors.transparent,  // Fondo transparente
      ),
      child: Text(
        day,
        style: const TextStyle(fontSize: 16, fontWeight: FontWeight.bold),
        overflow: TextOverflow.ellipsis,  // Asegura que el texto largo se recorte correctamente si es necesario
      ),
    );
  }
}

// Widget para una fila de días
class _DayRow extends StatelessWidget {
  final List<String> days;

  const _DayRow({required this.days});

  @override
  Widget build(BuildContext context) {
    return Row(
      mainAxisAlignment: MainAxisAlignment.spaceEvenly,
      children: days.map((day) => _DayBox(day: day)).toList(),
    );
  }
}
