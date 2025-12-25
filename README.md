# Observabilidade App

Bem-vindo ao **observabilidade-app**. Este projeto é uma solução focada em observabilidade, integrando uma aplicação backend Java com uma stack de monitoramento no Grafana, equipada com plugins avançados para traces, logs, métricas e profiling.

## 📂 Estrutura do Projeto

*   **`app/`**: Contém o código fonte da aplicação backend. É um projeto Java gerenciado via Maven (inclui wrapper `mvnw`).
*   **`grafana/`**: Contém configurações e plugins para a instância do Grafana.

## 🚀 Tecnologias e Componentes

O projeto utiliza as seguintes ferramentas:

*   **Backend**: Java (Maven)
*   **Banco de Dados**: MySQL
*   **Proxy Reverso**: Nginx
*   **Monitoramento e Alertas**: Prometheus, Alertmanager
*   **Visualização**: Grafana
*   **Plugins de Observabilidade**:
    *   `grafana-exploretraces-app`: Visualização e exploração de traces distribuídos.
    *   `grafana-lokiexplore-app`: Integração com Loki para análise de logs.
    *   `grafana-metricsdrilldown-app`: Ferramenta para aprofundamento (drill-down) em métricas.
    *   `grafana-pyroscope-app`: Integração com Pyroscope para Continuous Profiling (perfilamento contínuo).

## 🛠️ Como Executar

### Pré-requisitos

*   Docker e Docker Compose instalados.

### Iniciando a Aplicação

Para iniciar toda a stack de serviços (App, Banco de Dados, Monitoramento), execute o seguinte comando na raiz do projeto:

```bash
docker compose up -d
```

**Linux/macOS:**
```bash
cd app
# Certifique-se de que o script mvnw tem permissão de execução
./mvnw clean install
./mvnw spring-boot:run
```

### 2. Grafana

Para carregar os plugins incluídos neste projeto, inicie o Grafana apontando o diretório de plugins para a pasta `grafana/plugins`.

Exemplo com Docker:

```bash
docker run -d -p 3000:3000 --name=grafana \
  -v "$(pwd)/grafana/plugins:/var/lib/grafana/plugins" \
  grafana/grafana
```

Após iniciar, acesse `http://localhost:3000` e configure seus Data Sources para conectar à aplicação.
