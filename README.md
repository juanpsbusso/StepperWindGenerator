# Stepper Wind Generator o Generador Eólico DIY con Motor Paso a Paso

Este proyecto detalla la construcción de un generador eólico compacto y de bajo coste, diseñado para montarse en cualquier lugar y alimentar luces LED decorativas o un circuito de carga de baterías. Utiliza un motor paso a paso trifásico como generador, aprovechando su capacidad para generar tensión a bajas RPM.

## Motivación y Contexto

Vivo en una zona con vientos constantes. La idea de este proyecto surgió al ver el viento y pensar que podría tener una aplicación práctica y visual. Este pequeño generador, montado en el auto, no solo enciende unas luces LED para darle un aspecto genial, sino que la intensidad de las luces o la cantidad de LEDs que se encienden nos permite inferir la velocidad relativa del viento, convirtiéndolo en un 'anemómetro lumínico' visual.

## ¿Cómo Funciona?

## Principio de Generación

El corazón del sistema es un motor paso a paso. Cuando el eje del motor es girado por la fuerza del viento (mediante las aspas), el motor actúa como un generador de corriente alterna (AC). Dependiendo del modelo de motor, este entregará una tensión alterna multifásica. En mi caso, el motor específico que estoy utilizando es de tres fases, por lo que genera corriente alterna trifásica.

## El Corazón Eléctrico (El Rectificador Trifásico)

Para poder alimentar dispositivos de corriente continua (DC), como luces LED o cargar una batería, necesitamos convertir la AC trifásica que entrega el motor en una tensión DC estable. Para ello, he diseñado e implementado un rectificador trifásico de onda completa.

Utilicé una simulación (ver la Figura 1) para validar el diseño antes de construirlo. El circuito incluye:

* Un puente de diodos Schottky de baja caída (D1-D6) para rectificar la señal.

* Un regulador de tensión ajustable (U1, LM317H) para controlar la tensión de salida.

* Un circuito de control de carga basado en un transistor (Q1) y resistencias ajustables, diseñado originalmente para cargar una batería de 3.7V. Este circuito se puede adaptar fácilmente para controlar la intensidad de las luces LED.



<p align="center">
  <img src="https://github.com/user-attachments/assets/0cd42c6a-407f-4d9b-83bf-5e6669034cc5" width="600" alt="Esquema de simulación del rectificador trifásico">
</p>
<p align="center">
  <em>Figura 1: Esquema de simulación del rectificador trifásico de onda completa.</em>
</p>

## De la Simulación a la Realidad: PCB y Perfboard

Para pasar del diseño al prototipo, realicé el diseño de una placa de circuito impreso (PCB) utilizando KiCad. El diseño de la PCB está disponible en la carpeta hw/ del repositorio para aquellos que deseen fabricarlo.

<p align="center">
  <img src="https://github.com/user-attachments/assets/18572a97-8d0f-4780-beea-e35133042fbb" width="600" alt="Prototipo en perfboard con LEDs de vehículo">
</p>
<p align="center">
  <em>Figura 2: PCB diseñado en KiCad.</em>
</p>

Sin embargo, para la construcción inicial y pruebas rápidas, decidí armar el circuito en una perfboard (ver Figura 3). Esto demuestra la viabilidad del diseño incluso sin una fabricación de PCB profesional, utilizando componentes estándar y soldadura punto a punto.

<p align="center">
  <img src="https://github.com/user-attachments/assets/8fe50a0e-1588-4102-bcc5-f0958de519ec" width="600" alt="Vista superior del prototipo en perfboard conectado a las placas LED">
</p>
<p align="center">
  <em>Figura 3: Vista detallada del prototipo físico montado en perfboard y su conexión a los módulos LED.</em>
</p>

| Componente | Descripción | Cantidad |
| :--- | :--- | :--- |
| **D1-D6** | 1N5819G (Diodos Schottky) | 6 |
| **C1** | 10µF (Capacitor de desacoplo) | 1 |
| **-** | Placas LED (extraídas de óptica de vehículo) | 2 |
| **-** | Motor Paso a Paso (Modelo trifásico) | 1 |
| **-** | Perfboard o placa virgen para PCB | 1 |

## Futuras Mejoras

* Circuito de carga: Implementar el circuito completo de la simulación con el LM317 para poder cargar pequeñas baterías de litio.

* Integración de medición digital: Implementar un medidor de tensión digital, con un microcontrolador, para monitorear la batería o la tensión generada.

* Carcasa impermeable: Diseñar una carcasa 3D para proteger todo el sistema electrónico de las inclemencias del tiempo.
