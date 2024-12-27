# Configuração de Ambientes Python
 
## Objetivo
O objetivo deste arquivo é documentar como configurar diferentes ambientes de Python na mesma máquina Windows.

## Recursos
Serão utilizadas as bibliotecas **pyenv**, **venv** e **poetry**.  
Todos os recursos serão instalados utilizando **pipx**, para isolar também o usuário da máquina.

---

### PYENV
- **O que é?**  
  Um emulador de versões do Python. Com ele, você consegue definir diferentes versões do Python em cada projeto (diretório).

- **Como instalar**  
  Será utilizado o pyenv-win.

  1. Instale o pyenv-win no PowerShell.
  ```powershell
  Invoke-WebRequest -UseBasicParsing -Uri "https://raw.githubusercontent.com/pyenv-win/pyenv-win/master/pyenv-win/install-pyenv-win.ps1" -OutFile "./install-pyenv-win.ps1"; &"./install-pyenv-win.ps1"
  ```
  2. Reabra o PowerShell.
  3. Execute `pyenv --version` para verificar se a instalação foi bem-sucedida.
  4. Execute `pyenv install -l` para ver a lista de versões do Python suportadas.
  5. Execute `pyenv install <versão>` para instalar a versão desejada.
  6. Execute `pyenv global <versão>` para definir uma versão como global.
  7. Verifique qual versão do Python está sendo usada:
  ```powershell
  > pyenv version
  <versão> (definido por \caminho\para\.pyenv\pyenv-win\.python-version)
  ```
  8. Verifique se o Python está funcionando:
  ```powershell
  > python -c "import sys; print(sys.executable)"
  \caminho\para\.pyenv\pyenv-win\versions\<versão>\python.exe
  ```
  - **IMPORTANTE:** Após a instalação, configure as variáveis de ambiente do Windows:
    1. Adicione os caminhos abaixo no **Path**:
       - `%USERPROFILE%\.pyenv\pyenv-win\bin`
       - `%USERPROFILE%\.pyenv\pyenv-win\shims`
    2. Garanta que os caminhos do pyenv estejam **acima** dos paths do Python local para ter prioridade.

- **Comandos úteis**
  - `pyenv versions` → Lista as versões instaladas.
  - `pyenv install --list` → Exibe versões disponíveis.
  - `pyenv install <versão>` → Instala uma versão específica.
  - `pyenv global <versão>` → Define uma versão como global.
  - `pyenv local <versão>` → Define uma versão local criando um arquivo `.python-version`.
  - `pyenv rehash` → Atualiza os comandos do pyenv após instalar versões.

---

### VENV
- **O que é?**  
  Um módulo nativo do Python que virtualiza bibliotecas. Quando a virtualização está ativa, todos os pacotes instalados via `pip` serão específicos para aquele ambiente.

- **Como instalar**  
  O módulo já vem nativo no Python.

- **Comandos úteis**
  - `python -m venv .venv` → Cria a virtualização no diretório atual.
  - `.\.venv\Scripts\activate` → Ativa a virtualização no Windows.
  - `deactivate` → Desativa a virtualização.

---

### POETRY
- **O que é?**  
  Um gerenciador de dependências do Python. Ele utiliza o venv e permite visualizar e controlar bibliotecas instaladas, listando apenas aquelas solicitadas diretamente.

- **Como instalar**  
  Certifique-se de que o `pipx` esteja instalado e execute:
  ```bash
  pipx install poetry
  ```

- **Comandos úteis**
  - `poetry new <projeto>` → Cria um diretório padrão para projetos.
  - `poetry env use <versão>` → Define a versão do Python e ativa o venv (requer pyenv configurado).
  - `poetry add <biblioteca>` → Instala uma biblioteca e suas dependências.
  - `poetry remove <biblioteca>` → Remove uma biblioteca e suas dependências.

---

## Forma de uso
1. Instale o pyenv-win e o poetry.
2. Defina a versão do Python com o pyenv.
3. Use o poetry para gerenciar as bibliotecas.
4. Ative e desative os ambientes com venv.
