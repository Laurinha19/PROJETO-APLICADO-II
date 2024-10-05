import pandas as pd
import matplotlib.pyplot as plt
import numpy as np

# Simulação dos dados conforme os descritos
dados_estatisticas = {
    'Métrica': ['Número Médio de Operações', 'Volume Médio de Operações'],
    'Valor': [408, 864831.50],  # Valor em reais
    'Desvio Padrão': [1498, 4382223.00],
}

# Criar DataFrame
df_estatisticas = pd.DataFrame(dados_estatisticas)

# Configurando o gráfico
fig, ax1 = plt.subplots()

# Plotando as médias
ax1.bar(df_estatisticas['Métrica'], df_estatisticas['Valor'], color='b', alpha=0.6, label='Média')
ax1.set_ylabel('Valores Médios', color='b')
ax1.tick_params(axis='y', labelcolor='b')

# Criando um segundo eixo y para o desvio padrão
ax2 = ax1.twinx()
ax2.plot(df_estatisticas['Métrica'], df_estatisticas['Desvio Padrão'], color='r', marker='o', label='Desvio Padrão')
ax2.set_ylabel('Desvio Padrão', color='r')
ax2.tick_params(axis='y', labelcolor='r')

# Título e exibição do gráfico
plt.title('Estatísticas Descritivas')
fig.tight_layout()
plt.show()
