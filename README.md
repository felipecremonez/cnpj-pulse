# 🏢 CNPJ Pulse Enterprise

> **Plataforma Web Avançada para Inteligência e Consulta Cadastral de Pessoas Jurídicas**

O **CNPJ Pulse Enterprise** é uma solução *front-end* de alta performance desenvolvida para consulta, validação e análise de dados cadastrais de empresas brasileiras diretamente da base de dados da Receita Federal. 

Projetado com foco em experiência do usuário (UX), acessibilidade e alta disponibilidade, o projeto elimina a dependência de um servidor *back-end* próprio através de uma arquitetura resiliente de consumo direto de APIs públicas.

---

## 📸 Recursos em Destaque

- ⚡ **Consulta Instantânea & Validação Matemática:** Validação do dígito verificador do CNPJ via algoritmo oficial antes do envio da requisição, evitando chamadas desnecessárias à rede.
- 🔄 **Arquitetura Resiliente com Fallback Automático:** Integração encadeada entre fontes primárias e secundárias (**BrasilAPI** $\rightarrow$ **Minha Receita**) que garante alta taxa de sucesso nas respostas.
- 🎨 **Interface Corporativa & Dark Mode:** Design profissional, responsivo e adaptativo construído com Tailwind CSS e biblioteca de ícones Phosphor.
- 🗂️ **Visualização Categorizada por Abas:**
  - **Visão Geral & Contato:** Dados de abertura, capital social, endereço com link inteligente para o Google Maps e contatos oficiais.
  - **Atividades Econômicas (CNAE):** Separação clara entre atividade principal e secundárias.
  - **Quadro de Sócios e Administradores (QSA):** Listagem de integrantes e suas respectivas qualificações.
- 💾 **Histórico Local Persistente:** Armazenamento das consultas recentes via `localStorage` para re-consulta em um clique.
- 📄 **Exportação & Impressão Otimizada:** Função de cópia formatada em um clique e suporte a CSS Print para geração de relatórios limpos em PDF.

---

## 🛠️ Arquitetura & Funcionamento Técnico

```
                   +------------------------+
                   | Entrada do CNPJ pelo   |
                   |       Usuário          |
                   +-----------+------------+
                               |
                               v
                   +------------------------+
                   |  Validação de Máscara  |
                   |   e Algoritmo (DV)     |
                   +-----------+------------+
                               |
                    [ Válido? ]-+--> (Não) --> Exibe mensagem de erro
                               |
                             (Sim)
                               v
                   +------------------------+
                   | Requisição à BrasilAPI |
                   +-----------+------------+
                               |
                     [ Sucesso? ]-+--> (Sim) --> Renderiza Interface
                               |
                             (Não)
                               v
                   +------------------------+
                   | Fallback: Requisição à |
                   |     Minha Receita      |
                   +-----------+------------+
                               |
                     [ Sucesso? ]-+--> (Sim) --> Renderiza Interface
                               |
                             (Não) --> Exibe alerta de falha nas fontes
```

---

## 📦 Estrutura do Projeto

O projeto adota uma arquitetura de **Arquivo Único (Single-File Application)**, consolidando marcação, estilização, ícones e motor de execução em um único arquivo HTML super otimizado:

```text
cnpj-pulse-enterprise/
├── index.html        # Aplicação completa (HTML5 + Tailwind CSS + JavaScript ES6+)
└── README.md         # Documentação do projeto
```

---

## 🚀 Como Executar o Projeto

Como a aplicação é 100% *client-side*, **não é necessário instalar dependências ou configurar servidores Node.js/Python**.

### Execução Local:
1. Faça o download ou clone este repositório:
   ```bash
   git clone https://github.com/SEU-USUARIO/cnpj-pulse-enterprise.git
   ```
2. Navegue até a pasta do projeto e abra o arquivo `index.html` em qualquer navegador moderno (Chrome, Firefox, Edge, Safari).

---

## 🌐 Publicação no GitHub Pages

Para disponibilizar a aplicação gratuitamente na web:

1. Acesse as configurações do seu repositório no GitHub (**Settings**).
2. Na barra lateral, selecione **Pages**.
3. Em **Branch**, selecione `main` e a pasta `/ (root)`.
4. Clique em **Save**.
5. Em instantes, seu projeto estará online na URL:  
   `https://<seu-usuario>.github.io/cnpj-pulse-enterprise/`

---

## ⚖️ Conformidade e Privacidade

- **LGPD (Lei Geral de Proteção de Dados):** O sistema apenas consulta e exibe informações públicas fornecidas pela Secretaria da Receita Federal do Brasil.
- **Privacidade de Dados:** Nenhum dado pesquisado é enviado a servidores externos além das APIs oficiais de consulta pública. O histórico de buscas permanece gravado unicamente no navegador do próprio usuário (`localStorage`).

---

## 📄 Licença

Este projeto está licenciado sob a licença **MIT** — sinta-se à vontade para utilizar, modificar e distribuir.