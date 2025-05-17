# digitaliza_ponto - Digitalizador de Folha de Ponto Manuscrita

# Projeto - Automação de Captura de Folhas de Ponto

## 1. Visão Geral

Este projeto visa automatizar o processo de digitalização e extração de dados de folhas de ponto preenchidas manualmente. Através da captura e do processamento de imagens, e da utilização de técnicas de reconhecimento óptico de caracteres (OCR) e reconhecimento de escrita manual (HWR), o projeto extrai informações relevantes (como nome, data, horários de entrada/saída) e as organiza automaticamente em uma planilha Microsoft Excel, eliminando a necessidade de digitação manual.

## 2. Funcionalidades

O projeto implementa as seguintes funcionalidades principais:

* **Captura de Imagem:** Processamento de imagens digitais de folhas de ponto manuscritas.
* **Extração de Dados:** Identificação e extração automatizada de informações escritas à mão.
* **Reconhecimento Inteligente:** Aplicação de técnicas de OCR/HWR para converter texto manuscrito em dados digitais.
* **Exportação para Excel:** Organização dos dados extraídos em uma planilha Excel formatada.
* **Automação:** Redução drástica do tempo e esforço gasto na digitação de folhas de ponto.

## 3. Tecnologias Utilizadas

**Google Generative AI (Gemini):** Utilizado para processar e analisar imagens (Visão) e extrair dados manuscritos de documentos, atuando como o motor de "leitura inteligente" da folha de ponto.
*   **Python:** A linguagem de programação base para todo o script.
*   **pandas:** Essencial para organizar os dados extraídos em formato de tabela (`DataFrame`) e prepará-los para exportação.
*   **Pillow (PIL):** Usado para carregar e manipular as imagens da folha de ponto antes do envio para a API de IA.
*   **openpyxl:** Permite a criação e o salvamento dos dados extraídos em um arquivo Microsoft Excel (.xlsx).
*   **google.colab:** Oferece funcionalidades específicas do ambiente Colab, como o acesso seguro a chaves de API e o gerenciamento de upload/download de arquivos.

## 4. Configuração e Instalação

Para executar este notebook, você precisará:

1.  **Obter uma Chave de API do Google Generative AI:** Siga as instruções para obter sua chave em [Google AI Studio](https://aistudio.google.com/app/apikey).
2.  **Configurar a Chave de API no Google Colab:** Armazene sua chave de API de forma segura nos "Segredos" do Google Colab com o nome `GOOGLE_API_KEY`. O notebook acessará a chave a partir daí.
3.  **Executar as células do notebook:** O notebook instalará automaticamente as bibliotecas Python necessárias (google-generativeai, pillow, openpyxl) na primeira célula.

4.   **Uma vez que a chave de API estiver configurada nos segredos do Colab, basta executar todas as células em ordem.**
5.    **Faça upload** da **Folha de Ponto** (pode usar o modelo: **folha_modelo.jpg**)

## 5. Prompt Utilizado 

Analise a imagem fornecida de uma lista de presença/folha de ponto manuscrita.
Sua tarefa é extrair as informações de cada linha da tabela principal.
Para cada linha preenchida na tabela, extraia os seguintes campos:
- "Dia do Mês"
- "Nº do Livro"
- "Nº da Adesão"
- "Código da Função"
- "Nome" (o nome da pessoa)
- "Entrada" (o primeiro horário registrado para a pessoa, no formato HH:MM)
- "Saída" (o segundo horário registrado para a pessoa, no formato HH:MM)
- "Assinatura"

 Regras importantes para a extração:
 1. Formato da Saída: Apresente os dados extraídos como uma lista de objetos JSON, onde cada objeto representa uma linha da tabela.
 2. Campo "Assinatura": Se houver qualquer marca, escrita ou assinatura na coluna "Assinatura" para uma determinada linha, o valor para este campo deve ser "Sim". Se a célula da assinatura estiver visivelmente vazia (sem marcas além da linha da grade), o valor deve ser "Não".
 3. Campos Vazios ou Ilegíveis: Se um campo específico (exceto assinatura) estiver vazio, não preenchido, ou completamente ilegível na imagem para uma linha, use null ou uma string vazia "" para o valor desse campo no JSON. Para "Nº da Adesão" e "Saída", se estiverem vazios, use null.

## 6. Adaptação para outros Projetos de Digitalização de Manuscritos

Este agente pode ser facilmente adaptado para atender a diferentes formatos de formulários. Caso necessário, o prompt pode ser ajustado para se adequar às especificidades do seu projeto. Ele é capaz de extrair informações manuscritas de diversos tipos de documentos e alocá-las automaticamente em uma planilha estruturada, facilitando a digitalização e organização de dados.

## 7. Contribuições

Sinta-se à vontade para sugerir melhorias ou propor modificações. Contribuições são sempre bem-vindas!
