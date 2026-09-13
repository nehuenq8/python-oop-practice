"""
Ejercicio 6: Gestión de Empleados

Práctica de Programación Orientada a Objetos y encapsulamiento.

- Implementación de getters y setters tradicionales.
- Validación de salario.
- Gestión de una lista de objetos Empleado.
- Aumento de salario mediante un método de la clase.
"""

class Empleado:
    def __init__(self, nombre: str, salario: float):
        self.set_nombre(nombre)
        self.set_salario(salario)
        self.set_aumento(False)

    def get_nombre(self):
        return self._nombre

    def set_nombre(self, nombre):
        self._nombre = nombre

    def get_salario(self):
        return self._salario

    def set_salario(self, salario):
        if salario > 0:
            self._salario = salario
        else:
            raise ValueError("El salario debe ser mayor a 0.")

    def get_aumento(self):
        return self._aumento

    def set_aumento(self, aumento):
        self._aumento = aumento

    def aumentar_salario(self, porcentaje: float):
        aumento = self.get_salario() * porcentaje / 100
        nuevo_salario = self.get_salario() + aumento

        self.set_salario(nuevo_salario)
        self.set_aumento(True)


empleados: list[Empleado] = []

empleados.append(Empleado("Juan", 100000))
empleados.append(Empleado("Ana", 120000))
empleados.append(Empleado("Pedro", 90000))
empleados.append(Empleado("Laura", 150000))
empleados.append(Empleado("Carlos", 110000))

empleados[1].aumentar_salario(10)

print("Empleados que no recibieron aumento:\n")

for empleado in empleados:
    if not empleado.get_aumento():
        print(f"Nombre: {empleado.get_nombre()}")
        print(f"Salario: ${empleado.get_salario():,.2f}")
        print("-" * 30)
