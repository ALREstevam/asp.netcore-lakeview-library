# Projeto Lakeview Library
* Parte 1: https://www.youtube.com/watch?v=WTVcLFTgDqs&index=1&list=PL3_YUnRN3UhiQLW92PItnytGRFRNXkb2G
* Parte 2: https://www.youtube.com/watch?v=7rcCfCdiB9A&index=2&list=PL3_YUnRN3UhiQLW92PItnytGRFRNXkb2G
* Parte 3: https://www.youtube.com/watch?v=iE6f7QjVmww&index=3&list=PL3_YUnRN3UhiQLW92PItnytGRFRNXkb2G
* Parte 4: https://www.youtube.com/watch?v=u8uAoKTplWQ&index=4&list=PL3_YUnRN3UhiQLW92PItnytGRFRNXkb2G

# Problemas e Soluções
* O projeto deverá usar o template `Web Aplicattion (Model-View-Controller)` e não (`Web Aplicattion`)

# Notas
## `wwwroot`
* O diretório `wwwroot` é utilizado para guardar arquivos estáticos como imagens, javascript, css, bibliotecas de terceiros, bootstrap, jquery etc.

## Routes
* No seguinte código:
***Startup.cs***

		...
		app.UseMvc(routes =>
		            {
		                routes.MapRoute(
		                    name: "default",
		                    template: "{controller=Home}/{action=Index}/{id?}");
		            });
		...i

é feita a definição de rotas, a rota `defaullt` irá acessar o `HomeController` e executar a ação `Index` com um parâmetro opcional `id` pois está marcado com `?`.


## Configurações
* As configurações da aplicação são feitas no `Startup.cs`, no construtor, usando um objeto da classe `ConfigurationBuilder` 

* A configuração é feita via arquivos `.json` ligados ao objeto de configuração com o método `AddJsonFile(...)`

* O método `AddEnviromentVariables()`   permite adicionar variáveis como strings de conexão a um banco de dados, senhas etc

> *Variável de ambiente geralmente contém informações sobre o sistema, caminhos de diretórios específicos no sistema de arquivos e as preferências do utilizador. Ela pode afetar a forma como um procedimento se comporta.*
> 
## Serviços
Serviços são objetos que contém alguma funcionalidade para outra parte da aplicação que podem ser injetados em outras classes, por exemplo:
se no banco houver uma tabela `books` e no sistema uma classe `BookController` pode-se criar um serviço para lidar com o banco e injetá-lo no `BookController`,  assim o controller não terá que lidar com um `DbContext` mas pedirá para o serviço que o faça.

Construindo a aplicação desta forma, se a forma de armazenamento de dados mudar, basta criar um novo objeto que realize o serviço de lidar com esses dados, o controller não precisará ser alterado (nem mesmo ao fazer o `new` já que esse objeto é uma injeção de dependências)