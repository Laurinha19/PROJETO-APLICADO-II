import pandas as pd

# Carregar o arquivo CSV com o delimitador correto
file_path = 'dados_desenrola.csv'
df = pd.read_csv(file_path, delimiter=';', encoding='utf-8')  # Usar ponto e vírgula como delimitador

# Exibir os nomes das colunas
print("Nomes das colunas no DataFrame:", df.columns)

# Exibir as primeiras linhas do DataFrame
print("Conteúdo do DataFrame:")
print(df.head())

# Verificação e remoção de dados ausentes (exemplo)
df = df.dropna(subset=['NUMERO_OPERACOES', 'VOLUME_OPERACOES'])

# Tratamento de Dados
try:
    # 1. Corrigir valores numéricos com vírgula
    df['VOLUME_OPERACOES'] = df['VOLUME_OPERACOES'].astype(str).str.replace('.', '').str.replace(',', '.').astype(float)

    # 2. Garantir que 'NUMERO_OPERACOES' seja inteiro
    df['NUMERO_OPERACOES'] = df['NUMERO_OPERACOES'].astype(int)

    # 3. Tratamento de outliers (opcional)
    mean_volume = df['VOLUME_OPERACOES'].mean()
    std_volume = df['VOLUME_OPERACOES'].std()
    upper_limit = mean_volume + 3 * std_volume
    df = df[df['VOLUME_OPERACOES'] <= upper_limit]

    # 4. Normalização ou Padronização dos dados (se necessário para modelos preditivos)
    from sklearn.preprocessing import StandardScaler

    scaler = StandardScaler()
    df[['NUMERO_OPERACOES', 'VOLUME_OPERACOES']] = scaler.fit_transform(df[['NUMERO_OPERACOES', 'VOLUME_OPERACOES']])

    # 5. Verificar se há valores duplicados e removê-los
    df = df.drop_duplicates()

    # Exibir os primeiros dados após o tratamento
    print("Dados tratados:")
    print(df.head())

    # Opcional: Salvar o dataframe tratado em um novo arquivo CSV
    df.to_csv('dados_desenrola_tratado.csv', index=False)

except KeyError as e:
    print(f"Erro: A coluna {e} não foi encontrada no DataFrame.")
