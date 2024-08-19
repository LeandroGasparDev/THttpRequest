#Visão Geral

THttpRequest é uma classe desenvolvida em Delphi, projetada para simplificar o processo de realização de requisições HTTP/REST. 
Ela oferece uma interface flexível e fácil de ser implementada, permitindo o envio de requisições HTTP/REST (GET, POST, PUT, DELETE) e a manipulação das respostas recebidas.

Funcionalidades:
- Suporte a Métodos HTTP: Suporta os métodos GET, POST, PUT e DELETE através da enumeração THttpMethod.
- Cabeçalhos Personalizáveis: Gerencie facilmente os cabeçalhos HTTP/REST com a classe THeaders.
- Manipulação de Respostas: A classe TResponse encapsula os dados da resposta HTTP/REST, incluindo o código de status, o texto da resposta e os cabeçalhos.
- Interface Fluente: Métodos encadeáveis para configurar os parâmetros da requisição, tornando a classe fácil de usar.

Exemplo de Uso:
- delphi - Copiar código
	var
	  Request: THttpRequest;
	  Response: TResponse;
	begin
	  Request := THttpRequest.New
		.SetUrl('https://api.example.com/data')
		.SetMethod(mmGet)
		.SetContentType('application/json');

	  Response := Request.Execute;
	  try
		ShowMessage(Response.ResponseCode);
		ShowMessage(Response.ResponseText);
	  finally
		Response.Free;
	  end;
	end;
	
Instalação:
- Adicione a unit uHttpRequest ao seu projeto Delphi.
- Certifique-se de que as units necessárias (System.SysUtils, System.Classes, etc.) estão disponíveis no seu projeto.

Notas:
- O método Execute utiliza o objeto COM WinHttp.WinHttpRequest.5.1 para realizar as requisições HTTP.
- Um tratamento adequado de erros deve ser implementado para lidar com exceções durante as requisições HTTP.
