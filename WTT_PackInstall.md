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



### Instalação e configuração dos Pré-Requisitos (software) 


<details><summary> Instalação do PostgreSQL 9.4+ </summary>
<h5> Download PostgreSQL 9.4! </h5>
<ol>
<li> No arquivo baixado acima, encontra-se o instalador e manual de instalação e configuração.</li>
<li> Install postgres, remove flag "launch stack Builder at exit?"</li>
<li> Criar banco de dados</li>
 <li>  Criar table space com nome WTTDSERVER, apontando para o diretório DB do dserver ex. C:\WTT\dserver\Db</li>
 <li>  Criar Database com nome WTTDSERVER</li>

</ol>
</details>


<details><summary> Instalação do ODBC </summary>
<h3>
#### Download ODBC!
	</h3>
<p>
```python
No arquivo baixado acima, encontra-se o instalador e manual de instalação e configuração.```
Efetue a instalação do ODBC.```
Configure ODBC, adicionando Postgres ANSI e configurando conexão com Dserver.
```

</p>
</details>



<details><summary> Instalação do módulo D-Server </summary>
<p>


#### Download D-Server!

```python
	1. No arquivo baixado acima, encontra-se o instalador e manual de instalação e configuração.
	2. Criar pasta "WTT" na raiz do diretório desejado.
	3. Copiar pasta dserver para dentro da pasta WTT, criada anteriormente.
	4. Configurar dserver
	 - Instalar o serviço do dserver
	 - Ativar Dserver
	 - Cria pastar "C:\WTT\storage\dcmimport"
	 - Marcar flag "habilitar importação de arquivos dicom"
```

</p>
</details>



<details><summary> Instalação do módulo DSWeb </summary>
<p>

#### Download DSWeb!

```python
	1. No arquivo baixado acima, encontra-se o instalador e manual de instalação e configuração.
	1. Ativar IIS 
	2. Instalar urlrewrite2.exe (**Download [])
	3. Configurar IIS
	 	3.1. na raiz (primeiro item da coluna esquerda), seleciona Restrições ISAPI e CGI e clica em Editar configurações de recurso 	e marca a opção: Permitir módulos CGI não especificado.

	 	3.2. Mapeamentos de manipulador (seleciona CGI > botão direito, seleciona Editar Permissões de Recurso > Marcar opção executar )
	 	
	 	3.3. Default Web Site ( adicionar novo diretório virtual > Alias: STORAGE, Caminho fisico "c:\WTT\storage"´> conectar como: selecionar usuário WTTService  )

	 	3.4. Default Web Site ( adicionar novo diretório virtual > Alias: dsweb, Caminho fisico "c:\WTT\Dserver\Web"´> conectar como: selecionar usuário WTTService  )

		3.5. Default Web Site > dsweb ( URL Rewrite . Add Rules > Blank Rule > name: dsweb.exe | Pattern: .* | conditions: selecona lista em logical Grouping: Match Any, clica em ADD, check if ainput string: Is Not a File, confirma | em 		Rewrite URL informa o valor: dsweb.exe/{R:0} | Aplicar  )

	 	3.6. Teste: http://127.0.0.1/dsweb/version (Deve apresentar a versão do dsweb)

	 	3.7. Default Web Site > Storage ( selecionar Tipos de MIME e adicionar extenção .data (binary/dat), .dcm (binary/dcm) )

	    3.8. Rodar script headers.cmd com permissão de ADM 
```

</p>
</details>


<details><summary> Instalação do NodeJS v10+ </summary>
<p>

#### Download NodeJS v10+!

```python
	1. No arquivo baixado acima, encontra-se o instalador e manual de instalação e configuração.
	2. Executar o instalado em modo ADM

```

</p>
</details>



<p></p>


### Instalação e configuração do WTT Alliance - Lite Image


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
