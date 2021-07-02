---
title: 'Didacticiel de l’ancrage-partie 4 : conserver vos données'
description: Découvrez comment rendre des données persistantes dans une base de données et comment partager des répertoires dans un conteneur en montant un volume.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: c9408e099caaef097be3fc4eea26cee2b1889e8e
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222901"
---
# <a name="persist-your-data"></a> Rendre vos données persistantes

Si vous n’avez pas remarqué, la liste TODO est nettoyée chaque fois que vous lancez le conteneur. Pourquoi ? Penchons-nous sur la façon dont le conteneur fonctionne.

## <a name="the-containers-filesystem"></a>Système de fichiers du conteneur

Lorsqu’un conteneur s’exécute, il utilise les différentes couches d’une image pour son système de fichiers. Chaque conteneur obtient également son propre « espace de travail » pour créer, mettre à jour ou supprimer des fichiers. Les modifications ne seront pas visibles dans un autre conteneur, *même s'* ils utilisent la même image.

### <a name="see-this-in-practice"></a>Voir cela dans la pratique

Pour voir cela en action, vous allez démarrer deux conteneurs et créer un fichier dans chacun d’eux. Ce que vous verrez, c’est que les fichiers créés dans un conteneur ne sont pas disponibles dans un autre.

1. Démarrez un `ubuntu` conteneur qui créera un fichier nommé `/data.txt` avec un nombre aléatoire compris entre 1 et 10000.

    ```bash
    docker run -d ubuntu bash -c "shuf -i 1-10000 -n 1 -o /data.txt && tail -f /dev/null"
    ```

    Si vous êtes curieux de connaître la commande, vous démarrez un interpréteur de commandes bash et appelez deux commandes (pourquoi il a le `&&` ). La première partie sélectionne un nombre aléatoire unique et l’écrit dans `/data.txt` . La deuxième commande surveille simplement un fichier pour que le conteneur reste en cours d’exécution.

1. Valider vous pouvez voir la sortie à l’aide `exec` de pour accéder au conteneur. pour ce faire, ouvrez l’extension de VS Code et cliquez sur l’option **attacher l’interpréteur** de commandes. cela permet `exec` d’ouvrir un interpréteur de commandes dans le conteneur au sein du terminal VS Code.

    ![VS Code ouvrir l’interface CLI dans le conteneur ubuntu](media/attach_shell.png)

    Vous verrez un terminal qui exécute un shell dans le conteneur Ubuntu. Exécutez la commande suivante pour afficher le contenu du `/data.txt` fichier. Fermez ce terminal ultérieurement.

    ```bash
    cat /data.txt
    ```

    Si vous préférez la ligne de commande, vous pouvez utiliser la `docker exec` commande pour faire de même. Vous devez récupérer l’ID du conteneur (utilisez `docker ps` pour l’extraire) et récupérer le contenu à l’aide de la commande suivante.

    ```bash
    docker exec <container-id> cat /data.txt
    ```

    Vous devez voir un nombre aléatoire !

1. À présent, démarrez un autre `ubuntu` conteneur (la même image) et vous verrez que vous n’avez pas le même fichier.

    ```bash
    docker run -it ubuntu ls /
    ```

    Et regardez ! Il n’y a aucun `data.txt` fichier là ! C’est parce qu’il a été écrit dans l’espace de travail uniquement pour le premier conteneur.

1. Continuez et supprimez le premier conteneur à l’aide de la `docker rm -f` commande.

## <a name="container-volumes"></a>Volumes de conteneur

Avec l’expérience précédente, vous avez vu que chaque conteneur démarre à partir de la définition d’image chaque fois qu’il démarre. Alors que les conteneurs peuvent créer, mettre à jour et supprimer des fichiers, ces modifications sont perdues lorsque le conteneur est supprimé et que toutes les modifications sont isolées dans ce conteneur. Avec les volumes, vous pouvez modifier tout cela.

Les [volumes](https://docs.docker.com/storage/volumes/) permettent de reconnecter des chemins de système de fichiers spécifiques du conteneur à l’ordinateur hôte. Si un répertoire du conteneur est monté, les modifications apportées à ce répertoire sont également visibles sur l’ordinateur hôte. Si vous montez ce même répertoire à travers les redémarrages de conteneur, vous verrez les mêmes fichiers.

Il existe deux principaux types de volumes. vous pouvez utiliser les deux à la fois, mais vous commencerez par des **volumes nommés**.

## <a name="persist-your-todo-data"></a>Conserver vos données TODO

Par défaut, l’application todo stocke ses données dans une [base de données SQLite](https://www.sqlite.org/index.html) à l’adresse `/etc/todos/todo.db` . Si vous n’êtes pas familiarisé avec SQLite, pas de soucis ! Il s’agit simplement d’une base de données relationnelle dans laquelle toutes les données sont stockées dans un seul fichier. Bien qu’il ne s’agit pas de la meilleure solution pour les applications à grande échelle, cela fonctionne pour les petites démonstrations. Nous allons nous pencher sur l’activation ultérieure du moteur de base de données.

Si la base de données est un fichier unique, si vous pouvez conserver ce fichier sur l’ordinateur hôte et le rendre accessible au conteneur suivant, il doit pouvoir reprendre là où le dernier s’est arrêté. En créant un volume et en attachant (souvent appelé « montage ») à l’annuaire dans lequel les données sont stockées, vous pouvez conserver les données. À mesure que le conteneur écrit dans le `todo.db` fichier, il est conservé sur l’hôte du volume.

Comme nous l’avons vu, vous allez utiliser un **volume nommé**. Imaginez un volume nommé comme un simple compartiment de données. L’arrimeur conserve l’emplacement physique sur le disque et il vous suffit de mémoriser le nom du volume. Chaque fois que vous utilisez le volume, l’arrimeur s’assure que les données correctes sont fournies.

1. Créez un volume à l’aide de la `docker volume create` commande.

    ```bash
    docker volume create todo-db
    ```

1. Arrêtez le conteneur d’application todo une fois de plus dans la vue d’ancrage (ou avec `docker rm -f <id>` ), car il est toujours en cours d’exécution sans utiliser le volume persistant.

1. Démarrez le conteneur d’application TODO, mais ajoutez l' `-v` indicateur pour spécifier un montage de volume. vous allez utiliser le volume nommé et le monter sur `/etc/todos` , ce qui capture tous les fichiers créés dans le chemin d’accès.

    ```bash
    docker run -dp 3000:3000 -v todo-db:/etc/todos getting-started
    ```

1. Une fois le conteneur démarré, ouvrez l’application et ajoutez quelques éléments à votre liste TODO.

    ![Éléments ajoutés à la liste de tâches](media/items-added.png)

1. Supprimez le conteneur de l’application todo. Utilisez la vue d’ancrage ou `docker ps` pour obtenir l’ID, puis `docker rm -f <id>` pour le supprimer.

1. Démarrez un nouveau conteneur à l’aide de la même commande que ci-dessus.

1. Ouvrez l’application. Vos éléments doivent toujours apparaître dans votre liste.

1. Continuez et supprimez le conteneur lorsque vous avez terminé l’extraction de votre liste.

Hourra! Vous savez maintenant comment conserver les données !

> [!TIP]
> Bien que les volumes nommés et les montages de liaison (dont nous allons parler dans une minute) soient les deux principaux types de volumes pris en charge par l’installation par défaut du moteur d’ancrage, de nombreux plug-ins de pilote de volume sont disponibles pour prendre en charge NFS, SFTP, NetApp et bien plus encore. Cela est particulièrement important lorsque vous commencez à exécuter des conteneurs sur plusieurs hôtes dans un environnement en cluster avec essaim, Kubernetes, etc.

## <a name="dive-into-your-volume"></a>Plongez dans votre volume

Beaucoup de gens demandent souvent « où est-ce que l’arrimeur *stocke* mes données lorsque j’utilise un volume nommé ? » Si vous souhaitez en savoir plus, vous pouvez utiliser la `docker volume inspect` commande.

```bash
docker volume inspect todo-db
[
    {
        "CreatedAt": "2019-09-26T02:18:36Z",
        "Driver": "local",
        "Labels": {},
        "Mountpoint": "/var/lib/docker/volumes/todo-db/_data",
        "Name": "todo-db",
        "Options": {},
        "Scope": "local"
    }
]
```

`Mountpoint`Est l’emplacement réel sur le disque où sont stockées les données. Notez que sur la plupart des ordinateurs, vous devez disposer d’un accès racine pour accéder à ce répertoire à partir de l’hôte. C’est là que c’est là !

> [!NOTE]
> **Accès aux données de volume directement sur le Bureau de l’ordinateur d’amarrage** En cours d’exécution dans le Bureau de l’Ancreur, les commandes de l’arrimeur s’exécutent en réalité dans une petite machine virtuelle sur votre ordinateur. Si vous souhaitez examiner le contenu réel du répertoire de *montage* , vous devez d’abord obtenir l’intérieur de la machine virtuelle. Dans WSL 2, il se trouve à l’intérieur d’un WSL 2 distribution et il est accessible via l’Explorateur de fichiers.

## <a name="recap"></a>Récapitulatif

À ce stade, vous disposez d’une application opérationnelle qui peut survivre aux redémarrages ! Vous pouvez l’afficher à vos investisseurs et espérer qu’ils peuvent attraper votre vision.

Toutefois, vous avez vu précédemment que la reconstruction d’images pour chaque modification prend beaucoup de temps. Le meilleur moyen d’apporter des modifications, est-il possible d’effectuer des modifications ? Avec les montages de liaison (que nous avons indiqués plus haut), il existe une meilleure méthode. Jetons un coup d’œil à ce moment là !

## <a name="next-steps"></a>Étapes suivantes

Poursuivez avec le didacticiel.

> [!div class="nextstepaction"]
> [Utilisation des montages de liaison](use-bind-mounts.md)
