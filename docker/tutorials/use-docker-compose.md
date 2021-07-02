---
title: 'Didacticiel de l’ancrage-partie 7 : utiliser Docker Compose'
description: Décrit comment installer et utiliser Docker Compose.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 645d168aefe05040193d564d5c158acfb6688c11
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222745"
---
# <a name="use-docker-compose"></a>Utiliser Docker Compose

[Docker compose](https://docs.docker.com/compose/) est un outil qui a été développé pour aider à définir et partager des applications à plusieurs conteneurs. Avec compose, vous pouvez créer un fichier baYAML pour définir les services et avec une seule commande, peut faire tourner tout le contenu vers le haut ou le déchirer.

Le principal avantage de l’utilisation de compose est que vous pouvez *définir la pile* de votre application dans un fichier, la garder à la racine de votre projet référentiel (elle est maintenant contrôlée par la version) et permettre facilement à quelqu’un d’autre de contribuer à votre projet. Une personne aurait uniquement besoin de cloner votre référentiel et de démarrer l’application compose. en fait, vous pouvez voir un certain nombre de projets sur GitHub/GitLab.

Alors, comment commencer ?

## <a name="install-docker-compose"></a>Installer Docker Compose

si vous avez installé le bureau de l’amarrage pour Windows ou Mac, vous avez déjà Docker Compose ! Les instances de lecture avec l’arrimeur disposent déjà d’Docker Compose également installées. Si vous utilisez un ordinateur Linux, vous devez installer Docker Compose en suivant [les instructions fournies ici](https://docs.docker.com/compose/install/).

Après l’installation, vous devez être en mesure d’exécuter les éléments suivants et d’afficher les informations de version.

```bash
docker-compose version
```

## <a name="create-the-compose-file"></a>Créer le fichier compose

1. À la racine du projet d’application, créez un fichier nommé `docker-compose.yml` .

1. Dans le fichier compose, nous commençons par définir la version du schéma. Dans la plupart des cas, il est préférable d’utiliser la version la plus récente prise en charge. Vous pouvez consulter la [référence de fichier compose](https://docs.docker.com/compose/compose-file/) pour les versions de schéma actuelles et la matrice de compatibilité.

    ```yaml
    version: "3.7"
    ```

1. Ensuite, définissez la liste des services (ou conteneurs) que vous souhaitez exécuter dans le cadre de votre application.

    ```yaml hl_lines="3"
    version: "3.7"

    services:
    ```

Et maintenant, vous commencerez à migrer un service à la fois dans le fichier compose.

## <a name="define-the-app-service"></a>Définir le App Service

Pour vous souvenir, il s’agit de la commande que vous avez utilisée pour définir votre conteneur d’application (remplacez les ` \ ` caractères par `` ` `` dans Windows PowerShell).

```bash
docker run -dp 3000:3000 \
  -w /app -v ${PWD}:/app \
  --network todo-app \
  -e MYSQL_HOST=mysql \
  -e MYSQL_USER=root \
  -e MYSQL_PASSWORD=secret \
  -e MYSQL_DB=todos \
  node:12-alpine \
  sh -c "yarn install && yarn run dev"
```

1. Tout d’abord, définissez l’entrée du service et l’image du conteneur. Vous pouvez choisir n’importe quel nom pour le service. Le nom devient automatiquement un alias réseau, ce qui est utile lors de la définition du service MySQL.

    ```yaml hl_lines="4 5"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
    ```

1. En règle générale, la commande est proche de la `image` définition, bien qu’il n’y ait aucune exigence de classement. Donc, continuez et déplacez-le dans le fichier.

    ```yaml hl_lines="6"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
    ```

1. Migrez la `-p 3000:3000` partie de la commande en définissant le `ports` pour le service. Vous allez utiliser la [syntaxe abrégée](https://docs.docker.com/compose/compose-file/#short-syntax-1) ici, mais il existe également une [syntaxe longue](https://docs.docker.com/compose/compose-file/#long-syntax-1) plus détaillée disponible.

    ```yaml hl_lines="7 8"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
        ports:
          - 3000:3000
    ```

1. Ensuite, migrez le répertoire de travail ( `-w /app` ) et le mappage de volume ( `-v ${PWD}:/app` ) à l’aide des `working_dir` `volumes` définitions et. [Les volumes](https://docs.docker.com/compose/compose-file/#short-syntax-3) ont également une syntaxe [longue et longue](https://docs.docker.com/compose/compose-file/#long-syntax-3) .

   L’un des avantages des définitions de volume Docker Compose est que vous pouvez utiliser des chemins d’accès relatifs à partir du répertoire actif.

    ```yaml hl_lines="9 10 11"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
        ports:
          - 3000:3000
        working_dir: /app
        volumes:
          - ./:/app
    ```

1. Enfin, migrez les définitions de variables d’environnement à l’aide de la `environment` clé.

    ```yaml hl_lines="12 13 14 15 16"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
        ports:
          - 3000:3000
        working_dir: /app
        volumes:
          - ./:/app
        environment:
          MYSQL_HOST: mysql
          MYSQL_USER: root
          MYSQL_PASSWORD: secret
          MYSQL_DB: todos
    ```

### <a name="define-the-mysql-service"></a>Définir le service MySQL

Maintenant, il est temps de définir le service MySQL. La commande que vous avez utilisée pour ce conteneur était la suivante (remplacez les ` \ ` caractères par `` ` `` dans Windows PowerShell) :

```bash
docker run -d \
  --network todo-app --network-alias mysql \
  -v todo-mysql-data:/var/lib/mysql \
  -e MYSQL_ROOT_PASSWORD=secret \
  -e MYSQL_DATABASE=todos \
  mysql:5.7
```

1. Tout d’abord, définissez le nouveau service et nommez-le `mysql` pour qu’il récupère automatiquement l’alias réseau. Spécifiez également l’image à utiliser.

    ```yaml hl_lines="6 7"
    version: "3.7"

    services:
      app:
        # The app service definition
      mysql:
        image: mysql:5.7
    ```

1. Ensuite, définissez le mappage du volume. Lorsque vous avez exécuté le conteneur avec `docker run` , le volume nommé a été créé automatiquement. Toutefois, cela ne se produit pas lors de l’exécution de avec compose. Vous devez définir le volume dans la section de niveau supérieur `volumes:` , puis spécifier le point de montage dans la configuration du service. En fournissant simplement le nom du volume, les options par défaut sont utilisées. Toutefois, de [nombreuses autres options sont disponibles](https://github.com/compose-spec/compose-spec/blob/master/spec.md#volumes-top-level-element) .

    ```yaml hl_lines="8 9 10 11 12"
    version: "3.7"

    services:
      app:
        # The app service definition
      mysql:
        image: mysql:5.7
        volumes:
          - todo-mysql-data:/var/lib/mysql
    
    volumes:
      todo-mysql-data:
    ```

1. Enfin, il vous suffit de spécifier les variables d’environnement.

    ```yaml hl_lines="10 11 12"
    version: "3.7"

    services:
      app:
        # The app service definition
      mysql:
        image: mysql:5.7
        volumes:
          - todo-mysql-data:/var/lib/mysql
        environment: 
          MYSQL_ROOT_PASSWORD: secret
          MYSQL_DATABASE: todos
    
    volumes:
      todo-mysql-data:
    ```

À ce stade, le `docker-compose.yml` résultat final doit ressembler à ceci :

```yaml
version: "3.7"

services:
  app:
    image: node:12-alpine
    command: sh -c "yarn install && yarn run dev"
    ports:
      - 3000:3000
    working_dir: /app
    volumes:
      - ./:/app
    environment:
      MYSQL_HOST: mysql
      MYSQL_USER: root
      MYSQL_PASSWORD: secret
      MYSQL_DB: todos

  mysql:
    image: mysql:5.7
    volumes:
      - todo-mysql-data:/var/lib/mysql
    environment: 
      MYSQL_ROOT_PASSWORD: secret
      MYSQL_DATABASE: todos

volumes:
  todo-mysql-data:
```

## <a name="run-the-application-stack"></a>Exécuter la pile d’applications

Maintenant que vous disposez du `docker-compose.yml` fichier, vous pouvez le démarrer !

1. Tout d’abord, assurez-vous qu’aucune autre copie de l’application et de la base de données n’est en cours d’exécution ( `docker ps` et `docker rm -f <ids>` ).

1. Démarrez la pile d’applications à l’aide de la `docker-compose up` commande. Ajoutez l' `-d` indicateur pour tout exécuter en arrière-plan. vous pouvez également cliquer avec le bouton droit sur votre fichier compose et sélectionner l’option **composer** pour la barre latérale du VS Code. 

    ```bash
    docker-compose up -d
    ```

    Lorsque vous l’exécutez, vous devez obtenir une sortie semblable à celle-ci :

    ```plaintext
    Creating network "app_default" with the default driver
    Creating volume "app_todo-mysql-data" with default driver
    Creating app_app_1   ... done
    Creating app_mysql_1 ... done
    ```

    Vous remarquerez que le volume a été créé et qu’il s’agit d’un réseau. Par défaut, Docker Compose crée automatiquement un réseau spécifiquement pour la pile d’applications (ce qui explique pourquoi vous n’en avez pas défini un dans le fichier compose).

1. Examinez les journaux à l’aide de la `docker-compose logs -f` commande. Vous verrez les journaux de chacun des services entrelacés dans un seul flux. Cela s’avère extrêmement utile lorsque vous souhaitez surveiller les problèmes liés au minutage. L' `-f` indicateur « suit » le journal. vous obtiendrez donc une sortie en temps réel lors de sa génération.

    Si vous ne le souhaitez pas, vous verrez une sortie semblable à celle-ci :

    ```plaintext
    mysql_1  | 2019-10-03T03:07:16.083639Z 0 [Note] mysqld: ready for connections.
    mysql_1  | Version: '5.7.27'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  MySQL Community Server (GPL)
    app_1    | Connected to mysql db at host mysql
    app_1    | Listening on port 3000
    ```

    Le nom du service est affiché au début de la ligne (généralement en couleur) pour aider à distinguer les messages. Si vous souhaitez afficher les journaux d’un service spécifique, vous pouvez ajouter le nom du service à la fin de la commande logs (par exemple, `docker-compose logs -f app` ).

    > [!TIP]
    > En **attente de la base de BD avant le démarrage de l’application** Lorsque l’application démarre, elle est en fait en attente et attend que MySQL soit prêt avant de tenter de se connecter à it.DocKer ne dispose pas d’une prise en charge intégrée pour attendre qu’un autre conteneur soit entièrement opérationnel, en cours d’exécution et prêt avant de démarrer un autre conteneur. Pour les projets basés sur des nœuds, vous pouvez utiliser la dépendance [Wait-port](https://github.com/dwmkerr/wait-port) . Des projets similaires existent pour d’autres langages et infrastructures.

1. À ce stade, vous devez être en mesure d’ouvrir votre application et de la voir en cours d’exécution. Et Bonjour ! Vous êtes en train d’effectuer une seule commande !

## <a name="see-the-app-stack-in-the-docker-extension"></a>Consultez la pile d’applications dans l’extension de l’amarrage

Si vous examinez l’extension de l’ancrage, vous pouvez modifier les options de regroupement à l’aide des options « roue dentée » et « Group by ». dans ce cas, vous souhaitez voir les conteneurs regroupés par compose Project nom :

![Extension VS avec compose](media/vs-app-project-collapsed.png)

Si vous désactivez le réseau, vous verrez les deux conteneurs que vous avez définis dans le fichier compose.

![Extension VS avec compose développé](media/vs-app-project-expanded.png)

## <a name="tear-it-all-down"></a>Détacher tout

lorsque vous êtes prêt à le détacher, exécutez simplement `docker-compose down` , ou cliquez avec le bouton droit sur l’application dans la liste des conteneurs de l’extension VS Code ancrage et sélectionnez **composer**. Les conteneurs s’arrêtent et le réseau est supprimé.

> [!WARNING]
> **Suppression de volumes** Par défaut, les volumes nommés dans votre fichier compose ne sont pas supprimés lors de l’exécution de `docker-compose down` . Si vous souhaitez supprimer les volumes, vous devez ajouter l' `--volumes` indicateur.

Une fois que vous avez interrompu, vous pouvez basculer vers un autre projet, exécuter `docker-compose up` et être prêt à contribuer à ce projet. Il n’est pas vraiment plus simple que ça !

## <a name="recap"></a>Récapitulatif

Dans cette section, vous avez appris à Docker Compose et à savoir comment il simplifie considérablement la définition et le partage des applications multiservice. Vous avez créé un fichier compose en traduisant les commandes que vous utilisiez dans le format de composition approprié.

À ce stade, vous commencez à encapsuler le didacticiel. Toutefois, il existe quelques pratiques recommandées sur la création d’images à couvrir, car il existe un grand problème avec le fichier dockerfile que vous avez utilisé. Nous allons donc jeter un œil !

## <a name="next-steps"></a>Étapes suivantes

Poursuivez avec le didacticiel.

> [!div class="nextstepaction"]
> [Meilleures pratiques pour la création d’images](image-building-best-practices.md)
