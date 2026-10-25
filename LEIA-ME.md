# CDG SIS — Clínica Digital Sistema de Gerenciamento

## Configuração do servidor (uma única vez, feita pelo administrador)

1. **Firebase** (console.firebase.google.com): crie um projeto.
2. **Authentication › Método de login**: ative **E-mail/senha**.
3. **Firestore Database**: crie o banco (modo produção, região `southamerica-east1`).
4. **Firestore › Regras**: cole o conteúdo de `firestore.rules` e clique em **Publicar**.
5. **Configurações do projeto › Seus apps › Web (`</>`)**: registre o app e copie o `firebaseConfig`.
6. Abra `cdg-sis.html` num editor, procure `FIREBASE_CONFIG_EMBUTIDA` e cole o objeto no lugar de `null`:
   ```js
   const FIREBASE_CONFIG_EMBUTIDA = { apiKey: '...', authDomain: '...', projectId: '...', appId: '...' };
   ```
7. Envie o arquivo para o repositório do GitHub (ative o **GitHub Pages** do repositório).
8. **Authentication › Configurações › Domínios autorizados**: adicione `seu-usuario.github.io`.
9. Abra o endereço do GitHub Pages e clique em **Primeiro acesso da clínica** para criar o administrador. Faça isso logo após publicar as regras: depois do primeiro administrador, essa opção desaparece.
10. Em **Administração › Profissionais › Criar login**, cadastre o acesso de cada profissional.

## Segurança
- Os valores do `firebaseConfig` não são segredos (todo app web os expõe). A proteção dos dados está nas regras do passo 4 e no login de cada usuário.
- Recomendado: no Google Cloud Console › APIs e serviços › Credenciais, restrinja a chave de API ao seu domínio `seu-usuario.github.io/*`.
- Usuários comuns nunca veem a configuração do servidor: ela vive no arquivo, não na tela.

## Versão
x.y.z — o último número sobe a cada alteração até 50; depois sobe o do meio e o último zera; ao chegar a 10 no meio, sobe o primeiro (1.0.50 → 1.1.0; 1.9.50 → 2.0.0).
