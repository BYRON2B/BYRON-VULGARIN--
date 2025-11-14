# -----------------------------------------
# PROGRAMA: REPRESENTACIÓN INTERACTIVA DE UNA MATRIZ 3x5
# -----------------------------------------
# Autor: Alex Armando Ávila Coello
# Descripción: Este programa crea una matriz de 3 filas por 5 columnas,
# la muestra en pantalla y permite al usuario buscar un valor específico
# ingresando la fila y columna deseadas. Incluye manejo de errores.

# ---------------------------------------------------------
# Paso 1: DEFINICIÓN DE LA MATRIZ Y FUNCIONES AUXILIARES
# ---------------------------------------------------------

def mostrar_matriz(matriz: list[list[int]]):
    """
    Muestra la matriz en un formato visual claro, numerando las filas.
    """
    print("\n--- MATRIZ DE 3 FILAS x 5 COLUMNAS ---\n")
    for i, fila in enumerate(matriz):
        print(f"Fila {i+1}: {fila}")
    print("-" * 35)

def buscar_y_mostrar_elemento(matriz: list[list[int]], fila_num: int, col_num: int):
    """
    Busca un elemento en la matriz dada una fila y columna (basadas en 1)
    y muestra el resultado.
    """
    # Convertir a índices basados en 0 para Python
    indice_fila = fila_num - 1
    indice_col = col_num - 1

    # Verificar que los índices estén dentro de los límites de la matriz
    if 0 <= indice_fila < len(matriz) and 0 <= indice_col < len(matriz[0]):
        elemento = matriz[indice_fila][indice_col]
        print("\n---------------------------------------------")
        print(f"Resultado: El elemento en la Fila {fila_num}, Columna {col_num} es: {elemento}")
        print("---------------------------------------------")
    else:
        # Este error no debería ocurrir si la validación de entrada es correcta,
        # pero es una buena práctica tenerlo como respaldo.
        print("\nError: Los índices calculados están fuera de rango.")

# ---------------------------------------------------------
# Paso 2: BLOQUE PRINCIPAL DE EJECUCIÓN
# ---------------------------------------------------------
# Este bloque se ejecuta solo cuando el archivo se corre directamente.
if __name__ == "__main__":
    # Definición de la matriz (usando listas anidadas)
    matriz_principal = [
        [5, 8, 2, 4, 3],       # Fila 1
        [7, 5, 1, 8, 7],       # Fila 2
        [2, 8, 16, 15, 14]     # Fila 3
    ]

    # Mostrar la matriz al usuario
    mostrar_matriz(matriz_principal)

    # Explicación conceptual para el usuario
    print("\nExplicación:")
    print("Una matriz es una estructura de datos bidimensional.")
    print("Para encontrar un valor, necesitas su número de fila (horizontal) y de columna (vertical).")

    # Bucle para permitir búsquedas múltiples o salir del programa
    while True:
        try:
            # Pedir al usuario que ingrese la fila y columna
            print("\n--- Búsqueda de Elemento ---")
            fila_usuario = int(input("Ingresa el número de la fila (1-3): "))
            columna_usuario = int(input("Ingresa el número de la columna (1-5): "))

            # Validar que la entrada esté en el rango correcto
            if 1 <= fila_usuario <= 3 and 1 <= columna_usuario <= 5:
                # Si la entrada es válida, buscar y mostrar el elemento
                buscar_y_mostrar_elemento(matriz_principal, fila_usuario, columna_usuario)
            else:
                # Si la entrada está fuera de rango, mostrar un mensaje de error
                print("\nError: Por favor, ingresa una fila entre 1 y 3, y una columna entre 1 y 5.")

        except ValueError:
            # Si el usuario ingresa algo que no es un número
            print("\nError: Entrada no válida. Debes ingresar números enteros.")
        
        # Preguntar al usuario si desea realizar otra búsqueda
        otra_busqueda = input("\n¿Deseas buscar otro elemento? (s/n): ").lower()
        if otra_busqueda != 's':
            print("\n¡Programa finalizado!")
            break
