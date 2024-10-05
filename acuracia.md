# Definindo os valores de verdadeiros positivos, verdadeiros negativos,
# falsos positivos e falsos negativos
VP = 600  # Operações bem-sucedidas
VN = 300  # Operações não bem-sucedidas
FP = 50   # Falsos positivos
FN = 50   # Falsos negativos

# Calculando a acurácia
def calcular_acuracia(VP, VN, FP, FN):
    total = VP + VN + FP + FN
    acuracia = (VP + VN) / total
    return acuracia

# Chamada da função
acuracia = calcular_acuracia(VP, VN, FP, FN)

# Exibindo o resultado
print(f"Acurácia do modelo: {acuracia:.2%}")
