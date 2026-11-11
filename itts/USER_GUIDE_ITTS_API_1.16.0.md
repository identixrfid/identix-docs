# ITTS API – Guia do Integrador

Este documento apresenta a **API REST**, seus principais recursos e orientações necessárias para integração com sistemas externos.

O objetivo é fornecer aos integradores uma visão geral da API, incluindo seus recursos, endpoints, autenticação, formatos de requisição e resposta, regras de integração e demais informações necessárias para utilização dos serviços disponibilizados pelo ITTS.

---

## 1. Autenticação

A autenticação na API do ITTS é realizada por meio da geração de um **token de acesso**, obtido a partir de credenciais válidas de usuário.

```http
POST | api/itts/register
```

Body
- x-www-form-urlencoded
- username: abcd_name
- password: passpass
- grant_type: password

Exemplo payload resposta:

```json
{
    "access_token": "<token_de_acesso>",
    "token_type": "bearer",
    "expires_in": 3599
}
```

Observações Importantes:
- O token tem validade limitada (1 hora);
- Tokens expirados ou inválidos retornam HTTP 401 – Unauthorized;
- Recomenda-se armazenar o token de forma segura no cliente.

---

## 2. Status

Para obter o status da API:

```http
GET | api/itts/status
```

Exemplo payload resposta:

```json
{
    "serviceStatus": "is Running",
    "version": "1.4.0"
}
```

---

## 3. Devices

Permite obter a relação de devices registrados.

```http
GET | api/devices
```

Exemplo payload resposta:

```json
[
    {
        "id": "303da130-2487-4141-bb93-e30b882dd724",
        "name": "devactivity",
        "description": "devactivity",
        "ip": null,
        "isActive": false
    }
]
```

Onde:

- id (uuid) - Identificador exclusivo
- name (string) - Nome do dispositivo
- description (string) - Descrição do dispositivo
- ip (string) - IP atribuído ao dispositivo
- isActive - Indica se o dispositivo está ativo

---

## 4. Grupos de Itens

### 4.1. Obter grupos

Permite obter a relação de grupos registrados.

```http
GET | /api/modules/{module}/groups
```

Exemplo payload response:

```json
[
    {
        "id": "51ee9138-1f98-45a1-baea-b27345e6598b",
        "name": "Toalhas",
        "parentId": null,
        "icon": null,
        "sku": null,
        "unityType": "JOGO",
        "isActive": true,
        "serializationPreferences": {
            "scheme": "gtin",
            "tagSize": 96,
            "identifier": "00000000000001",
            "filterValue": 3,
            "companyPrefixLength": 7
        }
    }
]
```

Onde:

- id (uuid) - Identificador exclusivo
- name (string) - Nome do grupo
- parentId (uuid) - Identificador do grupo pai
- icon (string) - URL para uma imagem
- sku (string) - Stock Keeping Unit (SKU), código único alfanumérico
- unityType (string) - Unidade comercial
- isActive (boolean) - Indica se o grupo está ativo no sistema
- serializationPreferences (object, opcional) - Preferências utilizadas para geração do EPC
    - scheme (string) - Esquema GS1 utilizado
    - tagSize (numérico) - Tamanho do EPC em bits
    - identifier (string) - Identificador utilizado na composição do EPC
    - filterValue (integer) - Valor do filtro EPC GS1
    - companyPrefixLength (integer) - Quantidade de dígitos do Company Prefix GS1

### 4.2. Obter grupo

Permite obter um grupo a partir do seu identificador.

```http
GET | /api/modules/{module}/groups/{id}
```

Exemplo payload response:

```json
{
    "id": "51ee9138-1f98-45a1-baea-b27345e6598b",
    "name": "Toalhas",
    "parentId": null,
    "icon": null,
    "sku": null,
    "unityType": "JOGO",
    "isActive": true,
    "serializationPreferences": {
        "scheme": "gtin",
        "tagSize": 96,
        "identifier": "00000000000001",
        "filterValue": 3,
        "companyPrefixLength": 7
    }
}
```

Para obter também os campos personalizados do grupo, informe o parâmetro `includeCustomFields`:

```http
GET | /api/modules/{module}/groups/{id}?includeCustomFields=true
```

Exemplo payload response:

```json
{
    "id": "51ee9138-1f98-45a1-baea-b27345e6598b",
    "name": "Toalhas",
    "parentId": null,
    "icon": null,
    "sku": null,
    "unityType": "JOGO",
    "isActive": true,
    "serializationPreferences": {
        "scheme": "gtin",
        "tagSize": 96,
        "identifier": "00000000000001",
        "filterValue": 3,
        "companyPrefixLength": 7
    },
    "customFields": [
        {
            "id": "a3c1d6f2-7b1e-4f0a-9d55-2f0c8e3b1a10",
            "name": "Cor",
            "type": "ShortText",
            "description": "Cor da toalha",
            "required": false,
            "defaultValue": null,
            "rangeValue": null,
            "minLength": 0,
            "maxLength": 50,
            "unique": false,
            "options": null
        },
        {
            "id": "c7e2b9a4-1d3f-4e6b-8a20-5b9d1f4c7e21",
            "name": "Tamanho",
            "type": "OnlyChoice",
            "description": "Tamanho da toalha",
            "required": true,
            "defaultValue": null,
            "rangeValue": "P,M,G",
            "minLength": 0,
            "maxLength": 0,
            "unique": false,
            "options": [
                { "value": "G", "label": "G" },
                { "value": "M", "label": "M" },
                { "value": "P", "label": "P" }
            ]
        }
    ]
}
```

Onde:

- includeCustomFields (boolean, opcional, padrão false) - Parâmetro de consulta. Quando true, retorna os campos personalizados do grupo e os campos herdados dos grupos-pai
- customFields (array, opcional) - Lista de campos personalizados do grupo. Retornado somente quando includeCustomFields é true
    - id (uuid) - Identificador exclusivo do campo
    - name (string) - Nome do campo
    - type (string) - Tipo do campo (ex.: ShortText, LongText, Numeric, Date, OnlyChoice, MultipleChoice, State, YesNo)
    - description (string, opcional) - Descrição do campo
    - required (boolean) - Indica se o preenchimento do campo é obrigatório
    - defaultValue (string, opcional) - Valor padrão do campo
    - rangeValue (string, opcional) - Valores permitidos para o campo, separados por vírgula
    - minLength (integer) - Quantidade mínima de caracteres
    - maxLength (integer) - Quantidade máxima de caracteres
    - unique (boolean) - Indica se o valor do campo deve ser único
    - options (array, opcional) - Opções de seleção do campo. Retornado somente para os tipos OnlyChoice, MultipleChoice e State
        - value (string) - Valor da opção
        - label (string) - Texto apresentado da opção

### 4.3. Obter grupo por EAN ou SKU

Permite obter um grupo a partir do seu EAN ou SKU.

```http
GET | /api/modules/{module}/groups?ean={ean}
GET | /api/modules/{module}/groups?sku={sku}
```

Exemplo payload response:

```json
{
    "id": "51ee9138-1f98-45a1-baea-b27345e6598b",
    "name": "Toalhas",
    "parentId": null,
    "icon": null,
    "sku": null,
    "unityType": "JOGO",
    "isActive": true,
    "serializationPreferences": {
        "scheme": "gtin",
        "tagSize": 96,
        "identifier": "00000000000001",
        "filterValue": 3,
        "companyPrefixLength": 7
    }
}
```

### 4.4. Registrar um grupo

Permite registrar um novo grupo.

```http
POST | /api/modules/{module}/groups
```

Exemplo payload request:

```json
{        
    "name" : "Acessórios",
    "sku" : "12345679",    
	"serializationPreferences": 
	{
		"scheme": "gtin",
		"tagSize": 96,
		"identifier": "00000000000001",
		"filterValue": 3,
		"companyPrefixLength": 7
	}
}
```

Exemplo payload response:

```json
{
    "id": "4dc4316b-a7b3-4b9b-bc59-dadef61cd782"
}
```

### 4.5. Atualizar um grupo

Permite atualizar os dados de um grupo.

```http
PUT | /api/modules/{module}/groups/{id}
```

Exemplo payload request:

```json
{        
    "name" : "Acessórios Esportivos",
    "sku" : "111111111",
}
```

Exemplo payload response:

```json
{
    "id": "4dc4316b-a7b3-4b9b-bc59-dadef61cd782"
}
```

### 4.6. Excluir um grupo

Permite excluir um grupo.

```http
DELETE | /api/modules/{module}/groups/{id}
```

Exemplo payload request:

```json
{        
    "name" : "Acessórios Esportivos",
    "sku" : "111111111",
}
```

Exemplo payload response:

"1 record(s) deleted!"

### 4.7. Obter a configuração de apresentação do grupo

Permite obter a configuração de apresentação para os grupos. A configuração define os campos que são apresentados no cadastro de item de cada grupo, a ordem de apresentação, o rótulo e se o campo é editável no aplicaitivo móvel.

```http
GET | /api/modules/{module}/mobile/group-settings
```

Exemplo payload response:

```json
{
    "generatedAt": "2026-10-21T16:48:43.512Z",
    "groups": [
        {
            "groupName": "Toalhas",
            "description": "Configuração do cadastro de toalhas",
            "fields": [
                {
                    "fieldName": "description",
                    "isFixed": true,
                    "label": "Descrição",
                    "isEditable": true,
                    "isActive": true,
                    "displayOrder": 1
                },
                {
                    "fieldName": "Cor",
                    "isFixed": false,
                    "label": null,
                    "isEditable": false,
                    "isActive": true,
                    "displayOrder": 2
                }
            ]
        }
    ],
    "errors": []
}
```

Onde:

- generatedAt (timestamp) - Data e hora (UTC) em que a configuração foi gerada
- groups (array) - Lista de configurações dos grupos ativos
    - groupName (string) - Nome do grupo
    - description (string, opcional) - Descrição da configuração do grupo
    - fields (array) - Lista de campos do cadastro de item, ordenada por displayOrder
        - fieldName (string) - Nome do campo. Para os campos fixos, os valores são: description, identifier, alias, batch_number, order_code, manufacture_date, expiration_date e expected_place. Para os campos personalizados, é o nome do campo no grupo
        - isFixed (boolean) - Indica se é um campo fixo do item (true) ou um campo personalizado do grupo (false)
        - label (string, opcional) - Rótulo apresentado no coletor. Quando nulo, o coletor utiliza o nome do campo
        - isEditable (boolean) - Indica se o usuário pode alterar o valor do campo no coletor
        - isActive (boolean) - Indica se o campo é apresentado no coletor
        - displayOrder (integer) - Ordem de apresentação do campo
- errors (array) - Lista de erros da requisição

---

## 5. Itens

### 5.1. Obter itens

Permite obter a relação de itens registrados no sistema para qualquer módulo que esteja autorizado.

```http
GET | /api/items
```

Exemplo payload response:

```json
[
    {
        "id": "ee0a04b3-cb2b-4505-8923-ec51a8aea54b",
        "description": "Camisa Feminina Social Manga Longa",
        "alias": "Camisa 1",
        "batchNumber": 1234567890,
        "manufactureDate": 2024-01-01T00:00:00Z,
        "expirationDate": 2025-01-01T00:00:00Z,
        "currentHolderCompany": null,
        "expectedPlace": null,
        "place": null,
        "flow": null,
        "flowStep": null,
        "group": {
            "id": "f14a2e3b-6851-4d93-85a9-bc1a8e6af22d",
            "name": "Vestuário",
            "parentId": null,
            "icon": null,
            "sku": null,
            "serializarionPreferences": null
        },
        "identifiers": [
            {
                "value": "303500000000000000000001",
                "securityKey": E2801130200039E4A5B1088D
            }
        ],
        "fields": 
        [
            {
                "name": "Cor",
                "value": "rosa",
                "type": "ShortText"
            },
            {
                "name": "Tamanho",
                "value": "P",
                "type": "OnlyChoice"
            }
        ]
    }
]
```

Onde, para cada objeto da lista fields:

- name (string) - Nome do campo
- value (string, opcional) - Valor do campo no item
- type (string, opcional) - Tipo do campo (ex.: ShortText, Numeric, Date, OnlyChoice). Nulo quando a configuração do campo não está disponível

### 5.2. Adicionar item

Permite criar um novo item no sistema quando o identificador é conhecido.

```http
POST | /api/items
```

Exemplo payload request:

```json
{
    "identifier" : "303500000000000000000001",
    "identifierType" : "epc",
    "identifierSecurityKey" : "E2801130200039E4A5B1088D",
    "moduleId" : 9,
    "groupId" : "72998487-7045-4de5-9e48-0933010bbfb2",
    "description" : "Camisa Feminina Social Manga Longa",
    "alias" : "Camisa 1",    
    "batchNumber" : "1234567890",
    "order" : "1234567890",
    "manufactureDate" : "2024-01-01T00:00:00Z",
    "expirationDate" : "2025-01-01T00:00:00Z",
    "expectedPlaceId" : "559fa577-0c9f-46fa-8730-902031cecbc3",
    "fields" : {
        "color": "red",
        "size": "M",
        "imageUrl": "https://example.com/images/camisa1.jpg"
    },
    "initialEvent":
	{
        "PlaceId":"559fa577-0c9f-46fa-8730-902031cecbc3",
		"step" : "storing"
	}
}
```

Exemplo payload response:

```json
{
    "id": "ee0a04b3-cb2b-4505-8923-ec51a8aea54b"
}
```

Exemplo payload response com erro:

```json
{
    "errors": [
        {
            "message": "Alias já registrado(a)"
        },
        {
            "message": "Identifier já registrado(a)"
        }
    ]
}
```

Onde:

- identifier (string, obrigatório) - Código Epc padrão 96 bits, ex: "303500000000000000000001"
- identifierType (string, obrigatório) - Tipo do identificador, valor padrão "epc"
- identifierSecurityKey (string, opcional) - Código TID da etiqueta RFID, utilizado para segurança (Validar se a tag é a mesma identificada)
- moduleId (integer, obrigatório) - Identificador do módulo
- groupId (uuid, obrigatório) - Identificador do grupo ao qual o item pertence
- description (string, obrigatório) - Descrição do item
- alias (string, opcional) - Nome alternativo para o item
- batchNumber (string, opcional) - Número do lote do item
- order (string, opcional) - Código do pedido associado
- manufactureDate (data no formato ISO 8601 (UTC), opcional) - Data de fabricação do item
- expirationDate  (data no formato ISO 8601 (UTC), opcional) - Data de validade do item
- expectedPlaceId (uuid, opcional) - Identificador do local esperado para o item. Quando o local não existe para a empresa, o item é registrado sem local esperado
- fields (object) - Conjunto de informações adicionais sobre o item, como cor, tamanho, etc
    - Os campos devem fazer parte dos campos configurado no grupo
- initialEvent (object) - Permite configurar uma etapa inicial como por exemplo indicar que o item está em estoque

Ao registrar o item seu status final será *Active* e sua etapa *Commissioning*

Ao registrar o item 2 eventos serão registrados em histórico:
- Created
- Active

### 5.3. Serializar novos itens

Permite criar novos itens por meio do processo de serialização, onde novos EPCs são gerados para cada item com base nas configurações de serialização definidas para o grupo.

É obrigatório que o grupo informado contenha as configurações para serialização.

```http
POST | /api/modules/{module}/serializations
```

Exemplo payload request:

```json
{
	"order" : "123457",
	"items" : 
	[
		{ "groupid" : "72998487-7045-4de5-9e48-0933010bbfb2", "quantity" : 1, "order": "123456" }
	],
    "printerOptions" :
    {
        "labelTemplateId" : "2a305f7f-0852-4c98-aa3d-552ec1825f19",
        "deviceId" : "74ea844a-1790-4273-b91c-1b2794741e5e"
    },
    "initialEvent" :
	{
        "placeId" : "d514d0c0-bc97-40b2-9d35-868e1e61b809",
		"step" : "storing"
	}
}
```

Exemplo payload response:

```json
{
    "order" : "123457",
    "printerProcessId" : "fa893509-db10-4bd9-8089-0d9b5a2b70d4",
    "results" : [
        {
            "groupId" : "72998487-7045-4de5-9e48-0933010bbfb2",
            "groupName" : "Camisa Feminina Social Manga Longa",
            "quantitySerialized" : 1,
            "serializationProcessId" : "23fcedfc-ab17-44cd-8aa0-48acdeabaaaa",
            "epcs" : [
                "303B033080D2F68000000036"
            ]
        }
    ],
    "errors" : []
}
```

Exemplo payload response com erro:

```json
{
    "order" : "123457",
    "printerProcessId" : null,
    "results" : [],
    "errors" : [
        {
            "message": "Grupo (a399422c-9646-4436-8c85-2a6647d94703) inválido ou sem preferências de serialização"
        }
    ]
}
```

Onde:

- order (string, opcional) - Se informado a ordem será aplicada a todos os itens
- items (array, obrigatório)
    - groupid (uuid, obrigatório) - Define o grupo de itens
    - quantity (integer, obrigatório) - Define a quantidade de itens para o grupo informado
    - order (string, opcional) - Se informado será atribuído aos itens deo grupo
- printerOptions (opcional) - Configura opções de impressão
    - labelTemplateId (uuid, obrigatório) - Define o modelo da etiqueta
    - deviceId (uuid, obrigatório) - Define o dispositivo de impressão
- initialEvent (opcional) - Permite definir um evento inicial como por exemplo definir que o item deve ser movido para o estoque
    - placeId (uuid, opcional) - Define o local para onde o item será movido
    - step (string, obrigatório) - Define a etapa do processo para qual o item será movido

Ao registrar o item seu status final será *Active* e sua etapa *Commissioning*

Ao registrar o item 2 eventos serão registrados em histórico:
- Created
- Active

Se um evento inicial for definido ele será registrado para cada item assim como um novo evento de histórico equivalente.

### 5.4. Atualizar item

Permite atualizar os dados de um item.

```http
PUT | /api/items/{item_id}
```

Exemplo payload request:

```json
{   
    "description" : "Camisa Feminina Social Manga Curta",
    "alias" : "CFSMC",
    "fields" : {
        "color": "blue",
        "size": "M"        
    }
}
```

Exemplo payload response:

```json
{
    "id": "ee0a04b3-cb2b-4505-8923-ec51a8aea54b"
}
```

Onde:

- Id (uuid) - Identificador do item
  - Description (string) - Descrição do item
- Alias (string) - Nome alternativo do item
- BatchNumber (long) - Número do lote do item
- ManufactureDate (datetime) - Data de fabricação do item
- ExpirationDate (datetime) - Data de validade do item    
- CurrentHolderCompany (string) - Empresa atualmente responsável pela posse do item
- ExpectedPlace (string) - Local esperado do item
- Place (string) - Local atual do item
- Flow (string) - Fluxo ao qual o item está vinculado
- FlowStep (string) - Etapa atual do fluxo do item
- Group
    - Grupo ao qual o item pertence
        - Id (uuid) - Identificador do grupo
        - Name (string) - Nome do grupo
        - ParentId (uuid) - Identificador do grupo pai
        - Icon (string) - Ícone associado ao grupo
        - Sku (string) - SKU do grupo
        - SerializationPreferences
            - Preferências de serialização do grupo
- Identifiers
    - Identificadores vinculados ao item
        - Value (string)
            - EPC
        - SecurityKey (string)
            - Chave de segurança do EPC
- Fields
    - Campos adicionais vinculados ao item
        - Name (string)
            - Nome do campo
        - Value (string)
            - Valor do campo

### 5.5. Obter item por Id

Permite obter os dados de um item registrado no sistema para qualquer módulo que esteja autorizado o acesso.

```http
GET | /api/items/{item_id}
```

Exemplo payload response:

```json
{
    "id": "ee0a04b3-cb2b-4505-8923-ec51a8aea54b",
    "description": "Camisa Feminina Social Manga Longa",
    "alias": "Camisa 1",
    "batchNumber": 1234567890,
    "manufactureDate": 2024-01-01T00:00:00Z,
    "expirationDate": 2025-01-01T00:00:00Z,
    "currentHolderCompany": null,
    "expectedPlace": null,
    "place": null,
    "flow": null,
    "flowStep": null,
    "group": {
        "id": "f14a2e3b-6851-4d93-85a9-bc1a8e6af22d",
        "name": "Vestuário",
        "parentId": null,
        "icon": null,
        "sku": null,
        "serializarionPreferences": null
    },
    "identifiers": [
        {
            "value": "303500000000000000000001",
            "securityKey": E2801130200039E4A5B1088D
        }
    ],
    "fields": 
    [
        {
            "name": "Cor",
            "value": "rosa"
        },
        {
            "name": "Tamanho",
            "value": "P"
        }
    ]
}
```

### 5.6. Obter item por EPC

Permite obter os dados de um item registrado no sistema para qualquer módulo que esteja autorizado o acesso.

```http
GET | /api/items/{epc}
```

Exemplo payload response:

```json
{
    "id": "ee0a04b3-cb2b-4505-8923-ec51a8aea54b",
    "description": "Camisa Feminina Social Manga Longa",
    "alias": "Camisa 1",
    "batchNumber": 1234567890,
    "manufactureDate": 2024-01-01T00:00:00Z,
    "expirationDate": 2025-01-01T00:00:00Z,
    "currentHolderCompany": null,
    "expectedPlace": null,
    "place": null,
    "flow": null,
    "flowStep": null,
    "group": {
        "id": "f14a2e3b-6851-4d93-85a9-bc1a8e6af22d",
        "name": "Vestuário",
        "parentId": null,
        "icon": null,
        "sku": null,
        "serializarionPreferences": null
    },
    "identifiers": [
        {
            "value": "303500000000000000000001",
            "securityKey": E2801130200039E4A5B1088D
        }
    ],
    "fields": 
    [
        {
            "name": "Cor",
            "value": "rosa"
        },
        {
            "name": "Tamanho",
            "value": "P"
        }
    ]
}
```

### 5.7. Obter itens por Order

Permite obter os dados dos itens vinculados a um order.

```http
GET | /api/orders/{order}/items
```

Exemplo payload response:

```json
{
    "order": "123456",
    "module": {
        "id": 7,
        "name": "ACS",
        "description": "Controle de Acesso de Ativos"
    },
    "items": [
        {
            "id": "755bf901-2939-4e1b-9232-2670cc92921e",
            "description": "ALT00000",
            "identifiers": [
                {
                    "value": "303500000000000000000011",
                    "securityKey": null
                },
                {
                    "value": "303500000000000000000012",
                    "securityKey": "303500000000000000000012"
                }
            ]
        },
        {
            "id": "04de8e82-f926-4bde-8408-4464dc938630",
            "description": "ALT00001",
            "identifiers": []
        }
    ]
} 
```

Onde:

- Order (string) - Código do Pedido
- Module - Módulo ao qual os itens pertencem   
    - Id (integer) - Identificador do módulo
    - Name (string) - Nome do módulo
    - Description - Descrição do módulo
- Items - Itens vinculados ao código do pedido
    - Id (uuid) - Identificador do item
    - Description (string) - Descrição do item
    - Identifiers - Identificadores vinculados ao item
        - Value (string) - Valor do itendificador, ex: EPC
        - SecurityKey (string) - Chave de segurança, ex: TID

### 5.8. Associar um identificador a um item

Permite associar um identificador a um item registrado no sistema.

```http
POST | /api/items/{id}/identifiers
```

Exemplo payload request:

```json
{ 
    "identifier" : "303500000000000000000000", 
    "identifierType" : "epc",
    "identifierSecurityKey" : "303500000000000000000000"
} 
```

Exemplo payload response:

```json
{
    "id": "ee0a04b3-cb2b-4505-8923-ec51a8aea54b"
}
```

Exemplo payload response com erro:

```json
{
    "errors": [
        {
            "message": "Identificador já registrado(a)"
        },
        {
            "message": "Chave de segurança já registrado(a)"
        }
    ]
}
```

### 5.9. Ativar um identificador associado a um item

Permite ativar um identificador associado a um item registrado no sistema.

```http
POST | /api/items/identifiers/{identifier}/activate
```

Exemplo payload response:

200 OK

### 5.10. Suspender um identificador associado a um item

Permite suspender um identificador associado a um item registrado no sistema.

```http
POST | /api/items/identifiers/{identifier}/suspend
```

Exemplo payload response:

200 OK

### 5.11. Descartar um identificador associado a um item

Permite descartar um identificador associado a um item registrado no sistema.

```http
POST | /api/items/identifiers/{identifier}/discard
```

Exemplo payload response:

200 OK

---

### 5.12. Adiciona uma agregação de itens

Permite adicionar uma agregação de itens.

```http
POST | /api/aggregations
```

Exemplo payload request:

```json
{ 
	"aggregator" : 
        {
            "identifier": "303500000000000000000000",
            "identifierType": "epc"
        },
	"items" :
        [
		    {
                "identifier" : "303500000000000000000001",
                "identifierType": "epc"
            }
	    ]
}
```

Exemplo payload response:

```json
{
    "id": "ee0a04b3-cb2b-4505-8923-ec51a8aea54b"
}
```

Exemplo payload response com erro:

```json
{
    "errors": [
        {
            "message": "Agregação para este item já registrado(a)"
        }
    ]
}
```

Onde:

- identifier (string, obrigatório) - Código Epc padrão 96 bits, ex: "303500000000000000000000"
- identifierType (string, obrigatório) - Tipo do identificador (EPC ou MacAddress)
- items (coleção, obrigatório) - Conjunto de informações sobre os itens a serem agregados
    - identifier (string, obrigatório) - Código Epc padrão 96 bits, ex: "303500000000000000000001"
    - identifierType (string, obrigatório) - Tipo do identificador (EPC ou MacAddress)

### 5.13. Adiciona um item a uma agregação de itens

Permite adicionar um item a uma agregação de itens existente.

```http
POST | /api/aggregations/{id}/items
```

Exemplo payload request:

```json
{ 
	"items" :
    [
			{
                "identifier" : "303802BC831752C00000007D",
                "identifierType": "epc"
            }
	]
}
```

Exemplo payload response:

```json
{
    "id": "601c59ef-a1c5-4a86-a493-e562bb2c8da8"
}
```

Exemplo payload response com erro:

```json
{
    "errors": [
        {
            "message": "Item(s) já registrado(a)"
        }
    ]
}
```

Onde:

- items (coleção, obrigatório) - Conjunto de informações sobre os itens a serem agregados
    - identifier (string, obrigatório) - Código Epc padrão 96 bits, ex: "303500000000000000000001"
    - identifierType (string, obrigatório) - Tipo do identificador (EPC ou MacAddress)

### 5.14. Excluir uma agregação de itens

```http
DELETE | /api/aggregations/{id}
```

Exemplo payload response:

200 OK "1 record(s) deleted!"

### 5.15. Excluir uma agregação de itens a partir de um identificador

```http
DELETE | /api/aggregations/identifier/{identifier}
```

Exemplo payload response:

200 OK "1 record(s) deleted!"

### 5.16. Excluir um item de uma agregação de itens

```http
DELETE | /api/aggregations/{id}/items/{itemId}
```

Exemplo payload response:

200 OK "1 record(s) deleted!"

### 5.17. Excluir um item de uma agregação de itens a partir de um identificador

```http
DELETE | /api/aggregations/{id}/items/identifier/{identifier}
```

Exemplo payload response:

200 OK "1 record(s) deleted!"

### 5.18. Obter uma agregação de itens

```http
GET | /api/aggregations/{id}
```

Exemplo payload response:

```json
{
    "id": "273829ab-5518-4ab0-b7c3-fee9d3df17cc",
    "registered": "2026-10-28T11:59:04.499343",
    "aggregator": {
        "identifierType": "EPC",
        "identifierValue": "303500000000000000000000",
        "registered": "2026-10-28T11:59:04.499343",
        "item": {
            "id": "11efb5a9-8a21-4b5e-a2b7-5f3b60e7e24e",
            "description": "Caixa de papelão"
        }
    },
    "items": [
        {
            "identifierType": "EPC",
            "identifierValue": "303500000000000000000001",
            "registered": "2026-10-28T11:59:04.499343",
            "item": {
                "id": "15f290b4-bc85-474b-88ea-2e012ee2a7a1",
                "description": "Toalha Tipo A"
            }
        },
        {
            "identifierType": "EPC",
            "identifierValue": "303500000000000000000002",
            "registered": "2026-10-28T11:59:04.499343",
            "item": {
                "id": "85d3d777-4a94-4fc8-9278-592e5ef9fe78",
                "description": "Toalha Tipo A"
            }
        }
    ]
}
```

Onde:

- Id (uuid) - Identificador exclusivo da agregação
- Registered (datetime) - Momento de registro
- Aggregator - Item agregador
    - identifierType (string) - Tipo do identificador (EPC ou MacAddress)
    - identifierValue (string) - Código Epc padrão 96 bits, ex: "303500000000000000000001"
    - Registered (datetime) - Momento de registro
    - Item - Detalhes sobre o item agregador
        - Id (uuid) - Identificador exclusivo do item agregador
        - Description (string) - Descrição do item agregador
- Items (coleção) - Itens agregados
    - identifierType (string) - Tipo do identificador (EPC ou MacAddress)
    - identifierValue (string) - Código Epc padrão 96 bits, ex: "303500000000000000000001"
    - Registered (datetime) - Momento de registro
    - Item - Detalhes sobre o item agregador
        - Id (uuid) - Identificador exclusivo do item agregador
        - Description (string) - Descrição do item agregador

### 5.19. Obter uma agregação de itens a partir de um identificador

```http
GET | /api/aggregations/identifier/{identifier}
```

### 5.20. Obter uma agregação de itens a partir de um item agregado

```http
GET | /api/aggregations/item/{itemId}
```

### 5.21. Obter uma agregação de itens a partir de um identificador de um item agregado

```http
GET | /api/aggregations/item/identifier/{itemIdentifier}
```

### 5.22. Obter o histórico de agregações a partir de um identificador exclusivo de uma agregação

```http
GET | /api/aggregations/{id}/history
```

Exemplo payload response:

```json
{
    "aggregations": [
        {
            "aggregationId": "138cfb7d-1a26-451d-95b9-0f99c75ae9c1",
            "aggregator": {
                "identifierType": "EPC",
                "identifierValue": "303500000000000000000000",
                "registered": "2026-10-27T16:03:02.151956",
                "item": {
                    "id": "11efb5a9-8a21-4b5e-a2b7-5f3b60e7e24e",
                    "description": "Caixa de papelão"
                }
            },
            "events": [
                {
                    "id": "a0000000-0000-4000-8000-000000000001",
                    "transactionId": "c0000000-0000-4000-8000-000000000001",
                    "action": "created",
                    "registered": "2026-10-27T16:03:02.151956",
                    "items": [
                        {
                            "identifierType": "EPC",
                            "identifierValue": "303500000000000000000001",
                            "registered": "2026-10-27T16:03:02.151956",
                            "item": {
                                "id": "15f290b4-bc85-474b-88ea-2e012ee2a7a1",
                                "description": "Toalha tipo A"
                            }
                        },
                        {
                            "identifierType": "EPC",
                            "identifierValue": "303500000000000000000002",
                            "registered": "2026-10-27T16:03:02.151956",
                            "item": {
                                "id": "85d3d777-4a94-4fc8-9278-592e5ef9fe78",
                                "description": "Toalha tipo A"
                            }
                        }
                    ]
                },
                {
                    "id": "a0000000-0000-4000-8000-000000000003",
                    "transactionId": "c0000000-0000-4000-8000-000000000002",
                    "action": "item_added",
                    "registered": "2026-10-27T16:03:02.151956",
                    "items": [
                        {
                            "identifierType": "EPC",
                            "identifierValue": "303500000000000000000003",
                            "registered": "2026-10-27T16:04:10.576818",
                            "item": {
                                "id": "da28ebed-3d78-429c-a533-ae403b14ac39",
                                "description": "Toalha tipo A"
                            }
                        }
                    ]
                },
                {
                    "id": "a0000000-0000-4000-8000-000000000004",
                    "transactionId": "c0000000-0000-4000-8000-000000000003",
                    "action": "item_added",
                    "registered": "2026-10-27T16:03:02.151956",
                    "items": [
                        {
                            "identifierType": "EPC",
                            "identifierValue": "303500000000000000000004",
                            "registered": "2026-10-27T16:04:25.139302",
                            "item": {
                                "id": "316444d4-34aa-4b39-ab26-ea5bef3c5c29",
                                "description": "Toalha tipo B"
                            }
                        }
                    ]
                },
                {
                    "id": "a0000000-0000-4000-8000-000000000005",
                    "transactionId": "c0000000-0000-4000-8000-000000000004",
                    "action": "item_removed",
                    "registered": "2026-10-27T16:03:02.151956",
                    "items": [
                        {
                            "identifierType": "EPC",
                            "identifierValue": "303500000000000000000004",
                            "registered": "2026-10-27T16:10:00",
                            "item": {
                                "id": "85d3d777-4a94-4fc8-9278-592e5ef9fe78",
                                "description": "Toalha tipo B"
                            }
                        }
                    ]
                }
            ]
        }
    ],
    "page": 1,
    "pageSize": 20,
    "totalItems": 7,
    "totalPages": 1
}
```

Onde:

Aggregations (coleção) - Agregações encontradas
- AggregationId (uuid) - Identificador exclusivo da agregação
- Aggregator - Item agregador
  - IdentifierType (string) - Tipo do identificador (EPC ou MacAddress)
  - IdentifierValue (string) - Código EPC padrão 96 bits, ex: "303500000000000000000000"
  - Registered (datetime) - Momento de registro do identificador do item agregador
  - Item - Detalhes sobre o item agregador
    - Id (uuid) - Identificador exclusivo do item agregador
    - Description (string) - Descrição do item agregador
- Events (coleção) - Eventos relacionados à agregação
  - Id (uuid) - Identificador exclusivo do evento
  - TransactionId (uuid) - Identificador exclusivo da transação associada ao evento
  - Action (string) - Ação realizada na agregação (created, item_added ou item_removed)
  - Registered (datetime) - Momento de registro do evento
  - Items (coleção) - Itens relacionados ao evento
    - IdentifierType (string) - Tipo do identificador (EPC ou MacAddress)
    - IdentifierValue (string) - Valor do identificador do item
    - Registered (datetime) - Momento de registro do identificador do item
    - Item - Detalhes sobre o item
      - Id (uuid) - Identificador exclusivo do item
      - Description (string) - Descrição do item
- Page (integer) - Número da página atual
- PageSize (integer) - Quantidade máxima de registros por página
- TotalItems (integer) - Quantidade total de registros encontrados
- TotalPages (integer) - Quantidade total de páginas disponíveis

### 5.23. Obter o histórico de agregações a partir de um identificador de um agregado

```http
GET | /api/aggregations/identifier/{identifier}/history
```

### 5.24. Obter o histórico de agregações a partir de um identificador exclusivo de um agregado

```http
GET | /api/aggregations/item/{itemId}/history
```

### 5.25. Obter o histórico de agregações a partir de um identificador de um agregado

```http
GET | /api/aggregations/item/identifier/{itemIdentifier}/history
```

## 6. Eventos

### 6.1. Registrar um evento

Permite registrar um evento relacionado a um ou mais itens, como movimentação, alteração de etapa, etc.

O status estará condicionada a etapa conforme tabela referencia abaixo:

| Processo       | Step           | Status       |
|----------------|----------------|--------------|
| Provisionamento| creating       | created      |
| Vinculo EPC    | commissioning  | active       |
| Produção       | processing     | in_progress  |
| Estoque        | storing        | active       |
| Separação      | picking        | reserved     |
| Expedição      | shipping       | in_transit   |
| Recebimento    | receiving      | active       |
| Retorno        | receiving      | active       |
| Descarte       | discarding     | disposed     |

```http
POST | /api/item-events
```

Exemplo payload request:

```json
{
    "module" : "iris",
    "order" : "123456",
	"step" : "storing",
	"placeId" : "72998487-7045-4de5-9e48-0933010bbfb2",
	"items" :
	[
		{"identifier" : "303500000000000000000001"},
		{"identifier" : "303500000000000000000002"}
	]
}
```

Onde:

- Module (string, obrigatório)
    - Define o módulo do sistema que está registrando o evento.
- Order (string, opcional)
    - Define o código do pedido que está registrando o evento.
- Step (string, obrigatório)
    - Define a etapa do fluxo na qual o evento ocorreu, como "recebimento", "armazenagem", "expedição", etc.
- PlaceId (guid, opcional)
    - Identifica o local onde o evento ocorreu.
- Items (array, obrigatório)
    - Identificadores dos itens relacionados ao evento.

> **Importante**: PlaceId indica onde o evento foi observado. O movimento (origem -> destino) é inferido pela sequência dos eventos.

Para não perder a rastreabilidade por local, informar o local nos eventos.

PlaceId e LastSeenAt do Item são atualizados após o processamento do evento.

A estrutura atual contempla para os locais o Source e o Target:
- source define de onde o item veio
- target define para onde o item vai / onde ele passa a estar

Após o evento ocorrido o estado atual do item é = target.

Exemplos:

Expedição

```json
{
  "step": "shipping",
  "source": "CD São Paulo",
  "target": "Em Transito"
}
```

Recebimento

```json
{
  "step": "receiving",
  "source": "Em Transito",
  "target": "Loja Campinas"
}
```

Processamento interno

```json
{
  "step": "processing",
  "source": "Loja Campinas",
  "target": "Loja Campinas"
}
```

### 6.2. Obter o último evento de um item por Id ou EPC

Permite obter os dados do último evento de um item registrado no sistema para qualquer módulo que esteja autorizado o acesso.

```http
GET | /api/item-events/item/{id}/last-event
GET | /api/item-events/identifier/{identifier}/last-event
```

Exemplo payload response:

```json
{
    "id": "db167b93-b10c-4944-9139-62c72bfb14b4",
    "description": "AAA00004",
    "event": {
        "identifier": "303401B5F00A12C0000001E4",
        "status": "Em Estoque",
        "step": "Armazenamento",
        "place": "Estoque Corredor 1",
        "registered": "2026-02-06T16:54:48.981656"
    }
}
```

Onde:

- Id (uuid)
    - Identificador do item
- Description (string)
    - Descrição do item
- Event
    - Último evento do item
        - Identifier (string)
            - EPC que gerou o evento
        - Status (string)
            - Status aplicado ao item
        - Step (string)
            - Etapa aplicada ao item
        - Place (string)
            - Local onde o evento foi gerado
        - Registered (timestamp)
            - Momento de ocorrência

### 6.3. Obter os eventos de um item por Id ou EPC

Permite obter os dados dos eventos de um item registrado no sistema para qualquer módulo que esteja autorizado o acesso.

```http
GET | /api/item-events/item/{id}
GET | /api/item-events/identifier/{identifier}
```

Exemplo payload response:

```json
{
    "id": "db167b93-b10c-4944-9139-62c72bfb14b4",
    "description": "AAA00004",
    "events": [
        {
            "identifier": null,
            "status": "",
            "step": "",
            "place": null,
            "registered": "2025-05-06T08:41:06.226587"
        },
        {
            "identifier": "303401B5F00A12C0000001E4",
            "status": "Vendido",
            "step": "Expedição",
            "place": null,
            "registered": "2025-05-05T18:26:53.494799"
        }
    ]
}
```

Onde:

- Id (uuid)
    - Identificador do item
- Description (string)
    - Descrição do item
- Events
    - Eventos do item
        - Identifier (string)
            - EPC que gerou o evento
        - Status (string)
            - Status aplicado ao item
        - Step (string)
            - Etapa aplicada ao item
        - Place (string)
            - Local onde o evento foi gerado
        - Registered (timestamp)
            - Momento de ocorrência

### 6.4. Obter os eventos de itens por por código de pedido

Permite obter os dados dos eventos de itens registrado no sistema para qualquer módulo que esteja autorizado o acesso.

```http
GET | /api/orders/{order}/items/events
```

Exemplo payload response:

```json
{
        "id": "022165c3-658a-4857-8426-adf64decd688",
        "description": "Teste ACS 1",
        "events": [
            {
                "identifier": "303500000000000000000016",
                "status": "Ativo",
                "step": "Comissionamento",
                "place": null,
                "registered": "2026-04-29T17:03:50.811263"
            },
            {
                "identifier": "303500000000000000000015",
                "status": "Ativo",
                "step": "Comissionamento",
                "place": null,
                "registered": "2026-04-29T17:03:47.804268"
            }
        ]
    },
    {
        "id": "0909de86-de9e-47c3-bf16-87cee949c2c4",
        "description": "Teste ACS 2",
        "events": [
            {
                "identifier": "303500000000000000000013",
                "status": "Ativo",
                "step": "Comissionamento",
                "place": null,
                "registered": "2026-04-29T17:03:17.944424"
            }
        ]
    }
}
```

Onde:

- Id (uuid) - Identificador do item
- Description (string) - Descrição do item
- Events - Eventos dos itens
    - Identifier (string) - EPC que gerou o evento
    - Status (string) - Status aplicado ao item
    - Step (string) - Etapa aplicada ao item
    - Place (string) - Local onde o evento foi gerado
    - Registered (timestamp) - Momento de ocorrência

### 6.5. Obter os eventos 

Permite obter os dados dos eventos de itens registrado no sistema para qualquer módulo que esteja autorizado o acesso.
É possível fazer filtros por range de data, status e etapa.

```http
GET | /api/item-events
```

Exemplo payload response:

```json
{
        "id": "022165c3-658a-4857-8426-adf64decd688",
        "description": "Teste ACS 1",
        "events": [
            {
                "identifier": "303500000000000000000016",
                "status": "Ativo",
                "step": "Comissionamento",
                "place": null,
                "registered": "2026-04-29T17:03:50.811263"
            },
            {
                "identifier": "303500000000000000000015",
                "status": "Ativo",
                "step": "Comissionamento",
                "place": null,
                "registered": "2026-04-29T17:03:47.804268"
            }
        ]
    },
    {
        "id": "0909de86-de9e-47c3-bf16-87cee949c2c4",
        "description": "Teste ACS 2",
        "events": [
            {
                "identifier": "303500000000000000000013",
                "status": "Ativo",
                "step": "Comissionamento",
                "place": null,
                "registered": "2026-04-29T17:03:17.944424"
            }
        ]
    }
}
```

---

## 7. Atividades

### 7.1. Obter atividades

Permite obter a relação de atividades registradas.

```http
GET | /api/modules/{module}/activities
```

Exemplo payload response:

```json
[
    {
        "id": "4c89e7ed-0d94-4e25-938a-89f72565ff59",
        "templateId": "0848aadd-533e-4b1c-a8c4-1e99cf66f5f4",
        "registered": "2026-05-28T16:28:30.713258",
        "scheduled": "2026-05-28T17:28:00",
        "started": "2026-05-28T17:28:00",
        "completed": "2026-05-28T17:29:00",
        "status": "completed",
        "activityType": "Recebimento",
        "listType": "EPC",
        "companySourceName": "Empresa 1",
        "companyTargetName": "Empresa 2",
        "placeSourceName": null,
        "placeTargetName": null,
        "appliedStatus": null,
        "appliedStep": null,
        "quantityAccuracy": 50.0,
        "order": null,
        "validation": null,
        "expectedItems": [
            {
                "groupId": "b453cf81-ce6c-4e74-927c-1e13c5acb4c9",
                "identifier": "304000000020000000000008",
                "quantity": 1,
                "complianceThreshold": 0
            },
            {
                "groupId": "b453cf81-ce6c-4e74-927c-1e13c5acb4c9",
                "identifier": "304000000020000000000009",
                "quantity": 1,
                "complianceThreshold": 0
            }
        ],
        "capturedItems": [
            {
                "groupId": "b453cf81-ce6c-4e74-927c-1e13c5acb4c9",
                "epc": "3040000000200000000000008",
                "capturedAt": "2026-05-28T17:28:32.104076"
            },
            {
                "groupId": "b453cf81-ce6c-4e74-927c-1e13c5acb4c9",
                "epc": "304000000020000000000007",
                "capturedAt": "2026-05-28T17:28:32.104076"
            }
        ],
        "missingItems": [
            {
                "identifier": "304000000020000000000009",
                "quantity": 1
            }
        ],
        "notExpectedItems": [
            {
                "identifier": "304000000020000000000007",
                "quantity": 1
            }
        ],
        "priority": null
    }
]
```

Onde:

- id (uuid)
    - Identificador exclusivo da atividade
- templateId (uuid)
    - Identificador do modelo de atividade utilizado na criação da atividade
- registered (timestamp)
    - Data e hora em que a atividade foi registrada no sistema
- scheduled (timestamp)
    - Data e hora programadas para execução da atividade
- started (timestamp, opcional)
    - Data e hora de início da execução da atividade. Nulo quando a atividade ainda não foi iniciada
- completed (timestamp, opcional)
    - Data e hora de conclusão da atividade. Nulo quando a atividade ainda não foi finalizada
- status (string)
    - Status atual da atividade (ex.: pending, started, completed, canceled)
- activityType (string)
    - Tipo da atividade executada (ex.: Recebimento, Expedição, Inventário, Transferência)
- listType (string)
    - Tipo da lista utilizada para validação ou captura dos itens (ex.: EPC, EAN, SKU)
- companySourceName (string, opcional)
    - Nome da empresa de origem associada à movimentação
- companyTargetName (string, opcional)
    - Nome da empresa de destino associada à movimentação
- placeSourceName (string, opcional)
    - Nome do local de origem associado à movimentação
- placeTargetName (string, opcional)
    - Nome do local de destino associado à movimentação
- appliedStatus (string, opcional)
    - Status aplicado aos itens processados pela atividade após sua conclusão
- appliedStep (string, opcional)
    - Etapa aplicada aos itens processados pela atividade após sua conclusão
- quantityAccuracy (decimal)
    - Percentual de acuracidade da atividade, calculado com base na comparação entre itens esperados e itens capturados
- order (string, opcional)
    - Código da ordem, pedido ou documento associado à atividade
- validation (object, opcional)
    - Informações adicionais de validação da atividade, quando aplicável
- expectedItems (array)
    - Lista de itens esperados para a atividade
    Campos do objeto:
    - groupId (uuid)
        - Identificador do grupo do item. Em listas do tipo EPC, quando o item não está registrado ou não tem grupo, o valor é "00000000-0000-0000-0000-000000000000"
    - name (string, opcional)
        - Nome do grupo do item. Nulo quando o item não tem grupo
    - identifier (string)
        - Identificador esperado do item conforme o tipo de lista utilizado
    - quantity (integer)
        - Quantidade esperada do item
    - complianceThreshold (integer)        
- capturedItems (array)
    - Lista de itens efetivamente capturados durante a execução da atividade
    Campos do objeto:
    - groupId (uuid)
        - Identificador do grupo do item capturado
    - epc (string)
        - EPC ou identificador capturado
    - capturedAt (timestamp)
        - Data e hora da captura do item
- missingItems (array)
    - Lista de itens esperados que não foram capturados
    Campos do objeto:
    - identifier (string)
        - Identificador do item ausente
    - quantity (integer)
        - Quantidade não encontrada
- notExpectedItems (array)
    - Lista de itens capturados que não constavam entre os itens esperados
    Campos do objeto:
    - identifier (string)
        - Identificador do item não esperado
    - quantity (integer)
        - Quantidade encontrada indevidamente
- priority (integer, opcional)
    - Prioridade da atividade.

### 7.2. Obter uma atividade

Permite obter uma atividade a partir de seu identificador.

```http
GET | /api/modules/{module}/activities/{id}
```

Exemplo payload response:

```json
{
    "id": "4c89e7ed-0d94-4e25-938a-89f72565ff59",
    "templateId": "0848aadd-533e-4b1c-a8c4-1e99cf66f5f4",
    "registered": "2026-05-28T16:28:30.713258",
    "scheduled": "2026-05-28T17:28:00",
    "started": "2026-05-28T17:28:00",
    "completed": "2026-05-28T17:29:00",
    "status": "completed",
    "activityType": "Recebimento",
    "listType": "EPC",
    "companySourceName": "Empresa 1",
    "companyTargetName": "Empresa 2",
    "placeSourceName": null,
    "placeTargetName": null,
    "appliedStatus": null,
    "appliedStep": null,
    "quantityAccuracy": 50.0,
    "order": null,
    "validation": null,
    "expectedItems": [
        {
            "groupId": "b453cf81-ce6c-4e74-927c-1e13c5acb4c9",
            "identifier": "304000000020000000000008",
            "quantity": 1,
            "complianceThreshold": 0
        },
        {
            "groupId": "b453cf81-ce6c-4e74-927c-1e13c5acb4c9",
            "identifier": "304000000020000000000009",
            "quantity": 1,
            "complianceThreshold": 0
        }
    ],
    "capturedItems": [
        {
            "groupId": "b453cf81-ce6c-4e74-927c-1e13c5acb4c9",
            "epc": "3040000000200000000000008",
            "capturedAt": "2026-05-28T17:28:32.104076"
        },
        {
            "groupId": "b453cf81-ce6c-4e74-927c-1e13c5acb4c9",
            "epc": "304000000020000000000007",
            "capturedAt": "2026-05-28T17:28:32.104076"
        }
    ],
    "missingItems": [
        {
            "identifier": "304000000020000000000009",
            "quantity": 1
        }
    ],
    "notExpectedItems": [
        {
            "identifier": "304000000020000000000007",
            "quantity": 1
        }
    ],
    "priority": null
 }
```

### 7.3. Registrar uma atividade

Permite registrar uma nova atividade.

```http
POST | /api/modules/{module}/activities
```

Exemplo payload request:

```json
{
    "templateId": "0848aadd-533e-4b1c-a8c4-1e99cf66f5f4",
    "scheduled": "2026-06-10T16:30:00",
    "typeId": 3,
    "quantityAccuracy": null,
    "listType": "EPC",
    "priority": 1,
    "orderCode": null,
    "items": null,
    "companySourceId": 1,
    "companyTargetId": 2,
    "placeSourceId": null,
    "placeTargetId": null
}
```

Exemplo payload response:

```json
{
    "id": "4cddcd03-3f5d-422c-858e-abf8dfd2ea11"
}
```

Onde:

- templateId (uuid, obrigatório) - Identificador do modelo de atividade
- scheduled (timestamp, obrigatório) - Data e hora programadas para execução da atividade
- typeId (integer) - Identificador do tipo da atividade
- quantityAccuracy (decimal, opcional) - Percentual de acuracidade esperado para a atividade
- listType (string) - Tipo da lista de itens esperados (EPC, EAN ou SKU)
- priority (integer) - Prioridade da atividade
- orderCode (string, opcional) - Código da ordem, pedido ou documento associado à atividade
- items (array, opcional) - Lista de itens esperados para a atividade
    - identifier (string) - Identificador do item conforme o tipo de lista (EPC, EAN ou SKU)
    - description (string, opcional) - Descrição do item
    - quantity (integer) - Quantidade esperada
    - complianceThreshold (integer) - Limite de conformidade do item
- companySourceId (integer, opcional) - Identificador da empresa de origem
- companyTargetId (integer, opcional) - Identificador da empresa de destino
- placeSourceId (uuid, opcional) - Identificador do local de origem
- placeTargetId (uuid, opcional) - Identificador do local de destino

Os locais de origem (placeSourceId) e de destino (placeTargetId) informados na requisição prevalecem sobre os locais configurados no modelo da atividade. Quando não são informados, a atividade utiliza os locais do modelo. A Conferência por Local do coletor utiliza esta regra para registrar a atividade no local conferido.

### 7.4. Registrar uma atividade

Permite registrar uma nova atividade.

```http
POST | /api/modules/{module}/activities
```

Exemplo payload request:

```json
{
    "templateId": "0848aadd-533e-4b1c-a8c4-1e99cf66f5f4",
    "scheduled": "2026-06-10T16:30:00",
    "typeId": 3,
    "listType": "EPC",
    "priority": 1,
    "orderCode": null,
    "items": null,
    "companySourceId": 1,
    "companyTargetId": 2,
    "placeSourceId": null,
    "placeTargetId": null
}
```

Exemplo payload response:

```json
{
    "id": "4cddcd03-3f5d-422c-858e-abf8dfd2ea11"
}
```

### 7.5. Atualizar uma atividade

Permite atualizar dados de uma atividade.

```http
PUT | /api/modules/{module}/activities/{id}
```

Exemplo payload request:

```json
{
    "scheduled": "2026-06-11T16:30:00",
    "priority": 2,
    "orderCode": "7843"
}
```

Exemplo payload response:

```json
{
    "id": "4cddcd03-3f5d-422c-858e-abf8dfd2ea11"
}
```

### 7.6. Liberar uma atividade

Permite liberar uma atividade registrada. Após esta ação, não será possível alterar dados da atividade.

```http
POST | /api/modules/{module}/activities/{id}/release
```

Exemplo payload response:

```json
{
    "id": "4cddcd03-3f5d-422c-858e-abf8dfd2ea11"
}
```

### 7.7. Iniciar uma atividade

Permite iniciar uma atividade registrada. Só é possível iniciar atividades com modelos configurados para inicialização manual e que estejam liberadas.

```http
POST | /api/modules/{module}/activities/{id}/start
```

Exemplo payload response:

```json
{
    "id": "4cddcd03-3f5d-422c-858e-abf8dfd2ea11"
}
```

### 7.8. Reiniciar uma atividade

Permite reiniciar uma atividade registrada. Só é possível reiniciar atividades que já foram iniciadas.

```http
POST | /api/modules/{module}/activities/{id}/restart
```

Exemplo payload response:

```json
{
    "id": "4cddcd03-3f5d-422c-858e-abf8dfd2ea11"
}
```

### 7.9. Concluir uma atividade

Permite concluir uma atividade registrada. Só é possível concluir atividades que estejam em progresso.

```http
POST | /api/modules/{module}/activities/{id}/complete
```

Exemplo payload request:

```json
{
    "started": "2026-10-26T15:02:10-03:00",
    "items": [
        {
            "identifier": "304000000020000000000008"
        },
        {
            "identifier": "304000000020000000000007"
        }
    ]
}
```

Onde:

- started (timestamp, obrigatório) - Data e hora de início da execução da atividade
- items (array) - Lista de itens capturados durante a execução da atividade. A lista pode ser vazia
    - identifier (string) - EPC do item capturado

Regras da conclusão:

- O sistema registra os itens capturados e as datas de início e de conclusão da atividade;
- Em atividades com lista do tipo EPC, os itens capturados que não estão na lista de itens esperados são registrados como divergentes (lido mas não esperado);
- Quando o modelo da atividade não tem uma nova etapa configurada, a conclusão não registra eventos de movimentação dos itens. Quando o modelo tem uma nova etapa, o sistema registra um evento para cada item capturado, com a nova etapa e o local de destino do modelo;
- A atividade pode ser concluída sem itens capturados.

Exemplo payload response:

```json
{
    "id": "4cddcd03-3f5d-422c-858e-abf8dfd2ea11"
}
```

### 7.10. Cancelar uma atividade

Permite cancelar uma atividade registrada.

```http
POST | /api/modules/{module}/activities/{id}/cancel
```

Exemplo payload response:

```json
{
    "id": "4cddcd03-3f5d-422c-858e-abf8dfd2ea11"
}
```

### 7.11. Excluir uma atividade

Permite excluir uma atividade registrada.

```http
DELETE | /api/modules/{module}/activities/{id}
```

Exemplo payload response:

200 OK

---

## 8. Places

### 8.1. Obter itens de um local

Permite obter a relação de itens de um local específico a partir de um identificador. A Conferência por Local do coletor utiliza este endpoint para carregar os itens do local conferido.

```http
GET | /api/places/{id}/items
```

Exemplo payload response:

```json
[
    {
        "description": "Ovo Amarelo 1",
        "group": {
            "id": "f14a2e3b-6851-4d93-85a9-bc1a8e6af22d",
            "name": "Ovo Amarelo Grande 20"
        },
        "identifiers": [
            {
                "value": "303500000000000000000001"
            }
        ],
        "alias": "Ovo 1",
        "batchNumber": "L2026-10",
        "order": "7843",
        "manufactureDate": "2026-10-01",
        "expirationDate": "2026-11-15",
        "expectedPlace": "Câmara Fria 1",
        "fields": [
            {
                "name": "Cor",
                "value": "Amarelo",
                "type": "ShortText"
            },
            {
                "name": "Tamanho",
                "value": null,
                "type": "OnlyChoice"
            }
        ]
    }
]
```

Onde:

- description (string) - Descrição do item
- group (object, opcional) - Grupo ao qual o item pertence. Não é retornado quando o item não tem grupo
    - id (uuid) - Identificador exclusivo do grupo
    - name (string) - Nome do grupo
- identifiers (array) - Lista de códigos identificadores vinculados ao item
    - value (string) - Valor do identificador (ex.: EPC)
- alias (string, opcional) - Apelido do item
- batchNumber (string, opcional) - Número de lote do item
- order (string, opcional) - Código do pedido associado ao item
- manufactureDate (string, opcional) - Data de fabricação do item, no formato yyyy-MM-dd
- expirationDate (string, opcional) - Data de validade do item, no formato yyyy-MM-dd
- expectedPlace (string, opcional) - Nome do local esperado para o item
- fields (array, opcional) - Lista dos campos ativos do grupo, inclusive os campos herdados dos grupos-pai e os campos sem valor. Os campos do tipo imagem não são retornados. Não é retornado quando o item não tem grupo ou o grupo não tem campos
    - name (string) - Nome do campo
    - value (string, opcional) - Valor do campo no item
    - type (string, opcional) - Tipo do campo (ex.: ShortText, Numeric, Date, OnlyChoice)

Os atributos com valor nulo não são retornados, com exceção do value dos campos da lista fields.

---

## 9. Modelos de Etiquetas

### 9.1. Obter modelos

Permite obter a relação de templates de etiquetas registradas.

```http
GET | /api/label-templates
```

Exemplo payload response:

```json
{
    [
        "id": "f48418ba-4c18-4a4a-85d1-dd51deea503d",
        "companyId": 1,
        "name": "Etiqueta RFID Padrão 100x50",
        "description": "Template de impressão RFID",
        "rfidEnabled": true,
        "zplContent": "^XA^FO50,50^ADN,36,20^FDTeste RFID^FS^XZ",
        "width": 100.0,
        "height": 50.0,
        "dpi": 1,
        "orientation": 0,
        "printSpeed": 4,
        "darkness": 10,
        "lockAfterWrite": false,
        "usePrinterConfig": true,
        "defaultPrinterId": null
    ]
}
```

Onde:

- id (uuid, obrigatório) - Identificador único do modelo de etiqueta
- companyId (integer, obrigatório) - identifica a empresa proprietária do modelo
- name (string, obrigatório) - Nome do modelo de etiqueta
- description (string, opcional) - Descritivo detalhando a finalidade ou aplicação
- rfidEnabled (boolean, obrigatório) - Indica se o modelo possui suporte e tecnologia para gravação de tags RFID
- zplContent (string, obrigatório) - Código em linguagem ZPL contendo o layout e as instruções de impressão
- width / height (double, obrigatório) - Dimensões físicas (largura e altura)
- defaultPrinterId (uuid, opcional) - Identificador da impressora padrão vinculada a este modelo

### 9.2. Criar modelo

 Permite criar um modelo.

 POST | /api/label-templates

 Exemplo payload request:

 ```json
 {
    "name": "Etiqueta RFID Padrão 100x50",
    "description": "Template de impressão RFID",
    "rfidEnabled": true,
    "zplContent": "^XA^FO50,50^ADN,36,20^FDTeste RFID^FS^XZ",
    "width": 100,
    "height": 50,
    "density": 1,
    "orientation": 0,
    "printSpeed": 4,
    "darkness": 10,
    "lockAfterWrite": false,
    "usePrinterConfig": true,
    "defaultPrinterId": null
}
 ```

Exemplo payload response:

```json
{
    "id": "f48418ba-4c18-4a4a-85d1-dd51deea503d"
}
```

### 9.3. Alterar modelo

Permite alterar um modelo.

```http
PUT | /api/label-templates/{id}
```

Exemplo payload request:

```json
{
    "description": "Template de impressão RFID - 100x50"
}
```

Exemplo payload response:

```json
{
    "id": "f48418ba-4c18-4a4a-85d1-dd51deea503d"
}
```

### 9.4. Excluir modelo

Permite excluir um modelo.

```http
DELETE | /api/label-templates/{id}
```

Exemplo payload response:

```json
{
    "1 record(s) deleted!"
}
```

---

## 10. Impressão de Etiquetas

### 10.1. Imprimir etiqueta

Permitir registrar um processo de impressão de etiquetas.

```http
POST | /api/print-jobs
```

Exemplo payload request:

```json
{
	"deviceid" : "74ea844a-1790-4273-b91c-1b2794741e5e",
	"labels" : 
	[
		{
			"epc": "3038CD1400000B8000000005",
			"writeEpc": true,
            "modeid" : 2,
			"content": 
			{
				"type": "image",
				"value": "iVBORw0KGgoAAAANSUhEUgAAAHgAAAAoAQAAAAAdkQOIAAAAY0lEQVR4nGP8z4ACmBjQwAEUHjOLPIqGP+jqhx7/0cO5nxB8FgZeRoa/yPKMDQwfG1D086Gah6SbgYEJVZqB4f6798ve/YeB3ywMn/8LMCPL/0cGvwc+PCjkP2REBhyMBNIXADJOLJEb3BbnAAAAAElFTkSuQmCC"
			}
		},
        {
			"epc": "3038CD1400000B8000000006",
			"writeEpc": true,
			"content": 
			{
				"type": "image",
				"value": "iVBORw0KGgoAAAANSUhEUgAAAHgAAAAoAQAAAAAdkQOIAAAAY0lEQVR4nGP8z4ACmBjQwAEUHjOLPIqGP+jqhx7/0cO5nxB8FgZeRoa/yPKMDQwfG1D086Gah6SbgYEJVZqB4f6798ve/YeB3ywMn/8LMCPL/0cGvwc+PCjkP2REBhyMBNIXADJOLJEb3BbnAAAAAElFTkSuQmCC"
			}
		},
        {
			"epc": "3038CD1400000B8000000007",
			"writeEpc": true,
			"content": 
			{
				"type": "image",
				"value": "iVBORw0KGgoAAAANSUhEUgAAAHgAAAAoAQAAAAAdkQOIAAAAY0lEQVR4nGP8z4ACmBjQwAEUHjOLPIqGP+jqhx7/0cO5nxB8FgZeRoa/yPKMDQwfG1D086Gah6SbgYEJVZqB4f6798ve/YeB3ywMn/8LMCPL/0cGvwc+PCjkP2REBhyMBNIXADJOLJEb3BbnAAAAAElFTkSuQmCC"
			}
		}
	]
}
```

Onde:

- deviceid (uuid, obrigatório) - Identifica a impressora que irá realizar a impressão
- modeid (integer, obrigatório) - Identificador do modo de impressão (1 - Serviço, 2 - Agente)
- labels (array, obrigatório) - Lista de etiquetas a serem impressas
    - epc (string, obrigatório) - Identificador único da etiqueta
    - writeEpc (boolean, obrigatório) - Indica se o EPC deve ser gravado
    - content (object, obrigatório) - Conteúdo da etiqueta
        - type (string, obrigatório) - Tipo de conteúdo (ex: image)
        - value (string, obrigatório) - Valor do conteúdo (ex: base64 da imagem)

Exemplo payload response:

```json
{
    "id": "da322360-a608-4a84-996a-82d9a4c42c03"
}
```

Onde:

- id - identifica o processo de impressão registrado.

### 10.2. Obter status de impressão

Permite obter o status de um processo de impressão registrado.
```http
GET | /api/print-jobs/{id}
```

Exemplo payload response:

{
    "id": "587d4247-6585-4ba9-a764-33a5d05d6600",
    "jobId": "ad4cda06-52dc-46eb-9d6a-2c6a2e205590",
    "quantity": 3,
    "labelTemplateId": null,
    "deviceId": "74ea844a-1790-4273-b91c-1b2794741e5e",
    "zplTemplateSnapshot": "",
    "printed": 3,
    "failed": 0,
    "status": {
        "id": 3,
        "name": "Concluído"
    },
    "errors": []
}

Onde:

- id (uuid) - Identificador do processo de impressão
- jobId (uuid) - Identificador do job de impressão
- quantity (integer) - Quantidade de etiquetas a serem impressas
- labelTemplateId (uuid, opcional) - Identificador do modelo de etiqueta utilizado, se aplicável
- deviceId (uuid) - Identificador da impressora responsável pela impressão
- zplTemplateSnapshot (string) - Snapshot do template ZPL utilizado na impressão
- printed (integer) - Quantidade de etiquetas impressas com sucesso
- failed (integer) - Quantidade de etiquetas que falharam na impressão
- status (object) - Status atual do processo de impressão, contendo
    - id (integer) - Identificador do status
    - name (string) - Nome do status (ex: "Concluído", "Em andamento", "Falha").

O status do job de impressão pode assumir os seguintes valores:

| Código | Status           |
| -----: | ---------------- |
|      0 | Rascunho         |
|      1 | Pendente         |
|      2 | Processando      |
|      3 | Concluído        |
|      4 | Expirado         |
|      5 | Cancelado        |
|      6 | Abortado         |
|      7 | Erro             |
|      8 | Cancelando       |
|      9 | Pausa Solicitada |
|     10 | Pausado          |
|     11 | Retomado         |

### 10.3. Cancelar impressão

Permite cancelar um processo de impressão registrado.

```http
GET | /api/print-jobs/{id}/cancel
```

Exemplo payload response:

```json
{
    "id": "587d4247-6585-4ba9-a764-33a5d05d6600"
}
```

## 11. Módulo TLM

### 11.1. Notificações em Display

Permite registrar uma nova notificação para um display

```http
POST | /api/itts/tlm/notifications/device/{id}
```

Exemplo payload request:

```json
{
    "message" : "Identix ITTS",
    "color" : "green"
    "duration" : 5
}
```

Exemplo payload response:

```json
{
    "id": "ee0a04b3-cb2b-4505-8923-ec51a8aea54b"
}
```

Exemplo payload response com erro:

```json
{
    "errors": [
        {
            "message": "Cor inválido"
        }
    ]
}
```

Onde:

- message (string, obrigatório) - Mensagem a ser apresentada
- color (string, obrigatório) - Cor a ser utilizada (red, green, yellow)
- duration (integer, obrigatório) - Duração da apresentação da mensagem em segundos