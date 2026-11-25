# Vota Dolores Hidalgo

Plebiscito vecinal con barras animadas y revelación del ganador, construido con **TDD** en Flutter.
Proyecto complementario de práctica de la materia *Desarrollo Móvil Integral*.

## Reglas de negocio protegidas con pruebas

- Cada persona (id de usuario) vota una sola vez.
- Solo se puede votar por una opción que exista.
- No se puede votar después de la fecha de cierre.
- Los porcentajes son correctos, incluso con cero votos (sin división entre cero).
- Si hay empate en primer lugar, se reconoce como empate.

## Estructura

```
lib/
  modelos/        opcion_votacion.dart, votacion.dart, resultado_opcion.dart
  logica/         resultado_voto.dart, servicio_votacion.dart
  presentation/   votacion_screen.dart
  main.dart
test/
  servicio_votacion_test.dart
```

## Ciclo TDD aplicado (Rojo → Verde → Refactor)

| Ronda | Comportamiento | Prueba |
|-------|----------------|--------|
| 1 | Registrar un voto válido | `registrar un voto valido incrementa el contador` |
| 2 | Rechazar opción inexistente | `votar por una opcion que no existe regresa opcionInvalida` |
| 3 | Un usuario no vota dos veces | `un mismo usuario no puede votar dos veces` |
| 4 | Porcentajes (incluye caso sin votos) | `calcula el porcentaje...` / `si no hay ningun voto...` |
| 5 | Determinar ganador | `determinarGanador regresa la opcion con mas votos` |
| 6 | Reconocer empate | `si hay empate, determinarGanador regresa mas de una opcion` |
| 7 | Votación cerrada | `no se puede votar si la votacion ya cerro` / `...sigue abierta...` |
| 8 | Refactor de guard clauses | Las pruebas anteriores siguen en verde |
| — | Integración | `simulacion completa: varios vecinos votan...` |

## Cómo ejecutar

```bash
flutter pub get
flutter test    # 10 pruebas en verde
flutter run
```

## Evidencias (screenshots)

### 1. Proyecto creado
> _Pega aquí la captura de `flutter create vota_dolores_hidalgo` y la estructura de carpetas._

![Estructura del proyecto](screenshots/01_estructura.png)

### 2. Ronda en ROJO (prueba fallando)
> _Captura de `flutter test` con la primera prueba fallando (antes de crear `servicio_votacion.dart`)._

![Prueba en rojo](screenshots/02_rojo.png)

### 3. Ronda en VERDE
> _Captura de `flutter test` con las pruebas pasando._

![Pruebas en verde](screenshots/03_verde.png)

### 4. Todas las pruebas en verde (final)
![Todas las pruebas](screenshots/04_todas_verde.png)

### 5. App en ejecución — barras animadas
![App con barras](screenshots/05_app_barras.png)

### 6. Después de votar
![Después de votar](screenshots/06_despues_de_votar.png)

### 7. Revelación del ganador (animación)
![Ganador](screenshots/07_ganador.png)

## Enlace al repositorio

<!-- Reemplaza con la URL de tu repositorio -->
https://github.com/TU_USUARIO/vota_dolores_hidalgo
