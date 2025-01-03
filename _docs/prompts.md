# Documentação da API Mega Man

## Descrição do Projeto
Esta API foi desenvolvida em **.NET Core 3.1** para listar informações sobre os chefes do jogo **Mega Man**. Seu principal objetivo é fornecer dados no formato JSON, permitindo integração com outras aplicações ou frontends. O formato de resposta dos dados segue o exemplo abaixo:

```json
{
  "Id": 1,
  "Code": "DLN/DRN-003",
  "Name": "Cutman",
  "HP": 150,
  "Picture": "https://vignette.wikia.nocookie.net/megaman/images/2/22/Cutman.png"
}
```

---

## Especificações do Projeto
Segue a configuração do arquivo de projeto principal `MegamanApi.csproj`:

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.EntityFrameworkCore" Version="3.1.8" />
    <PackageReference Include="Microsoft.EntityFrameworkCore.Design" Version="3.1.8">
      <IncludeAssets>runtime; build; native; contentfiles; analyzers; buildtransitive</IncludeAssets>
      <PrivateAssets>all</PrivateAssets>
    </PackageReference>
    <PackageReference Include="Microsoft.EntityFrameworkCore.SqlServer" Version="3.1.8" />
    <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
  </ItemGroup>

</Project>
```

---

## Dependências do Projeto
As principais dependências utilizadas no projeto estão listadas na tabela abaixo:

| Dependência                          | Versão  | Descrição                                                                                     |
|---------------------------------------|----------|-------------------------------------------------------------------------------------------------|
| [Microsoft.EntityFrameworkCore](https://docs.microsoft.com/en-us/ef/core/)        | 3.1.8    | Provedor ORM para interação com o banco de dados.                                              |
| [Microsoft.EntityFrameworkCore.Design](https://docs.microsoft.com/en-us/ef/core/) | 3.1.8    | Suporte a ferramentas para design de banco de dados.                                            |
| [Microsoft.EntityFrameworkCore.SqlServer](https://docs.microsoft.com/en-us/ef/core/providers/sql-server/) | 3.1.8    | Provedor para SQL Server.                                                                       |
| [Newtonsoft.Json](https://www.newtonsoft.com/json)             | 12.0.2   | Biblioteca para serialização e desserialização de JSON.                                      |

---

## Estrutura do Projeto
O projeto segue a seguinte estrutura de diretórios:

```
.vs/
.vscode/
bin/
Controllers/
Database/
middlewares/
Models/
obj/
Properties/
Services/
appsettings.Development.json
appsettings.json
global.json
MegamanApi.csproj
MegamanApi.sln
Program.cs
Startup.cs
```

### Descrição dos Principais Diretórios
- **Controllers/**: Contém os controladores responsáveis por definir os endpoints da API.
- **Database/**: Gerencia conexões e mapeamentos com o banco de dados.
- **middlewares/**: Implementação de middlewares para gerenciar o pipeline de requisições.
- **Models/**: Define as classes e modelos de dados da aplicação.
- **Services/**: Contém a lógica de negócio e os serviços utilizados pelos controladores.

---

## Endpoints Disponíveis

### **GET** `/api/v1/robots`
Lista todos os robôs disponíveis.

**Resposta**:
```json
[
  {
    "Id": 1,
    "Code": "DLN/DRN-003",
    "Name": "Cutman",
    "HP": 150,
    "Picture": "https://vignette.wikia.nocookie.net/megaman/images/2/22/Cutman.png"
  }
]
```

---

### **GET** `/api/v1/robots/{id}`
Obtém detalhes de um robô pelo seu ID.

**Resposta Sucesso**:
```json
{
  "Id": 1,
  "Code": "DLN/DRN-003",
  "Name": "Cutman",
  "HP": 150,
  "Picture": "https://vignette.wikia.nocookie.net/megaman/images/2/22/Cutman.png"
}
```

**Resposta Erro**:
```json
{
  "message": "Nenhum robo encontrado"
}
```

---

### **POST** `/api/v1/robots`
Adiciona um novo robô. (Implementação prevista para futuras melhorias.)

**Resposta**:
```json
{
  "status": "success"
}
```

---

## Técnicas e Padrões Utilizados
- **Dependency Injection (DI)**: Facilita o gerenciamento de dependências e aumenta a manutenção do código.
- **Entity Framework Core**: Utilizado como ORM para abstrair o acesso ao banco de dados.
- **Clean Architecture**: Organização do projeto em camadas para separar responsabilidades.
- **RESTful API**: Padrão utilizado para definição dos endpoints da API.
- **JSON**: Padrão de troca de informações entre API e consumidores.

---

## Configuração e Execução

1. **Clone o repositório:**
   ```bash
   git clone https://github.com/seu-usuario/MegamanApi.git
   ```

2. **Instale as dependências:**
   Certifique-se de ter o SDK do .NET Core 3.1 instalado.
   ```bash
   dotnet restore
   ```

3. **Configure a aplicação:**
   Atualize os arquivos `appsettings.json` com as credenciais do banco de dados.

4. **Execute a API:**
   ```bash
   dotnet run
   ```

5. **Acesse a API:**
   A API estará disponível em: `http://localhost:5000/api/v1/robots`

---

## Licença
Este projeto está licenciado sob a [MIT License](https://opensource.org/licenses/MIT).


