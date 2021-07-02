---
title: 'Didacticiel : prise en main des & de l’arrimeur Visual Studio Code'
description: Didacticiel en plusieurs étapes qui aborde les principes de base de l’utilisation de l’arrimeur avec Visual Studio Code.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.topic: tutorial
ms.workload:
- azure
next_page: app.md
ms.openlocfilehash: 75a51f478e4e58700f6025dd6a87fcc38439ed87
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222654"
---
# <a name="tutorial-get-started-with-docker"></a>Tutoriel : Prise en main de Docker

Dans ce didacticiel, vous apprendrez à créer et à déployer des applications Dockr, y compris l’utilisation de plusieurs conteneurs avec une base de données, et l’utilisation de Docker Compose. Vous allez également déployer votre application en conteneur dans Azure.

## <a name="start-the-tutorial"></a>Commencer le tutoriel

Si vous avez déjà exécuté la commande pour commencer à utiliser le didacticiel, félicitations !  Si ce n’est pas le cas, ouvrez une invite de commandes ou une fenêtre bash, puis exécutez la commande suivante :

```cli
docker run -d -p 80:80 docker/getting-started
```

Vous remarquerez que quelques indicateurs sont utilisés. Voici quelques informations supplémentaires :

- `-d` -exécuter le conteneur en mode détaché (en arrière-plan)
- `-p 80:80` -mapper le port 80 de l’ordinateur hôte au port 80 dans le conteneur
- `docker/getting-started` -l’image à utiliser

> [!TIP]
> Vous pouvez combiner des indicateurs à un seul caractère pour raccourcir la commande complète.
> Par exemple, la commande ci-dessus peut être écrite comme suit :
>
> ```cli
> docker run -dp 80:80 docker/getting-started
> ```

## <a name="the-vs-code-extension"></a>Extension VS Code

avant d’aller plus loin, nous voulons mettre en surbrillance l’Extension de VS Code d’ancrage, qui vous donne un aperçu rapide des conteneurs en cours d’exécution sur votre machine. Il vous offre un accès rapide aux journaux de conteneur, vous permet d’obtenir un shell à l’intérieur du conteneur et vous permet de gérer facilement le cycle de vie des conteneurs (arrêter, supprimer, etc.).

Pour accéder à l’extension, suivez les instructions [ici](https://code.visualstudio.com/docs/containers/overview). Utilisez l’icône d’ancrage à gauche pour ouvrir la vue de l’ancrage. Si vous ouvrez l’extension maintenant, vous verrez ce didacticiel s’exécuter ! Le nom du conteneur ( `angry_taussig` ci-dessous) est un nom créé de manière aléatoire. Par conséquent, vous aurez probablement un nom différent.

![Conteneur du didacticiel s’exécutant dans l’extension de l’arrimeur](media/vs-tutorial-in-extension.png)

## <a name="what-is-a-container"></a>Qu’est-ce qu’un conteneur ?

Maintenant que vous avez exécuté un conteneur, qu' *est* -ce qu’un conteneur ? En d’autres termes, un conteneur est simplement un autre processus sur votre ordinateur qui a été isolé de tous les autres processus sur l’ordinateur hôte. Cette isolation s’appuie sur les [espaces de noms de noyau et les groupes](https://medium.com/@saschagrunert/demystifying-containers-part-i-kernel-space-2c53d6979504), fonctionnalités qui ont été dans Linux depuis longtemps. La station d’accueil a travaillé pour rendre ces fonctionnalités plus faciles à utiliser.

> [!NOTE]
> **Création de conteneurs à partir de zéro** Si vous souhaitez voir comment les conteneurs sont créés à partir de zéro, le riz Liz de la sécurité Aqua a une vidéo dans laquelle il crée un conteneur à partir de zéro dans Go :
>
> [!VIDEO https://www.youtube-nocookie.com/embed/8fi7uSYlOdc]

## <a name="what-is-a-container-image"></a>Qu’est-ce qu’une image conteneur

Lors de l’exécution d’un conteneur, il utilise un système de fichiers isolé. Ce système de fichiers personnalisé est fourni par une **image de conteneur**. Dans la mesure où l’image contient le système de fichiers du conteneur, elle doit contenir tout ce qui est nécessaire pour exécuter une application (toutes les dépendances, configuration, scripts, binaires, etc.). L’image contient également d’autres configurations pour le conteneur, telles que des variables d’environnement, une commande par défaut à exécuter et d’autres métadonnées.

Nous étudierons plus en détail les images plus tard, en couvrant des sujets tels que la superposition, les meilleures pratiques et bien plus encore.

> [!NOTE]
> Si vous êtes familiarisé avec `chroot` , imaginez un conteneur comme une version étendue de `chroot` . Le système de fichiers provient simplement de l’image. Toutefois, un conteneur ajoute un isolement supplémentaire non disponible lorsque vous utilisez simplement mécanisme chroot.

## <a name="next-steps"></a>Étapes suivantes

Poursuivez avec le didacticiel.

> [!div class="nextstepaction"]
> [L’application](your-application.md)
