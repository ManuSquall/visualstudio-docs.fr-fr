---
title: 'Didacticiel de l’ancrage-partie 6 : applications à plusieurs conteneurs'
description: Comment configurer la mise en réseau entre les conteneurs et ajouter un conteneur pour une base de données MySQL.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: d23d1f5d94729741630ee76263fd5b32041e9cfd
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222914"
---
# <a name="multi-container-apps"></a>Application à plusieurs conteneurs

Jusqu’à présent, vous travaillez avec des applications à un seul conteneur. Toutefois, vous allez maintenant ajouter MySQL à la pile d’applications. La question suivante se pose souvent : «où MySQL s’exécutera-t-il ? L’installer dans le même conteneur ou l’exécuter séparément ? En général, **chaque conteneur doit faire une chose et le faire correctement.** Voici quelques raisons :

- Il y a de bonnes chances que vous deviez mettre à l’échelle les API et les serveurs frontaux différemment des bases de données
- Des conteneurs distincts vous permettent d’isoler les versions et les mises à jour
- Si vous pouvez utiliser un conteneur pour la base de données localement, vous souhaiterez peut-être utiliser un service géré pour la base de données en production. Vous ne souhaitez pas expédier votre moteur de base de données avec votre application.
- L’exécution de plusieurs processus nécessite un gestionnaire de processus (le conteneur démarre un seul processus), ce qui complique le démarrage/l’arrêt du conteneur.

Et il y a plus de raisons. Par conséquent, vous allez mettre à jour votre application pour qu’elle fonctionne de la manière suivante :

![Application todo connectée au conteneur MySQL](media/multi-app-architecture.png)

## <a name="container-networking"></a>Mise en réseau de conteneurs

N’oubliez pas que les conteneurs, par défaut, s’exécutent de manière isolée et ne savent rien sur d’autres processus ou conteneurs sur le même ordinateur. Donc, comment autoriser un conteneur à communiquer avec un autre ? La réponse est la **mise en réseau**. À présent, vous n’êtes pas obligé d’être un ingénieur réseau (Hourra !). Mémorisez simplement cette règle...

> [!NOTE]
> Si deux conteneurs se trouvent sur le même réseau, ils peuvent communiquer entre eux. Si ce n’est pas le cas, ils ne le sont pas.

## <a name="start-mysql"></a>Démarrez MySQL

Il existe deux façons de placer un conteneur sur un réseau : l’assigner au démarrage ou connecter un conteneur existant. Pour le moment, vous allez d’abord créer le réseau et attacher le conteneur MySQL au démarrage.

1. Créez le réseau.

    ```bash
    docker network create todo-app
    ```

1. Démarrez un conteneur MySQL et attachez-le au réseau. Nous allons également définir quelques variables d’environnement que la base de données utilisera pour initialiser la base de données (consultez la section « variables d’environnement » dans la liste des hubs de l' [arrimeur MySQL](https://hub.docker.com/_/mysql/)) (remplacez les ` \ ` caractères par `` ` `` dans Windows PowerShell).

    ```bash
    docker run -d \
        --network todo-app --network-alias mysql \
        -v todo-mysql-data:/var/lib/mysql \
        -e MYSQL_ROOT_PASSWORD=secret \
        -e MYSQL_DATABASE=todos \
        mysql:5.7
    ```

    Vous verrez également que vous avez spécifié l' `--network-alias` indicateur. Nous reviendrons ici dans un instant.

    > [!TIP]
    > Vous remarquerez que vous utilisez un nom de volume ici et que vous le `todo-mysql-data` Montez à l' `/var/lib/mysql` emplacement où MySQL stocke ses données. Toutefois, vous n’avez jamais exécuté une `docker volume create` commande. L’ancrage reconnaît que vous souhaitez utiliser un volume nommé et en crée un automatiquement pour vous.

1. Pour confirmer que la base de données est en cours d’exécution, connectez-vous à la base de données et vérifiez qu’elle se connecte.

    ```bash
    docker exec -it <mysql-container-id> mysql -p
    ```

    Lorsque l’invite de mot de passe apparaît, tapez **secret**. Dans l’interpréteur de commandes MySQL, répertoriez les bases de données et vérifiez que la `todos` base de données s’affiche.

    ```cli
    mysql> SHOW DATABASES;
    ```

    La sortie doit ressembler à ceci :

    ```plaintext
    +--------------------+
    | Database           |
    +--------------------+
    | information_schema |
    | mysql              |
    | performance_schema |
    | sys                |
    | todos              |
    +--------------------+
    5 rows in set (0.00 sec)
    ```

    Hourra! Vous avez votre `todos` base de données et celle-ci est prête à être utilisée.

## <a name="connect-to-mysql"></a>Se connecter à MySQL

Maintenant que MySQL est en cours d’exécution, utilisons-le ! Mais la question est... utilisation? Si vous exécutez un autre conteneur sur le même réseau, comment trouver le conteneur (souvenez-vous que chaque conteneur a sa propre adresse IP) ?

Pour le déterminer, vous allez utiliser le conteneur [nicolaka/netpousse](https://github.com/nicolaka/netshoot) , qui est fourni avec un *grand nombre* d’outils utiles pour le dépannage ou le débogage des problèmes de réseau.

1. Démarrez un nouveau conteneur à l’aide de l' `nicolaka/netshoot` image. Veillez à le connecter au même réseau.

    ```bash
    docker run -it --network todo-app nicolaka/netshoot
    ```

1. À l’intérieur du conteneur, utilisez la `dig` commande, qui est un outil DNS utile. Recherchez l’adresse IP du nom d’hôte `mysql` .

    ```bash
    dig mysql
    ```

    Et vous obtiendrez une sortie similaire à celle-ci...

    ```text
    ; <<>> DiG 9.14.1 <<>> mysql
    ;; global options: +cmd
    ;; Got answer:
    ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 32162
    ;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

    ;; QUESTION SECTION:
    ;mysql.             IN  A

    ;; ANSWER SECTION:
    mysql.          600 IN  A   172.23.0.2

    ;; Query time: 0 msec
    ;; SERVER: 127.0.0.11#53(127.0.0.11)
    ;; WHEN: Tue Oct 01 23:47:24 UTC 2019
    ;; MSG SIZE  rcvd: 44
    ```

    Dans la SECTION « réponse », vous verrez un `A` enregistrement pour `mysql` ce qui correspond à `172.23.0.2` (votre adresse IP aura probablement une valeur différente). Bien qu' `mysql` il ne s’agit pas d’un nom d’hôte valide, l’ancrage a pu le résoudre en adresse IP du conteneur qui avait cet alias réseau (n’oubliez pas l' `--network-alias` indicateur que vous avez utilisé précédemment ?).

    Ce que cela signifie... Il suffit à votre application de se connecter à un ordinateur hôte nommé `mysql` et de communiquer avec la base de données ! Il n’est pas encore plus simple que cela !

## <a name="run-your-app-with-mysql"></a>Exécuter votre application avec MySQL

L’application todo prend en charge le paramètre de quelques variables d’environnement pour spécifier les paramètres de connexion MySQL. Il s'agit de :

- `MYSQL_HOST` -nom d’hôte du serveur MySQL en cours d’exécution
- `MYSQL_USER` : nom d’utilisateur à utiliser pour la connexion.
- `MYSQL_PASSWORD` : mot de passe à utiliser pour la connexion.
- `MYSQL_DB` -la base de données à utiliser une fois connecté

> [!WARNING]
> **définition des Paramètres de connexion via des Variables d’environnement** Bien que l’utilisation de variables d’environnement pour définir les paramètres de connexion soit généralement possible pour le développement, elle est fortement déconseillée lors de l’exécution d’applications en production. Pour comprendre pourquoi, découvrez [pourquoi vous ne devez pas utiliser de variables d’environnement pour les données secrètes](https://diogomonica.com/2017/03/27/why-you-shouldnt-use-env-variables-for-secret-data/).
> Un mécanisme plus sécurisé consiste à utiliser la prise en charge du secret fournie par votre infrastructure d’orchestration de conteneur. Dans la plupart des cas, ces secrets sont montés en tant que fichiers dans le conteneur en cours d’exécution. Vous verrez de nombreuses applications (y compris l’image MySQL et l’application TODO) prennent également en charge les variables env avec un `_FILE` suffixe pour pointer vers un fichier contenant le fichier.
> Par exemple, la définition `MYSQL_PASSWORD_FILE` de la fonction var fait en sorte que l’application utilise le contenu du fichier référencé comme mot de passe de connexion. La station d’accueil ne fait rien pour prendre en charge ces variables env. Votre application doit savoir comment rechercher la variable et obtenir le contenu du fichier.

Tout comme expliqué, commencez votre conteneur de développement !

1. Spécifiez chacune des variables d’environnement ci-dessus et connectez le conteneur à votre réseau d’applications (remplacez les ` \ ` caractères par `` ` `` dans Windows PowerShell).

    ```bash hl_lines="3 4 5 6 7"
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

1. Si vous examinez les journaux du conteneur ( `docker logs <container-id>` ), vous devez voir un message indiquant qu’il utilise la base de données MySQL.

    ```plaintext hl_lines="7"
    # Previous log messages omitted
    $ nodemon src/index.js
    [nodemon] 1.19.2
    [nodemon] to restart at any time, enter `rs`
    [nodemon] watching dir(s): *.*
    [nodemon] starting `node src/index.js`
    Connected to mysql db at host mysql
    Listening on port 3000
    ```

1. Ouvrez l’application dans votre navigateur et ajoutez quelques éléments à votre liste TODO.

1. Connecter à la base de données MySQL et prouver que les éléments sont écrits dans la base de données. N’oubliez pas que le mot de passe est **secret**.

    ```bash
    docker exec -ti <mysql-container-id> mysql -p todos
    ```

    Et dans le shell MySQL, exécutez la commande suivante :

    ```plaintext
    mysql> select * from todo_items;
    +--------------------------------------+--------------------+-----------+
    | id                                   | name               | completed |
    +--------------------------------------+--------------------+-----------+
    | c906ff08-60e6-44e6-8f49-ed56a0853e85 | Do amazing things! |         0 |
    | 2912a79e-8486-4bc3-a4c5-460793a575ab | Be awesome!        |         0 |
    +--------------------------------------+--------------------+-----------+
    ```

    Évidemment, votre table aura une apparence différente, car elle contient vos éléments. Toutefois, vous devez les y stocker !

Si vous examinez rapidement l’extension de la station d’accueil, vous verrez que deux conteneurs d’applications sont en cours d’exécution. Toutefois, il n’y a pas d’indication réelle qu’elles sont regroupées dans une seule application. Vous verrez comment faire plus rapidement !

![Extension de l’ancrage qui montre deux conteneurs d’applications non groupés](media/vs-multi-container-app.png)

## <a name="recap"></a>Récapitulatif

À ce stade, vous disposez d’une application qui stocke ses données dans une base de données externe qui s’exécute dans un conteneur distinct. Vous avez appris quelques instants sur la mise en réseau des conteneurs et vu comment la découverte de service peut être effectuée à l’aide de DNS.

Toutefois, il y a de bonnes chances que vous commençons par tout ce que vous devez faire pour démarrer cette application. Vous devez créer un réseau, démarrer des conteneurs, spécifier toutes les variables d’environnement, exposer des ports et bien plus encore. C’est beaucoup à retenir et c’est certainement ce qui complique le passage à quelqu’un d’autre.

Dans la section suivante, nous aborderons Docker Compose. Avec Docker Compose, vous pouvez partager vos piles d’applications de manière beaucoup plus simple et permettre aux autres de les faire tourner avec une seule commande (et simple) !

## <a name="next-steps"></a>Étapes suivantes

Poursuivez avec le didacticiel.

> [!div class="nextstepaction"]
> [Utilisation de Docker Compose](use-docker-compose.md)
