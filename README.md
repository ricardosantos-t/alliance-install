## Bem vindo(a) a nossa área de downloads

Essa página tem por objetivo, descrever os pré-requisitos e apoiar no processo de instalação do módulo **WTT Alliance - Lite Image v0.5**.

### Pré-Requisitos (mínimo de hardware)
- SO: Windows 7 PRO ou superior
- Memória: 8GB ou superior
- HD: 100GB ou superior (particionado)
- C:\ 30GB (Somente S.O.)
- D:\ 70GB (Somente dados da aplicação)
- _Caso o sistema deva funcionar no mesmo equipamento do DServer, atente-se aos pré-requisitos do DServer._

### Pré-Requisitos (software)
- NodeJS v10 ou superior
- Banco de dados PostgreSQL 9.4+
- Instalação do módulo DServer

Uma vez que os pré-requisitos estejam atendidos, siga os passos abaixo para iniciar o processo de instalação do módulo “WTT Alliance - Lite Image v0.5”.

| Versões | Descrição | Download | Releases
|:-------------|:------------------|:----------------|:----------------|
| 0.5.1 - Full | Com node_module | http://google.com.br | .... |
| 0.5.1 - Partial | Sem node_module | http://google.com.br | ..... |

1. Faça o download da versão mais recente (preferencialmente partial).
2. Extraia o arquivo no local com maior espaço (exemplo: D:\WTT\Alliance\lite-image).
3. Entre na pasta extraída através do **prompt de comando (modo administador)**.
4. Execute o comando: `> node -v` se a versão do nodejs não for exibida, significa que o NodeJS ainda não foi instalado, então baixe ele [aqui](https://nodejs.org/dist/v12.13.1/node-v12.13.1-x64.msi) e prossiga com a instalação do NodeJS.
5. Repita o passo 4 para certificar-se de que o NodeJS esteja realmente pronto para ser usado.
6. Ainda na pasta extraída no passo 2, edite o arquivo **configuration.json**, aqui você poderá modificar a porta de execução e conexões com banco de dados da aplicação e dserver, altere os valores conforme o necessário, salve e feche o arquivo.
7. Ainda na pasta extraída, execute o comando `> node server --createdb` será criado o banco de dados da aplicação.
8. Ainda na pasta extraída, execute o comando `> node server --install` um serviço (WTT Alliance - Lite Image v0.5) será instalado no windows, iniciado e uma página de configuração será exibida.
9. Na página de configuração, atente-se para os parâmetros de porta da aplicação e conexão com banco de dados.

### Comandos Suportados
- Instala o serviço no windows
```markdown
> node server --install
```

- Desinstala o serviço do windows
```markdown
> node server --uninstall
```

- Inicia o serviço do windows
```markdown
> node server --start
```

- Interrompe o serviço do windows
```markdown
> node server --stop
```

- Executa a aplicação sem iniciar o serviço do windows
```markdown
> node server --run
```

- Cria o banco de dados da aplicação
```markdown
> node server --createdb
```

- Abre aplicação no browser
```markdown
> node server --open
```
