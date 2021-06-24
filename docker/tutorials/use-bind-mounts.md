---
title: 'Didacticiel de l’ancrage-partie 5 : utiliser des montages de liaison'
description: Décrit comment utiliser des montages de liaison pour contrôler le point de montage sur l’hôte.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 6a4aa7623f69f9b02f9649a1a66ade010a823669
ms.sourcegitcommit: 98d187abd9352d2255348b84d99d015e65caa0ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2021
ms.locfileid: "112574111"
---
# <a name="use-bind-mounts"></a>Utiliser des montages de liaison

Dans le chapitre précédent, vous avez appris et utilisé un **volume nommé** pour conserver les données dans votre base de données. Les volumes nommés sont très utiles si vous souhaitez simplement stocker des données, car vous n’avez pas à vous soucier de l' *emplacement* de stockage des données.

Avec les **montages de liaison**, vous contrôlez le montage exact sur l’hôte. Vous pouvez l’utiliser pour rendre les données persistantes, mais il est souvent utilisé pour fournir des données supplémentaires dans des conteneurs. Lorsque vous travaillez sur une application, vous pouvez utiliser un montage de liaison pour monter le code source dans le conteneur afin de lui permettre de voir les modifications du code, de répondre et de voir immédiatement les modifications.

Pour les applications basées sur des nœuds, [nodemon](https://npmjs.com/package/nodemon) est un outil formidable pour surveiller les modifications apportées aux fichiers, puis redémarrer l’application. Il existe des outils équivalents dans la plupart des autres langages et infrastructures.

## <a name="quick-volume-type-comparisons"></a>Comparaisons des types de volumes rapides

Les montages de liaison et les volumes nommés sont les deux principaux types de volumes fournis avec le moteur de l’ancrage. Toutefois, des pilotes de volume supplémentaires sont disponibles pour prendre en charge d’autres cas d’utilisation ([SFTP](https://github.com/vieux/docker-volume-sshfs), [CEPH](https://ceph.com/geen-categorie/getting-started-with-the-docker-rbd-volume-plugin/), [NetApp](https://netappdvp.readthedocs.io/en/stable/), [S3](https://github.com/elementar/docker-s3-volume), etc.).

| Propriété | Volumes nommés | Montages liés |
| -------- | ------------- | ----------- |
| Emplacement de l’hôte | L’ancrage choisit | Vous contrôlez |
| Exemple de montage (à l’aide de `-v` ) | My-volume:/usr/local/Data | /path/to/data:/usr/local/data |
| Remplit le nouveau volume avec le contenu du conteneur | Oui | Non |
| Prend en charge les pilotes de volume | Oui | Non |

## <a name="start-a-dev-mode-container"></a>Démarrer un conteneur dev-mode

Pour exécuter votre conteneur pour prendre en charge un flux de travail de développement, procédez comme suit :

- Montez votre code source dans le conteneur
- Installer toutes les dépendances, y compris les dépendances de « développement »
- Démarrer nodémon pour surveiller les modifications de système de fichiers

1. Assurez-vous que vous n’avez aucun `getting-started` conteneur précédent en cours d’exécution.

1. Exécutez la commande suivante (remplacez les ` \ ` caractères par `` ` `` dans Windows PowerShell). Vous allez découvrir ce qui se passe ultérieurement :

    ```bash
    docker run -dp 3000:3000 \
        -w /app \
        -v "%cd%:/app" \
        node:12-alpine \
        sh -c "yarn install && yarn run dev"
    ```

    - `-dp 3000:3000` -identique à avant. Exécuter en mode détaché (arrière-plan) et créer un mappage de port
    - `-w /app` -définit le répertoire de travail ou le répertoire actif à partir duquel la commande s’exécutera
    - `-v "%cd%:/app"` -bind monter le répertoire actif à partir de l’hôte dans le conteneur dans le `/app` Répertoire
    - `node:12-alpine` -l’image à utiliser. Notez qu’il s’agit de l’image de base de votre application à partir de fichier dockerfile
    - `sh -c "yarn install && yarn run dev"` -la commande. Nous démarrons un shell à l’aide `sh` de (Alpine n’a pas `bash` ) et en exécutant `yarn install` pour installer *toutes les* dépendances, puis en cours d’exécution `yarn run dev` . Si vous regardez dans le `package.json` , nous voyons que le script est en cours de `dev` démarrage `nodemon` .

1. Vous pouvez surveiller les journaux à l’aide de `docker logs -f <container-id>` . Vous savez que vous êtes prêt à aller quand vous voyez :

    ```bash
    docker logs -f <container-id>
    $ nodemon src/index.js
    [nodemon] 1.19.2
    [nodemon] to restart at any time, enter `rs`
    [nodemon] watching dir(s): *.*
    [nodemon] starting `node src/index.js`
    Using sqlite database at /etc/todos/todo.db
    Listening on port 3000
    ```

    Lorsque vous avez terminé de surveiller les journaux, quittez en appuyant sur `Ctrl` + `C` .

1. À présent, apportez une modification à l’application. Dans le `src/static/js/app.js` fichier, modifiez le bouton **Ajouter un élément** pour simplement **Ajouter**. Cette modification sera à la ligne 109.

    ```diff
    -                         {submitting ? 'Adding...' : 'Add Item'}
    +                         {submitting ? 'Adding...' : 'Add'}
    ```

1. Actualisez simplement la page (ou ouvrez-la) et vous devriez voir la modification reflétée dans le navigateur presque immédiatement. Le redémarrage du serveur de nœud peut prendre quelques secondes. par conséquent, si vous recevez une erreur, essayez de l’actualiser après quelques secondes.

    ![Capture d’écran de l’étiquette mise à jour pour le bouton Ajouter](media/updated-add-button.png)

1. N’hésitez pas à apporter les autres modifications que vous souhaitez apporter. Lorsque vous avez terminé, arrêtez le conteneur et générez votre nouvelle image à l’aide de `docker build -t getting-started .` .

L’utilisation des montages de liaison est *très* courante pour les configurations de développement local. L’avantage est que l’ordinateur de développement n’a pas besoin d’installer tous les environnements et les outils de génération. Avec une seule `docker run` commande, l’environnement de développement est extrait et prêt à l’emploi. Vous en apprendrez plus sur Docker Compose dans une étape ultérieure, car cela vous aidera à simplifier vos commandes (vous obtenez déjà beaucoup d’indicateurs).

## <a name="recap"></a>Récapitulatif

À ce stade, vous pouvez rendre votre base de données persistante et répondre rapidement aux besoins et aux demandes de vos investisseurs et de vos retrouveurs. Hourra! Mais devinez quoi ? Vous avez reçu des informations exceptionnelles !

**Votre projet a été sélectionné pour un développement futur.**

Pour préparer la production, vous devez migrer votre base de données de l’utilisation de SQLite vers une solution qui peut s’adapter un peu mieux. Pour plus de simplicité, vous allez conserver une base de données relationnelle et basculer votre application pour utiliser MySQL. Mais comment devez-vous exécuter MySQL ? Comment autoriser les conteneurs à communiquer les uns avec les autres ? Vous en apprendrez plus sur ce qui suit !

## <a name="next-steps"></a>Étapes suivantes

Poursuivez avec le didacticiel.

> [!div class="nextstepaction"]
> [Application à plusieurs conteneurs](multi-container-apps.md)