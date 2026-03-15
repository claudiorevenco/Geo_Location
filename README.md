# GeoLocation - Sistema de Georreferenciação

Sistema web moderno para gestão e visualização de locais georreferenciados, desenvolvido com PHP, MySQL, Leaflet e design responsivo.

## ✨ Funcionalidades

### 🗺️ Mapa & Locais
- **Mapa Interativo** - Visualização de locais no mapa com Leaflet
- **Geolocalização** - Deteção automática da localização do utilizador
- **Marcadores Personalizados** - Ícones por categoria com cores distintivas
- **Popups Informativos** - Detalhes rápidos ao clicar nos marcadores
- **Filtragem** - Filtros por categoria e localização em tempo real

### 🏷️ Organização
- **Categorias** - Organização por tipos (restaurantes, hotéis, museus, etc.)
- **Países & Cidades** - Hierarquia geográfica completa
- **Slugs Amigáveis** - URLs otimizadas para SEO

### 🖼️ Gestão de Conteúdo
- **Upload de Fotos** - Imagens com compressão automática (max 2MB)
- **Galeria de Imagens** - Visualização em modais responsivos
- **Descrições** - Texto curto e descrição completa por local

### 💬 Partilha & Comunicação
- **Partilha por Email** - Envio de detalhes do local via PHPMailer
- **Templates HTML** - Emails formatados com design profissional
- **Links Diretos** - Partilha via URL com slug único

### 👤 Autenticação & Autorização
- **Sistema de Login** - Sessões seguras com SHA3-512
- **Hashing SHA3-512** - Algoritmo de encriptação moderno com salt
- **Níveis de Acesso** - Utilizadores normais e administradores
- **Proteção de Rotas** - Redirecionamento automático baseado em permissões
- **Migração Automática** - Conversão de passwords antigas (bcrypt → SHA3)

### ⚙️ Administração (CRUD Completo)
- **Gestão de Utilizadores** - Criar, editar, eliminar, ativar/desativar
- **Paginação** - 10 registos por página com navegação inteligente
- **Pesquisa em Tempo Real** - Filtro por nome e email
- **Estatísticas** - Dashboard com métricas de utilizadores
- **Modais Interativos** - Edição inline sem recarregar a página
- **Proteção Anti-Eliminação** - Impede auto-eliminação do admin

### 📱 Experiência do Utilizador
- **Design Responsivo** - Adaptável a mobile, tablet e desktop
- **Zoom Otimizado** - 80% de zoom em páginas de autenticação
- **Animações Suaves** - Transições CSS modernas
- **Temas & Cores** - Paleta vibrante com gradientes
- **Feedback Visual** - Alertas de sucesso/erro em tempo real

## 🚀 Instalação

### Requisitos
- PHP 7.4+ (recomendado 8.x)
- MySQL 5.7+ ou MariaDB 10.3+
- Extensões PHP: PDO, PDO_MySQL, GD (para imagens), OpenSSL (para emails)
- Servidor web (Apache/Nginx)

### Passos

1. **Clonar/Copiar ficheiros** para a pasta do servidor web
```
/var/www/html/geolocation/
```

2. **Instalar dependências (PHPMailer via Composer)**  
```
composer require phpmailer/phpmailer
```

3. **Configurar ligação à BD em includes/config.php**  
```

$host = 'localhost'
$db   = 'geo_dados'
$user = 'root'
$pass = 'sua_password'
$charset = 'utf8mb4'
```
4. **Configurar email (opcional) em includes/functions.php** 
```
Gmail de Suporte: geo.location.suporte@gmail.com
Senhas de app: tzgp qibj sfne dfqc
Nome da senha de app: GeoLocation

$mail->Host = 'smtp.gmail.com';
$mail->Username = 'seu-email@gmail.com';
$mail->Password = 'password-de-app';
```
5. **Criar pastas com permissões** 
```
mkdir uploads
chmod 777 uploads
```
6. **Aceder à aplicação** 
```
http://localhost/geolocation/

Credenciais Padrão
Admin: admin@geolocation.pt / #Teste123
Utilizador:claudiorevenco@geodados.pt / #Teste123
```

### 📁 Estrutura de Pastas
```
geolocation/
├── admin/                  # Painel de administração
│   ├── utilizadores.php    # Gestão CRUD de utilizadores
│   ├── utilizadores_action.php  # Processamento de ações
│   └── utilizadores_api.php     # API AJAX para modais
├── api/                    # Endpoints da API REST
│   ├── get_locais.php      # Listar locais (JSON)
│   ├── get_local.php       # Detalhes de um local
│   ├── get_paises.php      # Listar países
│   ├── get_cidades.php     # Listar cidades por país
│   ├── inserir_local.php   # Criar novo local
│   ├── editar_local.php    # Atualizar local
│   ├── apagar_local.php    # Eliminar local
│   └── enviar_email.php    # Enviar email com PHPMailer
├── includes/               # Ficheiros core PHP
│   ├── config.php          # Configuração BD e sessão
│   ├── auth.php            # Funções de autenticação
│   ├── hash.php            # Funções SHA3-512 (novo)
│   └── functions.php       # Funções auxiliares (upload, email)
├── vendor/                 # Dependências Composer (PHPMailer)
├── assets/
│   ├── css/style.css       # Design system completo
│   └── js/script.js        # JavaScript interativo
├── uploads/                # Imagens dos locais
├── index.php               # Página principal com mapa
├── login.php               # Autenticação com SHA3
├── register.php            # Registo de novos utilizadores
├── logout.php              # Terminar sessão
└── README.md               # Este ficheiro

```
### 🛠️ Tecnologias Utilizadas

```
PHP 8.x - Linguagem principal com tipagem estrita
PDO - Acesso à base de dados seguro
MySQL/MariaDB - Sistema de gestão de base de dados
PHPMailer 6.x - Envio de emails SMTP
SHA3-512 - Algoritmo de hashing moderno (FIPS 202)

HTML5 - Estrutura semântica
CSS3 - Variáveis CSS, Grid, Flexbox, Animações
JavaScript ES6+ - Fetch API, Arrow functions, Template literals
Leaflet 1.9 - Biblioteca de mapas interativos
Font Awesome 6 - Ícones vetoriais
Serviços Externos
OpenStreetMap - Tiles de mapa gratuitos
Nominatim - Geocoding e reverse geocoding
Google SMTP - Envio de emails (configurável)

```
### 🔐 Segurança
```
SHA3-512 com Salt - Hashing unidirecional de passwords
Salt Aleatório - 32 bytes gerados com random_bytes()
Timing-safe Compare - hash_equals() contra timing attacks
Sessões Seguras - Regeneração de ID, flags HTTPOnly/Secure
Proteção de Dados
Prepared Statements - 100% das queries parametrizadas
XSS Protection - htmlspecialchars() em todos os outputs
CSRF Tokens - Pronto para implementação (estrutura existente)
Validação Server-side - Todos os inputs validados em PHP
Uploads
Validação de Tipo - Apenas imagens (JPG, PNG, GIF, WebP)
Verificação MIME - getimagesize() contra ficheiros falsos
Limite de Tamanho - 2MB máximo por ficheiro
Nomes Únicos - uniqid() para evitar conflitos
Sandboxing - Pasta uploads/ fora do web root (recomendado)

```

###  🐛 Resolução de Problemas
```
Erro	                        Causa	                        Solução
"Erro na ligação à BD" -	Credenciais incorretas - 	Verificar includes/config.php
"Função isAdmin() não existe" - 	auth.php desatualizado -	Atualizar com função isAdmin()
"Coluna created_at não existe" -	Schema desatualizado -	Executar ALTER TABLE ou usar criado_em
Modal não abre	- Erro JavaScript	Verificar consola (F12), -  caminho do API
Email não envia -	SMTP não configurado - 	Configurar credenciais no functions.php
Mapa vazio	- Sem locais na BD	- Inserir locais ou verificar query
Upload falha	- Permissões incorretas	- chmod 777 uploads/ temporariamente

```
