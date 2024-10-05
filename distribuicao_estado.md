import pandas as pd
import matplotlib.pyplot as plt

# Simulação dos dados conforme os descritos
dados_distribuicao = {
    'Estado': ['SP', 'RJ', 'MG', 'BA', 'PR', 'RS', 'CE', 'PE', 'PA', 'GO'],
    'Número de Operações': [616687, 252335, 200702, 128133, 105474, 103213, 99254, 89921, 64511, 62499],
}

# Criar DataFrame
df_distribuicao = pd.DataFrame(dados_distribuicao)

# Gráfico de Pizza para o Número de Operações
plt.figure(figsize=(10, 8))
plt.pie(df_distribuicao['Número de Operações'], labels=df_distribuicao['Estado'], autopct='%1.1f%%', startangle=140)

# Título do gráfico
plt.title('Distribuição do Número de Operações por Estado')
plt.axis('equal')  # Para que o gráfico de pizza seja circular

# Exibir o gráfico
plt.show()
