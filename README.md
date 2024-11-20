# Teste de uma Loja com Sistema de Gerenciamento de Estoque 📦

Um sistema completo de gerenciamento de estoque desenvolvido com Flask, oferecendo funcionalidades para administradores e usuários comuns. O sistema inclui gerenciamento de produtos, carrinho de compras e interface responsiva.

## 🚀 Características

### Gerenciamento de Usuários
- Sistema de registro e login
- Dois níveis de acesso: Administrador e Usuário comum
- Autenticação segura com hash de senhas
- Gerenciamento de sessões

### Painel Administrativo
- Interface protegida para administradores
- Gerenciamento completo de produtos (CRUD)
- Gerenciamento de usuários
- Visualização de estoque

### Catálogo de Produtos
- Listagem responsiva de produtos
- Detalhes do produto
- Indicadores de estoque
- Categorização de produtos

### Carrinho de Compras
- Adição/remoção de produtos
- Cálculo automático de totais
- Persistência de dados por usuário
- Verificação de disponibilidade de estoque

### Interface
- Design responsivo com Bootstrap 5
- Layout moderno e intuitivo
- Compatível com dispositivos móveis
- Feedback visual para ações do usuário

## 📋 Pré-requisitos

- Python 3.8 ou superior
- pip (gerenciador de pacotes Python)
- Virtualenv (recomendado)
- SQLite (padrão) ou outro banco de dados SQL suportado pelo SQLAlchemy

## 🔧 Instalação

1. Clone o repositório
```bash
git clone https://github.com/Nardar-Cave/TestLoja.git
cd sistema-estoque
```

2. Crie e ative um ambiente virtual
```bash
python -m venv venv

# Windows
venv\Scripts\activate

# Linux/Mac
source venv/bin/activate
```

3. Instale as dependências
```bash
pip install -r requirements.txt
```

4. Configure as variáveis de ambiente
Crie um arquivo `.env` na raiz do projeto:
```env
SECRET_KEY=sua-chave-secreta-aqui
DATABASE_URL=sqlite:///inventory.db
```

5. Inicialize o banco de dados
```bash
flask db init
flask db migrate
flask db upgrade
```

6. Crie um usuário administrador
```python
from app import app, db
from models import User

with app.app_context():
    admin = User(email='admin@example.com', is_admin=True)
    admin.set_password('senha123')
    db.session.add(admin)
    db.session.commit()
```

7. Execute a aplicação
```bash
python app.py
```

## 🚦 Rotas Principais

- `/` - Página inicial (catálogo de produtos)
- `/login` - Login de usuários
- `/register` - Registro de novos usuários
- `/cart` - Carrinho de compras
- `/admin` - Painel administrativo (requer login de admin)

## ⚠️ Limitações e Considerações

1. **Segurança**
   - O sistema utiliza autenticação básica
   - Não implementa autenticação de dois fatores
   - Senhas têm requisitos mínimos básicos

2. **Banco de Dados**
   - Configurado com SQLite por padrão
   - Para produção, considere migrar para PostgreSQL ou MySQL
   - Backup automático não implementado

3. **Carrinho**
   - Não mantém itens após logout
   - Não implementa processamento de pagamentos
   - Verificação de estoque apenas no momento da adição

4. **Imagens**
   - Armazena apenas URLs de imagens
   - Não inclui upload de imagens
   - Não implementa CDN

5. **Performance**
   - Não implementa cache
   - Paginação básica
   - Sem otimização para grandes volumes de dados

## 🔒 Segurança

- Altere a `SECRET_KEY` em produção
- Implemente HTTPS em produção
- Mantenha as dependências atualizadas
- Revise permissões de arquivos em produção
- Implemente rate limiting para APIs
- Configure adequadamente o CORS

## 📝 Boas Práticas

1. **Ambiente de Desenvolvimento**
   - Use ambiente virtual
   - Mantenha requirements.txt atualizado
   - Configure .gitignore adequadamente

2. **Banco de Dados**
   - Faça backup regularmente
   - Use migrations para alterações
   - Monitore o crescimento do banco

3. **Código**
   - Siga PEP 8
   - Documente funções e classes
   - Implemente logs adequados

## 🤝 Contribuindo

1. Faça um Fork do projeto
2. Crie uma Branch para sua Feature (`git checkout -b feature/AmazingFeature`)
3. Faça o Commit de suas mudanças (`git commit -m 'Add some AmazingFeature'`)
4. Faça o Push para a Branch (`git push origin feature/AmazingFeature`)
5. Abra um Pull Request

## ✅ TODO

- [ ] Implementar recuperação de senha
- [ ] Adicionar suporte a múltiplas imagens por produto
- [ ] Implementar sistema de notificações
- [ ] Adicionar relatórios de vendas
- [ ] Implementar sistema de cupons
- [ ] Adicionar integração com gateway de pagamento
- [ ] Implementar sistema de avaliações de produtos
- [ ] Adicionar histórico de pedidos
- [ ] Implementar sistema de busca avançada
