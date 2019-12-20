## Bem vindo(a) a nossa área de downloads

Essa página tem por objetivo, descrever os pré-requisitos e apoiar no processo de instalação do módulo **WTT Alliance - Lite Image v0.5**.

Documentação: https://wtt-tecnologia.github.io/alliance-install/

### Pré-Requisitos (mínimo de hardware)
- SO: Windows 7 PRO ou superior
- Memória: 8GB ou superior
- HD: 100GB ou superior (particionado)
- C:\ 30GB (Somente S.O.)
- D:\ 70GB (Somente dados da aplicação)
- _Caso o sistema deva funcionar no mesmo equipamento do DServer, atente-se aos pré-requisitos do DServer._

### Pré-Requisitos (software) | [Baixar Pacote](https://s3-sa-east-1.amazonaws.com/wtt-lite-image-0.5/pre-install.zip) | [Manual](https://wtt-tecnologia.github.io/alliance-install/dsweb)
- NodeJS v10 ou superior
- Banco de dados PostgreSQL 9.4+
- Instalação do módulo DServer
- Instalação do módulo DSWeb

Uma vez que os pré-requisitos estejam atendidos, siga os passos abaixo para iniciar o processo de instalação do módulo “WTT Alliance - Lite Image v0.5”.

| Versões | Descrição | Download | Releases
|:-------------|:------------------|:----------------|:----------------|
| 0.5.2 - Partial | Requer internet (recomendado) | [Baixar](https://github.com/WTT-TECNOLOGIA/alliance-install/blob/master/wtt-alliance-lite-image-v0.5.2.zip) | .... |
| 0.5.1 - Partial | Requer internet (recomendado) | [Baixar](https://github.com/WTT-TECNOLOGIA/alliance-install/raw/master/wtt-alliance-lite-image-v0.5.1.zip) | .... |

1. Faça o download da versão mais recente (preferencialmente partial).
2. Extraia o arquivo no local com maior espaço (exemplo: D:\WTT\Alliance\lite-image).
3. Entre na pasta extraída através do **prompt de comando (modo administador)**.
4. Execute o comando: `> node -v` se a versão do nodejs não for exibida, significa que o NodeJS ainda não foi instalado, então baixe ele [aqui](https://nodejs.org/dist/v12.13.1/node-v12.13.1-x64.msi) e prossiga com a instalação do NodeJS.
5. Repita o passo 4 para certificar que o NodeJS esteja realmente pronto para ser usado.
6. Ainda na pasta extraída, execute o comando `> npm install` para baixar e/ou atualizar as dependências do sistema, nesse momento você deverá ter internet disponível, caso contrário utilize a versão "full" do instalador (recomendamos a versão partial).
7. Ainda na pasta extraída, renomeie o arquivos **configuration-sample.json** para **configuration.json** e edite esse arquivo, aqui você poderá modificar a porta de execução e conexões com banco de dados da aplicação e dserver, altere os valores conforme necessário, salve e feche o arquivo.
8. Ainda na pasta extraída, execute o comando `> node server --install` um serviço (WTT Alliance - Lite Image v0.5), será instalado no windows e iniciado, caso o banco de dados não exista ele será criado e a aplicação será carregada no browser.
9. Caso o browser não seja carregado automaticamente, execute o comando `> node server --open` ele irá forçar a abertura do navegador direcionado para url da aplicação.
10. Após instalação atentar-se para as devidas configurações do sistema, tais como:
- NetworkID da instituição - alterar diretamente na tabela "ali_sites".
- URL de apontamento para o DSWEB - Disponível em configurações do site, refletindo na tabela "ali_site_configurations".
- Definir data de início da importação (importante) - Disponível em configurações do site, refletindo na tabela "ali_site_configurations".

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
