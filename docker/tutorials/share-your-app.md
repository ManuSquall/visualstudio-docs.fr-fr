---
title: 'Didacticiel de l’ancrage-partie 3 : partager votre application'
description: Décrit comment partager des images de l’arrimeur à l’aide du Registre du Hub Dockr.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: d64d10c7abefc14f31c39c3b8397e95cec67e9f4
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222784"
---
# <a name="share-your-app"></a>Partager votre application

Maintenant que nous avons créé une image, nous allons la partager ! Pour partager des images de station d’accueil, vous devez utiliser un registre d’ancrage. Le registre par défaut est le Hub Dockr et c’est là que sont issues toutes les images que nous avons utilisées.

## <a name="create-a-repo"></a>Créer un référentiel

Pour envoyer une image, vous devez d’abord créer un référentiel sur le hub d’ancrage.

1. Accédez au [Hub de l’ancreur](https://hub.docker.com/signup/msftedge?utm_source=msftedge) et connectez-vous si nécessaire.

1. Cliquez sur le bouton **créer un référentiel** .

1. Pour le nom de référentiel, utilisez `getting-started` . Assurez-vous que la visibilité est `Public` .

1. Cliquez sur le bouton **créer** .

Si vous regardez sur le côté droit de la page, vous verrez une section intitulée commandes de l' **ancrage**. Cela donne un exemple de commande que vous devrez exécuter pour effectuer une transmission Push à ce référentiel.

![Commande de l’arrimeur avec l’exemple Push](media/push-command.png)

## <a name="push-the-image"></a>Pousser l’image

1. Dans la ligne de commande, essayez d’exécuter la commande Push que vous voyez sur le hub d’ancrage. Notez que votre commande utilise votre espace de noms, et non « dockr ».

    ```plaintext
    $ docker push docker/getting-started
    The push refers to repository [docker.io/docker/getting-started]
    An image does not exist locally with the tag: docker/getting-started
    ```

    Pourquoi a-t-il échoué ? La commande Push a cherché une image nommée dockr/Getting Started, mais n’en a pas trouvé une. Si vous exécutez `docker image ls` , vous ne verrez pas l’un ni l’autre.

    Pour résoudre ce problème, vous devez « baliser » votre image existante que nous avons créée pour lui attribuer un autre nom.

1. Connectez-vous au hub de l’Ancreur à l’aide de la commande `docker login -u <username>` .

1. Utilisez la `docker tag` commande pour attribuer `getting-started` un nouveau nom à l’image. Veillez à effectuer une permutation `<username>` avec votre ID d’ancrage.

    ```bash
    docker tag getting-started <username>/getting-started
    ```

1. Essayez à présent d’exécuter à nouveau votre commande Push. Si vous copiez la valeur à partir du Hub de l’Ancreur, vous pouvez supprimer la `tagname` partie, car vous n’avez pas ajouté de balise au nom de l’image. Si vous ne spécifiez pas de balise, l’ancrage utilise une balise appelée `latest` .

    ```bash
    docker push <username>/getting-started
    ```

    au lieu de la ligne de commande, vous pouvez également cliquer avec le bouton droit sur la balise image dans la section **Images** de la vue dockr, puis choisir **envoyer...**, puis choisir **Connecter registre...** , puis **ancrer Hub**.

## <a name="run-the-image-on-a-new-instance"></a>Exécuter l’image sur une nouvelle instance

Maintenant que votre image a été générée et envoyée dans un registre, essayez d’exécuter l’application sur une toute nouvelle instance qui n’a jamais vu cette image de conteneur ! Pour ce faire, vous allez utiliser la fonction lire avec l’ancrage.

1. Ouvrez votre navigateur pour [jouer avec l’ancrage](http://play-with-docker.com).

1. Connectez-vous avec votre compte d’ancrage Hub.

1. Une fois que vous êtes connecté, cliquez sur le lien « + ajouter une nouvelle INSTANCE » dans la barre latérale gauche. (Si vous ne le voyez pas, rendez votre navigateur un peu plus grand.) Après quelques secondes, une fenêtre de terminal s’ouvre dans votre navigateur.

    ![Lire avec l’arrimeur ajouter une nouvelle instance](media/pwd-add-new-instance.png)

1. Dans le terminal, démarrez votre application récemment envoyée.

    ```bash
    docker run -dp 3000:3000 <username>/getting-started
    ```

    Vous devriez voir que l’image est extraite et finalement démarrer !

1. Cliquez sur le badge 3000 lorsqu’il apparaît et vous devriez voir l’application avec vos modifications. Hourra! Si le badge 3000 ne s’affiche pas, vous pouvez cliquer sur le bouton **ouvrir le port** et taper 3000.

## <a name="recap"></a>Récapitulatif

Dans cette section, vous avez appris à partager des images en les envoyant à un registre. Vous êtes ensuite allé à une toute nouvelle instance et avez pu exécuter l’image qui a fait l’objet d’un push. Cela est assez courant dans les pipelines CI, où le pipeline crée l’image et l’envoie à un registre, puis l’environnement de production peut utiliser la version la plus récente de l’image.

Maintenant que vous avez compris, rappelez-vous qu’à la fin de la dernière section, lorsque vous avez redémarré l’application, vous avez perdu tous vos éléments de liste TODO. Ce n’est évidemment pas une excellente expérience utilisateur. vous allez apprendre ensuite comment rendre les données persistantes entre les redémarrages.

## <a name="next-steps"></a>Étapes suivantes

Poursuivez avec le didacticiel.

> [!div class="nextstepaction"]
> [Conservation de votre base de données](persist-your-data.md)
