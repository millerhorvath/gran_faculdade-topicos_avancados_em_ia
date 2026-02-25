# ⚠️ Problemas Conhecidos e Soluções (Troubleshooting)

Este arquivo documenta os problemas mais comuns que os alunos podem enfrentar ao configurar o ambiente de laboratório para a disciplina de **Tópicos Avançados em Inteligência Artificial** e como resolvê-á-los.

---

### 1. Erro PSSecurityException (Windows / PowerShell)

🚩 **Sintoma:** Ao tentar ativar o ambiente virtual no PowerShell rodando `venv\Scripts\activate`, você recebe um erro contendo o termo `"PSSecurityException"` informando que a execução de scripts foi desabilitada neste sistema.

🔍 **Causa:** Por padrão, o PowerShell no Windows vem com uma política de execução restrita que impede a execução de qualquer script (mesmo os locais) por questões de segurança.

✅ **Solução:**
1. Abra o PowerShell.
2. Execute primeiro o comando de desbloqueio para o seu usuário:
```powershell
Set-ExecutionPolicy Unrestricted -Scope CurrentUser
```
3. Feito isso, navegue novamente até a pasta do laboratório e tente ativar o ambiente virtual com `venv\Scripts\activate`. O erro não deve mais ocorrer.

---

### 2. Erro [Errno 2] No such file or directory (MAX_PATH no Windows)

🚩 **Sintoma:** Ao tentar instalar as dependências rodando `pip install -r requirements.txt`, a instalação falha repentinamente com mensagens de erro vermelhas similares a `[Errno 2] No such file or directory` relativas a falhas ao acessar o diretório de alguma biblioteca (como `jedi` ou `django-stubs`).

🔍 **Causa:** O Windows possui um limite histórico e padrão que restringe o tamanho total do caminho de um arquivo ou diretório (MAX_PATH) a somente 260 caracteres. Se a pasta onde você clonou ou baixou este repositório estiver muito profunda (por exemplo, dentro de várias sub-pastas aninhadas no seu Google Drive, OneDrive ou Documentos), na hora do `pip` baixar e descompactar dependências complexas num diretório como `venv/Lib/site-packages/...`, esse limite é facilmente atingido e o Windows bloqueia a criação do arquivo.

⭐ **Solução (Recomendada):** Mover o laboratório!
A forma mais simples de resolver é **mover a pasta raiz do projeto (`Lab/`) para um local mais próximo da raiz do seu disco rígido**. 
Por exemplo, coloque a pasta em `C:\Projetos\Lab\`. Feito isso, abra o terminal no novo local e tente rodar a instalação do `requirements.txt` novamente.

🛠️ **Solução Alternativa (Habilitar Long Paths do Windows):**
Se você deseja manter os arquivos no local original, você pode dizer para o Windows ignorar esse limite de 260 caracteres editando o Registro e habilitando a política *LongPathsEnabled*.
1. Abra um terminal do PowerShell **como Administrador** (clique com botão direito no menu iniciar > Windows PowerShell (Admin)).
2. Execute o comando longo abaixo para habilitar os caminhos longos:
```powershell
New-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Control\FileSystem" -Name "LongPathsEnabled" -Value 1 -PropertyType DWORD -Force
```
3. Volte ao seu terminal normal e tente rodar a instalação novamente.
---

### 3. Erro "fatal: bad object refs/desktop.ini" (Git + Google Drive)

🚩 **Sintoma:** Ao tentar rodar comandos do Git (como `git pull`, `git push` ou `git commit`), você recebe um erro similar a `fatal: bad object refs/desktop.ini`.

🔍 **Causa:** Quando o repositório Git está em uma pasta sincronizada pelo **Google Drive** no Windows, o Drive frequentemente cria arquivos ocultos chamados `desktop.ini` dentro das pastas do sistema do Git (como `.git/refs/`). O Git tenta interpretar esses arquivos como referências de commits, o que causa a falha.

✅ **Solução:**
Você deve remover esses arquivos de dentro da pasta oculta `.git`.
1. Abra o Terminal ou PowerShell na raiz do seu projeto.
2. Execute o comando abaixo para remover recursivamente todos os arquivos `desktop.ini` que estiverem dentro da pasta `.git`:
```powershell
Get-ChildItem -Path ".git" -Recurse -Filter "desktop.ini" -Force | Remove-Item -Force
```
3. Após rodar o comando, tente executar o comando Git original novamente.
