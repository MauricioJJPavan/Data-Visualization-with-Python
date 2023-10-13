# IBM Data Visualization with Python
![data-visualization-with-python](https://github.com/MauricioJJPavan/Data-Visualization-with-Python/assets/132507042/9c97af6f-541b-4a5d-a5ca-10c0d7e3f314)


Develop a Line plot using the functionality of pandas to show how automobile sales fluctuate from year to year.
![Line_plot_1](https://github.com/MauricioJJPavan/Data-Visualization-with-Python/assets/132507042/a64f30c2-2425-40cc-a2f4-f5299ad83849)


Plot different lines for categories of vehicle type and analyse the trend to answer the question "Is there a noticeable difference in sales trends between different vehicle types during recession periods?"
![Line_plot_2](https://github.com/MauricioJJPavan/Data-Visualization-with-Python/assets/132507042/87edca10-d093-4878-9959-ebd69f691363)


Use the functionality of Seaborn Library to create a visualization to compare the sales trend per vehicle type for a recession period with a non-recession period.
![Bar_Chart](https://github.com/MauricioJJPavan/Data-Visualization-with-Python/assets/132507042/4ee8ed86-ebd9-4ce5-98a0-fd2835c1541b)


Create and display graphs for Recession Report Statistics.
![RecessionReportgraphs](https://github.com/MauricioJJPavan/Data-Visualization-with-Python/assets/132507042/4760ce8c-203c-4438-a9d4-4e973a71f782)


Create and display graphs for Yearly Report Statistics.
![YearlyReportgraphs](https://github.com/MauricioJJPavan/Data-Visualization-with-Python/assets/132507042/5015446c-6a1d-4eed-8692-66b22eba4f79)




import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt


# Dados de exemplo
data = {
    'Ano': [2010, 2011, 2012, 2013, 2014, 2015, 2016, 2017, 2018, 2019, 2020],
    'Vendas': [50000, 55000, 60000, 75000, 80000, 70000, 85000, 95000, 100000, 110000, 90000],
    'TipoVeiculo': ['Sedan', 'SUV', 'Caminhao', 'Sedan', 'SUV', 'Caminhao', 'Sedan', 'SUV', 'Caminhao', 'Sedan', 'SUV']
}

df = pd.DataFrame(data)

plt.figure(figsize=(10, 6))
plt.plot(df['Ano'], df['Vendas'], marker='o', linestyle='-')

plt.title('Vendas de Automóveis ao Longo dos Anos')
plt.xlabel('Ano')
plt.ylabel('Vendas')

plt.grid(True)
plt.show()





plt.figure(figsize=(10, 6))

for tipo_veiculo in df['TipoVeiculo'].unique():
    plt.plot(df[df['TipoVeiculo'] == tipo_veiculo]['Ano'], 
             df[df['TipoVeiculo'] == tipo_veiculo]['Vendas'],
             label=tipo_veiculo,
             marker='o',
             linestyle='-')

plt.title('Tendências de Vendas para Diferentes Tipos de Veículos ao Longo dos Anos')
plt.xlabel('Ano')
plt.ylabel('Vendas')
plt.legend()
plt.grid(True)
plt.show()




anos_recessao = [2013, 2014]
df['Periodo'] = df['Ano'].apply(lambda x: 'Recessão' if x in anos_recessao else 'Não-Recessão')

plt.figure(figsize=(10, 6))
sns.lineplot(x='Ano', y='Vendas', hue='TipoVeiculo', style='Periodo', data=df, marker='o')
plt.title('Tendência de Vendas por Tipo de Veículo: Recessão vs. Não-Recessão')
plt.xlabel('Ano')
plt.ylabel('Vendas')
plt.legend(title='Tipo de Veículo')
plt.grid(True)
plt.show()





anos_recessao = [2013, 2014]
df['Periodo'] = df['Ano'].apply(lambda x: 'Recessão' if x in anos_recessao else 'Não-Recessão')

# Gráfico de barras para média de vendas por tipo de veículo durante a recessão
plt.figure(figsize=(10, 6))
sns.barplot(x='TipoVeiculo', y='Vendas', hue='Periodo', data=df)
plt.title('Média de Vendas por Tipo de Veículo durante a Recessão')
plt.xlabel('Tipo de Veículo')
plt.ylabel('Média de Vendas')
plt.legend(title='Período')
plt.grid(True)
plt.show()

# Gráfico de dispersão para visualizar a relação entre ano e vendas durante a recessão
plt.figure(figsize=(10, 6))
sns.scatterplot(x='Ano', y='Vendas', hue='Periodo', style='TipoVeiculo', data=df)
plt.title('Relação entre Ano e Vendas durante a Recessão')
plt.xlabel('Ano')
plt.ylabel('Vendas')
plt.legend(title='Período')
plt.grid(True)
plt.show()

# Gráfico de linha para mostrar a evolução das vendas durante a recessão
plt.figure(figsize=(10, 6))
sns.lineplot(x='Ano', y='Vendas', hue='TipoVeiculo', style='Periodo', data=df, marker='o')
plt.title('Evolução das Vendas por Tipo de Veículo durante a Recessão')
plt.xlabel('Ano')
plt.ylabel('Vendas')
plt.legend(title='Tipo de Veículo')
plt.grid(True)
plt.show()






plt.figure(figsize=(10, 6))
sns.barplot(x='Ano', y='Vendas', hue='TipoVeiculo', data=df)
plt.title('Vendas por Tipo de Veículo ao Longo dos Anos')
plt.xlabel('Ano')
plt.ylabel('Vendas')
plt.legend(title='Tipo de Veículo')
plt.grid(True)
plt.show()

plt.figure(figsize=(10, 6))
sns.lineplot(x='Ano', y='Vendas', data=df, marker='o')
plt.title('Tendência Geral de Vendas ao Longo dos Anos')
plt.xlabel('Ano')
plt.ylabel('Vendas')
plt.grid(True)
plt.show()

plt.figure(figsize=(10, 6))
sns.violinplot(x='TipoVeiculo', y='Vendas', data=df, inner='quartile')
plt.title('Distribuição de Vendas por Tipo de Veículo')
plt.xlabel('Tipo de Veículo')
plt.ylabel('Vendas')
plt.grid(True)
plt.show()
