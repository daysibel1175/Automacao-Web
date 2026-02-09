# Automação Web para Atualização de Preços

## 📋 Descrição do Projeto

Este projeto implementa uma automação web em Python utilizando Selenium para atualizar automaticamente os preços de produtos com base nas cotações de moedas (Dólar, Euro) e commodities (Ouro). O sistema é ideal para lojas que comercializam produtos internacionais e precisam manter seus preços atualizados conforme as variações do mercado.

## 🎯 Funcionalidades

- **Busca automática de cotações**: Captura em tempo real as cotações do Dólar e Euro através do Google
- **Consulta de preço do ouro**: Obtém a cotação atualizada do ouro em reais através do site Melhor Câmbio
- **Atualização de planilha**: Atualiza automaticamente os preços de compra e venda dos produtos
- **Cálculo de margens**: Aplica margem de lucro específica para cada produto
- **Exportação de dados**: Gera planilha Excel atualizada com os novos preços

## 🚀 Como Funciona

O sistema realiza as seguintes etapas:

1. **Coleta de Cotações**:
   - Abre o navegador Chrome automaticamente
   - Busca no Google a cotação do Dólar
   - Busca no Google a cotação do Euro
   - Acessa o site Melhor Câmbio para obter o preço do ouro

2. **Processamento de Dados**:
   - Lê a planilha `Produtos.xlsx` com os produtos e preços originais
   - Atualiza as cotações na coluna correspondente
   - Calcula o preço de compra: `Preço Original × Cotação`
   - Calcula o preço de venda: `Preço de Compra × Margem`

3. **Exportação**:
   - Gera uma nova planilha `Produtos Atualizado.xlsx` com os valores atualizados

## 📦 Tecnologias Utilizadas

- **Python 3.9+**
- **Selenium**: Automação de navegador web
- **Pandas**: Manipulação de dados e planilhas Excel
- **openpyxl**: Leitura e escrita de arquivos Excel

## 🔧 Instalação

### Pré-requisitos

- Google Chrome instalado
- ChromeDriver compatível com sua versão do Chrome

### Instalação das Dependências

```bash
pip install selenium pandas openpyxl
```

## 📖 Uso

1. Certifique-se de que o arquivo `Produtos.xlsx` está no diretório do projeto com a estrutura:
   - Produtos
   - Preço Original
   - Moeda (Dólar, Euro ou Ouro)
   - Cotação
   - Preço de Compra
   - Margem
   - Preço de Venda

2. Execute o notebook Jupyter:
```bash
jupyter notebook "Automaçao Web.ipynb"
```

3. Execute todas as células do notebook em sequência

4. O arquivo `Produtos Atualizado.xlsx` será gerado com os preços atualizados

## 📊 Estrutura dos Dados

### Entrada (Produtos.xlsx)
| Produtos | Preço Original | Moeda | Cotação | Preço de Compra | Margem | Preço de Venda |
|----------|----------------|-------|---------|-----------------|--------|----------------|
| Câmera Canon | 999.99 | Dólar | 5 | 4999.95 | 1.40 | 6999.930 |
| Joia 20g | 20.00 | Ouro | 350 | 7000.00 | 1.15 | 8050.000 |

### Saída (Produtos Atualizado.xlsx)
A mesma estrutura, porém com cotações atualizadas em tempo real e preços recalculados.

## 🛠️ Detalhes Técnicos

### Selenium vs PyAutoGUI

O projeto utiliza Selenium em vez de PyAutoGUI porque:
- **Controle direto do navegador**: Selenium controla o navegador nativamente
- **Execução em segundo plano**: Pode rodar sem interface gráfica (headless mode)
- **Maior confiabilidade**: Não depende de posicionamento de elementos na tela
- **Melhor tratamento**: Sabe quando a página carregou completamente
- **Caracteres especiais**: Não tem problemas com acentuação e caracteres especiais

### XPath

O projeto usa XPath para localizar elementos na página web:
```python
navegador.find_element("xpath", '//*[@id="search-box"]')
```

Para obter o XPath de um elemento:
1. Inspecione a página (F12)
2. Selecione o elemento com o seletor
3. Clique com botão direito no código HTML
4. Copy → Copy XPath

### Modo Headless (Opcional)

Para executar sem abrir a janela do navegador:
```python
from selenium.webdriver.chrome.options import Options
chrome_options = Options()
chrome_options.add_argument('--headless')
navegador = webdriver.Chrome(options=chrome_options)
```

## 📝 Estrutura do Projeto

```
Automacao-Web/
│
├── Automaçao Web.ipynb       # Notebook principal com toda a automação
├── Produtos.xlsx              # Planilha de entrada com produtos
├── Produtos Atualizado.xlsx   # Planilha de saída com preços atualizados
└── README.md                  # Este arquivo
```

## 🤝 Contribuindo

Contribuições são bem-vindas! Sinta-se à vontade para:
- Reportar bugs
- Sugerir novas funcionalidades
- Melhorar a documentação
- Enviar pull requests

## 📄 Licença

Este projeto é de código aberto e está disponível para uso educacional e comercial.

## 👤 Autor

Desenvolvido para automatização de preços em lojas que trabalham com produtos internacionais e commodities.

---

**Nota**: Certifique-se de ter uma conexão estável com a internet ao executar a automação, pois o sistema depende de consultas em tempo real a sites externos.
