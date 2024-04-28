# GITHUB ACTIONS
--------------

[//]: # (version: 1.0)
[//]: # (author: Jose Carlos Limones Hernandez)
[//]: # (date: 2024-04-27)

## Tabla de contenidos

- [GITHUB ACTIONS](#github-actions)
  - [Tabla de contenidos](#tabla-de-contenidos)
  - [Introducción](#introducción)
  - [Inicio](#inicio)
  - [Cuando se lanza la ACTION](#cuando-se-lanza-la-action)
  - [Jobs](#jobs)
  - [STEPS](#steps)
  - [Configuracion de python](#configuracion-de-python)
  - [Ejecucion del codigo](#ejecucion-del-codigo)
  - [Ejemplo](#ejemplo)

## Introducción
[Tabla de contenidos](#tabla-de-contenidos)

[ACTIONS](https://docs.github.com/es/actions):

Automatiza, personaliza y ejecuta tus flujos de trabajo de desarrollo de software directamente en tu repositorio con GitHub Actions. Puedes descubrir, crear y compartir acciones para realizar cualquier trabajo que quieras, incluido CI/CD, y combinar acciones en un flujo de trabajo completamente personalizado.

## Inicio
[Tabla de contenidos](#tabla-de-contenidos)

Para utilizar github actions lo primero que debemos hacer es crear nuestro archivo de configuracion ***.yml***.

```yml
name: Stats #Este sera el nombre de la automatizacion

on:   # Cuando queremos que se lance la "action"
  schedule:
    - cron: '0 0 * * *'

jobs:
  build:
    if: github.repository == 'mouredev/roadmap-retos-programacion' && github.ref == 'refs/heads/main'
    runs-on: ubuntu-latest

    permissions:
      contents: write

    steps:
      - name: Checkout repo
        uses: actions/checkout@v4

      - name: Setup Python
        uses: actions/setup-python@v5
        with:
          python-version: '3.11'

      - name: Run script
        run: python ./Roadmap/stats.py

      - name: Commit and Push changes
        uses: stefanzweifel/git-auto-commit-action@v5
        with:
          commit_message: Update stats
          commit_user_name: Brais Moure [GitHub Actions]
          commit_user_email: mouredev@gmail.com
          commit_author: mouredev <mouredev@gmail.com>
```

## Cuando se lanza la ACTION
[Tabla de contenidos](#tabla-de-contenidos)

- ***on:***
  - push -> Querremos que la ACTION se lance cuando hagamos push.
    ```yml
    on: 
        push:
            branches: [ main ]
    ```
  - Cada vez que se solicite una pull request.
  - programar una **cron**(proceso recurrente), se ejecutra la ACTION cada intervalo de tiempo determinado en el archivo ***.yml***.

  - Para **cron**:
  ```yml
  schedule:
    - cron: '* * * * *' # Se ejecutaria cada minuto
    - cron: '30 8 1 1 *' # Se ejecutaria el dia 1 del mes 1 a las 8:30
    - cron: '30 8 * * *' # Todos los dias de la semana a las 8:30.
    - cron: '0 0 * * *' # Todos los dias de la semana a las 00:00.
    - cron: '*/15 * * * *' # Se ejecutaria cada 15 minutos
  ```
  Cada** * **representa un dia de la semana
## Jobs
[Tabla de contenidos](#tabla-de-contenidos)

- Los jobs es una regla obligatoria en nuestra ACTION, y basicmente es un conjunto de pasos que se tienen que ejecutar en nuestra ACTION.
- Dentro de los jobs, los primero que tenempos que configurar es nuestra construccion(build:).
> [!IMPORTANT]
> Hay mas opciones para **jobs** dependera del proyecto que vayamos a hacer.
- Indicaremos en que tipo de maquina queremos hacerlo.(runs-on)
- Por ultimo le indicaremos los pasos a seguir.(steps)
```yml
jobs:
    build:
        runs-on: ubuntu-latest

    steps:  
```

## STEPS
[Tabla de contenidos](#tabla-de-contenidos)

- Dentro de los steps le indicaremos las ACTIONS que queremos realizar.(uses).
- Para nuestras actions podemos usar las que ya ha creado la [comunidad](https://github.com/orgs/actions/repositories):
- Con la primera linea podemos hacer que se traiga el repositorio a nuestra action.
- Aqui tenemos un ejemplo de una action creada por github con los parametros que podemos usar:
```yml
- uses: actions/checkout@v4
  with:
    # Repository name with owner. For example, actions/checkout
    # Default: ${{ github.repository }}
    repository: ''

    # The branch, tag or SHA to checkout. When checking out the repository that
    # triggered a workflow, this defaults to the reference or SHA for that event.
    # Otherwise, uses the default branch.
    ref: ''

    # Personal access token (PAT) used to fetch the repository. The PAT is configured
    # with the local git config, which enables your scripts to run authenticated git
    # commands. The post-job step removes the PAT.
    #
    # We recommend using a service account with the least permissions necessary. Also
    # when generating a new PAT, select the least scopes necessary.
    #
    # [Learn more about creating and using encrypted secrets](https://help.github.com/en/actions/automating-your-workflow-with-github-actions/creating-and-using-encrypted-secrets)
    #
    # Default: ${{ github.token }}
    token: ''

    # SSH key used to fetch the repository. The SSH key is configured with the local
    # git config, which enables your scripts to run authenticated git commands. The
    # post-job step removes the SSH key.
    #
    # We recommend using a service account with the least permissions necessary.
    #
    # [Learn more about creating and using encrypted secrets](https://help.github.com/en/actions/automating-your-workflow-with-github-actions/creating-and-using-encrypted-secrets)
    ssh-key: ''

    # Known hosts in addition to the user and global host key database. The public SSH
    # keys for a host may be obtained using the utility `ssh-keyscan`. For example,
    # `ssh-keyscan github.com`. The public key for github.com is always implicitly
    # added.
    ssh-known-hosts: ''

    # Whether to perform strict host key checking. When true, adds the options
    # `StrictHostKeyChecking=yes` and `CheckHostIP=no` to the SSH command line. Use
    # the input `ssh-known-hosts` to configure additional hosts.
    # Default: true
    ssh-strict: ''

    # The user to use when connecting to the remote SSH host. By default 'git' is
    # used.
    # Default: git
    ssh-user: ''

    # Whether to configure the token or SSH key with the local git config
    # Default: true
    persist-credentials: ''

    # Relative path under $GITHUB_WORKSPACE to place the repository
    path: ''

    # Whether to execute `git clean -ffdx && git reset --hard HEAD` before fetching
    # Default: true
    clean: ''

    # Partially clone against a given filter. Overrides sparse-checkout if set.
    # Default: null
    filter: ''

    # Do a sparse checkout on given patterns. Each pattern should be separated with
    # new lines.
    # Default: null
    sparse-checkout: ''

    # Specifies whether to use cone-mode when doing a sparse checkout.
    # Default: true
    sparse-checkout-cone-mode: ''

    # Number of commits to fetch. 0 indicates all history for all branches and tags.
    # Default: 1
    fetch-depth: ''

    # Whether to fetch tags, even if fetch-depth > 0.
    # Default: false
    fetch-tags: ''

    # Whether to show progress status output when fetching.
    # Default: true
    show-progress: ''

    # Whether to download Git-LFS files
    # Default: false
    lfs: ''

    # Whether to checkout submodules: `true` to checkout submodules or `recursive` to
    # recursively checkout submodules.
    #
    # When the `ssh-key` input is not provided, SSH URLs beginning with
    # `git@github.com:` are converted to HTTPS.
    #
    # Default: false
    submodules: ''

    # Add repository path as safe.directory for Git global config by running `git
    # config --global --add safe.directory <path>`
    # Default: true
    set-safe-directory: ''

    # The base URL for the GitHub instance that you are trying to clone from, will use
    # environment defaults to fetch from the same instance that the workflow is
    # running from unless specified. Example URLs are https://github.com or
    # https://my-ghes-server.example.com
    github-server-url: ''
```

> [!IMPORTANT]
> En [Github Marketplace](https://github.com/marketplace) podremos encontrar mas actions.

## Configuracion de python
[Tabla de contenidos](#tabla-de-contenidos)

[setup python](https://github.com/actions/setup-python)

Para utilizarlo:
```yml
steps:
- uses: actions/checkout@v4
- uses: actions/setup-python@v5
  with:
    python-version: '3.11' 
- run: python my_script.py
```

## Ejecucion del codigo
[Tabla de contenidos](#tabla-de-contenidos)

El siguiente paso sera indicarle que ejecute el codigo(run):
```yml
- run: python my_script.py
```

> [!NOTE]
> Es importante darle un name a cada step para entender bien los logs.

## Ejemplo
[Tabla de contenidos](#tabla-de-contenidos)

**stats.py**:
```yml
name: Stats

on:
    push:
        branches: [ main ]

jobs:
    build:
        runs-on: ubuntu-lastest

        permissions:
            # Give the default GITHUB_TOKEN write permission to commit and push the
            # added or changed files to the repository.
            contents: write

        steps:
            - name: Checkout repo
              uses: actions/checkout@v4

            - name: Setup Python
              uses: actions/setup-python@v5
            with:
                python-version: '3.11'

            - name: Run Script
              run: python ./Roadmap/stats.py

            - name: Commit and push actions
              uses: stefanzweifel/git-auto-commit-action@v5
              widh:
                commit_message: Update Stats
                commit_user_name: JLimones (GitHub Actions)
                commit_user_name: josec.limones@gmail.com
                commit_author: jlimones
```

> [!NOTE]
> Este tutorial o guia esta basado en el [video](https://www.youtube.com/watch?v=pNtcTmCiXzw) de [mouredev](https://mouredev.com/). El repositorio es [roadmap-retos-programacion](https://github.com/mouredev/roadmap-retos-programacion).
> 
> Desde aqui me gustaria agradecerle la labor que hace para la comunidad dev.