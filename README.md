# Discord Bot - Tech Girls

> [!NOTE]
> **Projeto em Desenvolvimento / Fase de Ajustes:** Este repositório encontra-se atualmente em fase de testes e integração.

## Objetivo

Bot do Discord para a comunidade Tech Girls, desenvolvido para automatizar a analise e o envio de notícias de tecnologia relevantes utilizando Web Scraping, Inteligência Artificial (Google Gemini) e agendamento de tarefas.

---

## 👥Equipe do Projeto e Atribuicoes

O projeto foi construído de forma colaborativa, onde cada desenvolvedora ficou responsável por um pilar essencial:

* **Maria Fernanda** (Eu 🚀).
* **Lucila:** Agente de IA. Engenharia de Prompt e Integração com a **IA (Google Gemini)**, além de toda a **Containerização e ambiente Docker** da aplicação.
* **Thais:** Modelagem do **Banco de Dados (SQLite)** e desenvolvimento das **funções do `database.py`** para persistência de dados.
* **Andressa:** Gestão de **Documentação Geral e Completa do Projeto**

---
  
## Sobre este Fork & Minhas Contribuições ✨

Este repositório é um **Fork** focado na implementação e validação da **arquitetura de Tasks, orquestração de comandos Slash e pipeline de entregas do Discord**.

### O que foi desenvolvido por mim:

* **(`news_search.py`):** Coleta e extração assíncrona das notícias diretamente da API/página do TabNews, estruturando os dados para consumo da IA e envio para o banco de dados.
* **(`embeds.py`):** Formatação visual das mensagens no Discord (layout, cores, campos de tags, local para o resumo gerado pela IA e botões com links de acesso direto à matéria).
* **Comando `/setupnews` (`setup_channel.py`):** Criação do comando Slash com validação de permissões de administrador (`administrator=True`) para capturar e vincular o ID do Servidor (`guild_id`) e do Canal (`channel_id`), enviando-os para o banco de dados.
* **Arquitetura & Otimização de Tasks (`TasksBot`):** Projeção do ciclo de vida da rotina em segundo plano. A Task permanece **inativa** por padrão, economizando o uso da API do Gemini enquanto não houver canais cadastrados. O comando `/setupnews` atua como gatilho automático para "acordar" e iniciar a execução (`.start()`) das tasks.
* **Ambiente de Testes Banco de dados "fake" (`TasksTeste`):** Criação testes isolados com banco de dados simulado (*Mock*) e intervalo de execução reduzido, permitindo validar a esteira completa de envio (*Scraping → Análise de IA → Embed no Discord*) sem dependências do banco real.

---

## 🎬 Demonstração do Teste em Execução:

> O vídeo abaixo mostra a validação em tempo real da esteira de testes capturando as notícias, processando via Gemini e disparando os Embeds formatados no Discord:

https://github.com/user-attachments/assets/e741ad56-0175-4e93-a27b-ea04dcbcde49

---

## 🛠️ Tecnologias & Libs Utilizadas

* **Python 3.11**
* **discord.py**: Framework para comandos Slash, Cogs e gerenciamento do Bot.
* **google-generativeai / Gemini API**: Validação, sumarização e categorização do conteúdo das notícias.
* **BeautifulSoup4 / aiohttp**: Web Scraping e requisições assíncronas ao TabNews.
* **python-dotenv**: Gerenciamento de variáveis de ambiente de forma segura.

---

## ⏳ Próximos Passos (Roadmap)
- [ ] Finalização das funções de persistência no database.py.
- [ ] Conexão final do comando /setupnews com a gravação do servidor/canal no SQLite.
- [ ] Migração do ambiente de teste (tasks_teste.py) para o agendador oficial de produção (tasks_bot.py).
- [ ] Validação do build final no ambiente containerizado com Docker.

---

<p align="center">
  Desenvolvido como Desafio para a comunidade <b>Tech Girls</b> 💜
</p>
