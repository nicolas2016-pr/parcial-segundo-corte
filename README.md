# parcial-segundo-corte
#segundo parcial- NICOLAS SANCHEZ VARON
class Pelicula:
    def __init__(self, codigo="", titulo="", director="", duracion=0, alquilada=False):
        self.__codigo = codigo
        self.__titulo = titulo
        self.__director = director
        self.__duracion = duracion  # en minutos
        self.__alquilada = alquilada

    # Getters
    def get_codigo(self):
        return self.__codigo

    def get_titulo(self):
        return self.__titulo

    def get_director(self):
        return self.__director

    def get_duracion(self):
        return self.__duracion

    def get_alquilada(self):
        return self.__alquilada

    # Setters
    def set_codigo(self, codigo):
        self.__codigo = codigo

    def set_titulo(self, titulo):
        self.__titulo = titulo

    def set_director(self, director):
        self.__director = director

    def set_duracion(self, duracion):
        if duracion >= 0:
            self.__duracion = duracion
        else:
            raise ValueError("La duración no puede ser negativa.")

    def set_alquilada(self, alquilada):
        self.__alquilada = alquilada

    # Métodos funcionales
    def alquilar(self):
        if not self.__alquilada:
            self.__alquilada = True
            return True
        else:
            return False

    def devolver(self):
        if self.__alquilada:
            self.__alquilada = False
            return True
        else:
            return False

    def calcular_precio(self, valor_minuto):
        if valor_minuto < 0:
            return "El valor por minuto no puede ser negativo."
        total = self.__duracion * valor_minuto
        return f"El precio de ver la película es: ${total:.2f}"

    def __str__(self):
        estado = "está alquilada" if self.__alquilada else "no está alquilada"
        return (f"La película con código {self.__codigo}, título '{self.__titulo}', "
                f"dirigida por {self.__director}, tiene una duración de {self.__duracion} minutos y {estado}.")

    def __eq__(self, otra_pelicula):
        if isinstance(otra_pelicula, Pelicula):
            return self.__codigo == otra_pelicula.get_codigo()
        return False


if __name__ == "__main__":
    peli1 = Pelicula("01", "Matrix", "Lana Wachowski", 136, False)
    peli2 = Pelicula("02", "Inception", "Christopher Nolan", 148, False)
    peli3 = Pelicula("03", "El Padrino", "Francis Ford Coppola", 175, False)

    print(peli1)
    print(peli2)
    print(peli3)

    print(peli1.alquilar())   
    print(peli1.alquilar())   
    print(peli1.devolver())   

    print(peli1.calcular_precio(0.75))  
