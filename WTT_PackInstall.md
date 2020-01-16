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



<details><summary> Instalação do módulo D-Server </summary>
	<p>
	 <h5 style="margin-left: 30px;" font size="14px">
	 	<a href="https://s3-sa-east-1.amazonaws.com/wtt-lite-image-0.5/D-Server.zip"><b>Download D-Server</b></a>
	 </h5>
		<ol>
			<li> No arquivo baixado do link acima, encontra-se o instalador, manual de instalação e configuração.</li>
			<li> Crie uma pasta "WTT" na raiz do diretório local com maior espaço (exemplo: D:\WTT).</li>
			<li> Extrair do arquivo compactado a pasta "dserver", colocando-a dentro da pasta WTT, criada anteriormente. (exemplo: D:\WTT\dserver).</li>
			<li> Executar o programa como Administrador "WTTdserverSvc.exe" dentro da pasta \\wtt\dserver\prg </li>
			<ul>
				<li> ! Caso apresente erro "Run-time error 70 - Permission denied", copie os arquivos localizado na pasta System32 (\WTT\dserver\SYSTEM32) e cole na pasta C:\Windows\SysWOW64 (caso seja windows 64bits), abra o Prompt de comando em modo administrador e utilize os comandos abaixo para registrar as DLLs: 
					<li> C:\Windows\SysWOW64>regsvr32 MSCOMCTL.OCX </li>
					<li> C:\Windows\SysWOW64>regsvr32 MSSTDFMT.DLL </li>
				    <li> C:\Windows\SysWOW64>regsvr32 NTSVC.ocx </li>
				  	<li> C:\Windows\SysWOW64>regsvr32 tabctl32.ocx </li>
			  	</li>
		  	</ul>
			<li> Na aba configurações (user: admin, Key: wttsolution) > avançado > clique em; Instalar serviço.</li>
			<li> Ativar Dserver.</li>
			<li> Na aba configurações (user: admin, Key: wttsolution) > Servidor > Marcar flag "habilitar importação de arquivos dicom".</li>
			<li> Na raiz da pasta "WTT", crie uma pasta "storage" dentro dela crie uma pasta "dcmimport" (exemplo: C:\WTT\storage\dcmimport).</li>
			<li> Instale o Postgres e retorne ao D-Server para configurar a comunicação com o banco de dados.</li>
		</ol>
	</p>
</details>



<details><summary> Instalação do PostgreSQL 9.4+ </summary>
	<p>
	 <h5 style="margin-left: 30px;" font size="14px">
	 	<a href="https://s3-sa-east-1.amazonaws.com/wtt-lite-image-0.5/Postgres.zip"><b>Download PostgreSQL 9.4</b></a>
	 </h5>
		<ol>
			<li> No arquivo baixado do link acima, encontra-se o instalador, manual de instalação e configuração.</li>
			<li> Crie uma pasta "suporte" na raiz da pasta "WTT" e extraia o arquivo compactado na pasta Suporte (exemplo: D:\WTT\suporte\postgres).</li>
			<li> Execute como Administrador o instalador "postgresql-9.4.5-1-windows-x64.exe" e na última tela, remova a flag "launch stack Builder at exit?" apresentada no final da instalação </li>
			<li> Abrir Pagadmim, clique em PostgreSQL, informe a senha criada anteriormente.</li>
			<li> Crie table space com nome "WTTDSERVER", Owner "postgres", na aba Definition informe o diretório DB do dserver (exemplo: C:\WTT\dserver\Db).</li>
			<li> Crie Database com nome "WTTDSERVER", Owner "postgres", em Definition seleciona a table space "WTTDSERVER", na aba Variables Selecione standard_conforming_strings, marca o box "Variable value"e clica em ADD/change, clicar em ok.</li>
			<li> Selecione a Database "WTTDSERVER", clique em SQL, informe o script padrão do banco de dados (.txt disponibilizado no arquivo baixado), e clique em "execute query" (botão play).</li>
			<li> Instale o ODBC (disponibilizado abaixo) e efetue a configuração. </li>
		</ol>
	</p>
</details>



<details><summary> Instalação do ODBC </summary>
	<p>
	 <h5 style="margin-left: 30px;" font size="14px">
	 	<a href="https://s3-sa-east-1.amazonaws.com/wtt-lite-image-0.5/ODBC.zip"><b>Download ODBC</b></a>
	 </h5>
		<ol>
			<li> No arquivo baixado do link acima, encontra-se o instalador, manual de instalação e configuração.</li>
			<li> Extraia o arquivo compactado na pasta Suporte (exemplo: D:\WTT\suporte\ODBC).</li>
			<li> Execute como Administrador o instalador "psqlodbc-setup.exe".</li>
			<li> Abra o ODBC, na aba "DNS de Sistema" clique em adincionar > selecione PostgreSQL ANSI e configure os dados referente as tabelas WTTDSERVER.</li>
			<li> Reinicie a maquina. </li>
			<li> Configure no D-Server o banco de dados criado, seguindo manual de configuração do do D-Server</li>
		</ol>
	</p> 
</details>



<details><summary> Instalação do módulo DSWeb </summary>
	<p>
	 <h5 style="margin-left: 30px;" font size="14px">
	 	<a href="https://s3-sa-east-1.amazonaws.com/wtt-lite-image-0.5/DsWeb.zip"><b>Download DSWeb</b></a>
	 </h5>
		<ol>
			<li> No arquivo baixado do link acima, encontra-se o instalador e manual de instalação e configuração. </li>
			<li> Extraia o arquivo compactado na pasta Suporte (exemplo: D:\WTT\suporte\DsWeb).</li>
			<li> Installar o IIS em recursos do windows e garantir que a opção CGI esteja marcada. (IIS > Serviços da World Wide Web > Recursos de Desenvolvimento de Aplicativos > CGI). </li>
			<li> Criar o usuário wttservice (local) em gerenciamento do computador e definir com perfil de administrador. </li>
			<li> Na raiz do IIS (primeiro item da coluna esquerda), seleciona "Restrições ISAPI e CGI" e clica em "Editar configurações de recurso" e marca a opção: Permitir módulos CGI não especificado. </li>
			<li> Execute como Administrador o arquivo “headers.cmd”. Esse arquivo adicionará no diretório virtual STORAGE, uma configuração dentro de “Cabeçalhos de Resposta HTTP”.</li>
			<li> Execute como Administrador o instalador "urlrewrite2.exe". </li>
			<li> No IIS "Default Web Site" criar diretório virtual “DSWEB”  (adicionar novo diretório virtual > Alias: “DSWEB”, Caminho fisico "c:\WTT\Dserver\Web"´> conectar como: selecionar usuário WTTService). </li>
			<li> Dentro do diretório virtual DSWEB, abra a opção “Mapeamentos de Manipulador” e clique em “Editar permissões de recurso”. Adicione a permissão “Executar”. </li>
			<li> Dentro do diretório virtual DSWEB, abra a opção “URL Rewrite” > Add Rule(s)... 
				<ul>
				<li> Inbound rules - Blank rule - Preencha os seguintes campos: </li>
				<li> - Name: DsWeb.exe </li>
				<li> - Requested URL: Matches the Pattern </li>
				<li> - Using: Regular Expressions </li>
				<li> - Pattern: .* </li>
				<li> - Ignore case: habilitado </li>
				<li> - Expanda a sessão “Conditions” e preencha o seguinte campo: </li>
				<li> - Logical grouping: Match Any </li>
				<li> - Clique em “Add...” e preencha os seguintes campos: </li>
				<li> - Check if input string: Is Not a File </li>
				<li> - Condition input: {REQUEST_FILENAME}</li>
				<li> - Atenção: se a opção “Is Not a File” não estiver aparecendo, confira se na instalação do IIS foi adicionada a opção “ASP” ou “ASP.net”. </li>
				<li> - Clique em “OK” para salvar e fechar a condição criada. </li>
				<li> - Expanda a sessão “Action” e preencha os seguintes campos: </li>
				<li> - Action type: Rewrite </li>
				<li> - Rewrite URL: DsWeb.exe/{R:0} </li>
				<li> - Append query string: habilitado </li>
				<li> - Clique em “Aplicar” no menu do lado direito para salvar a regra. </li>
				<li> - Para verificar se o diretório virtual foi criado corretamente e está acessível, acesse o seguinte endereço no navegador:  </li>
				<li> - http://localhost:porta/DsWeb/version ou http://IP_SERVIDOR:PORTA/DsWeb/version.  No Chrome e no Firefox, deve exibir uma página com a versão do DsWeb. No Internet Explorer, deve exibir uma mensagem perguntando se deseja salvar o arquivo “version.json”. Salve o arquivo e abra com o bloco de notas, o conteúdo deve ser um texto mostrando a versão do DsWeb. </li>
				</ul>
			</li>
			<li> Default Web Site ( adicionar novo diretório virtual > Alias: STORAGE, Caminho fisico "c:\WTT\storage"´> conectar como: selecionar usuário WTTService  ) </li>
			<li> Default Web Site > Storage ( selecionar Tipos de MIME e adicionar extenção .dat (binary/dat), .dcm (binary/dcm) ) </li>
			<li> Teste: http://127.0.0.1/dsweb/version (Deve apresentar a versão do dsweb) </li>
		</ol>
	</p>
</details>



<details><summary> Instalação do NodeJS v10+ </summary>
	<p>
	 <h5 style="margin-left: 30px;" font size="14px">
		 <a href="https://s3-sa-east-1.amazonaws.com/wtt-lite-image-0.5/NodeJs.zip"><b>Download NodeJS v10+</b></a>
	 </h5>
		<ol>
			<li> No arquivo baixado do link acima, encontra-se o instalador e manual de instalação e configuração. </li>
			<li> Executar o instalado em modo ADM. </li>
		</ol>
	</p>
</details>



<details><summary> Artefatos de Testes </summary>
	<p>
	 <h5 style="margin-left: 30px;" font size="14px">
	 	<a href="https://s3-sa-east-1.amazonaws.com/wtt-lite-image-0.5/Massa+de+Testes.zip"><b>Download Artefatos de Testes</b></a>
	 </h5>
		<ol>
			<li> No arquivo baixado do link acima, encontra-se artefatos para apoiar os testes pós instalação. </li>
		</ol>
	</p>
</details>




_ _

### Instalação e configuração do WTT Alliance - Lite Image


Uma vez que os pré-requisitos estejam atendidos, siga os passos abaixo para iniciar o processo de instalação do módulo “WTT Alliance - Lite Image v0.5”.

| Versões | Descrição | Download | Releases
|:-------------|:------------------|:----------------|:----------------|
| 0.5.4 - Partial | Requer internet (recomendado) | [Baixar](https://github.com/WTT-TECNOLOGIA/alliance-install/blob/master/wtt-alliance-lite-image-v0.5.4.zip?raw=true) | .... |


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


_ _
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
