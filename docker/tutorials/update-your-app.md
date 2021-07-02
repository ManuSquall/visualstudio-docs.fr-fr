---
title: 'Didacticiel de l’ancrage-partie 2 : mettre à jour votre application'
description: Décrit comment mettre à jour une application Dockr.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 43034ff2e65564cc8af2710b796b76996f21f4c8
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222771"
---
# <a name="update-the-app"></a>Mettre à jour l’application

En guise de petite demande de fonctionnalité, l’équipe produit vous demande de modifier le « texte vide » lorsque vous n’avez pas d’éléments de liste TODO. Elle souhaite la faire passer à ce qui suit :

> Vous n’avez pas encore d’éléments TODO ! Ajoutez-en un ci-dessus.

C’est assez simple, n’est-ce pas ? Nous allons apporter la modification.

## <a name="update-the-source-code"></a>Mettre à jour le code source

1. Dans le `src/static/js/app.js` fichier, mettez à jour la ligne 56 pour utiliser le nouveau texte vide.

    ```diff
    -                <p className="text-center">No items yet! Add one above!</p>
    +                <p className="text-center">You have no todo items yet! Add one above!</p>
    ```

1. Générez la version mise à jour de l’image à l’aide de la même commande que celle que vous avez utilisée auparavant.

    ```bash
    docker build -t getting-started .
    ```

1. Démarrez un nouveau conteneur à l’aide du code mis à jour.

    ```bash
    docker run -dp 3000:3000 getting-started
    ```

**Tiens donc !** Vous avez probablement vu une erreur semblable à celle-ci (les ID seront différents) :

```bash
docker: Error response from daemon: driver failed programming external connectivity on endpoint laughing_burnell 
(bb242b2ca4d67eba76e79474fb36bb5125708ebdabd7f45c8eaf16caaabde9dd): Bind for 0.0.0.0:3000 failed: port is already allocated.
```

Que s’est-il passé ? Le nouveau conteneur n’a pas pu démarrer, car votre ancien conteneur est toujours en cours d’exécution. Le problème est dû au fait que ce conteneur utilise le port 3000 de l’ordinateur hôte et qu’un seul processus sur l’ordinateur (les conteneurs inclus) peut écouter un port spécifique. Pour résoudre ce problème, supprimez l’ancien conteneur.

## <a name="replace-the-old-container"></a>Remplacer l’ancien conteneur

Pour supprimer un conteneur, vous devez d’abord l’arrêter. Une fois qu’elle est arrêtée, elle peut être supprimée. Vous pouvez supprimer l’ancien conteneur de deux manières. N’hésitez pas à choisir le chemin avec lequel vous êtes le plus à l’aise.

### <a name="remove-a-container-using-the-cli"></a>Supprimer un conteneur à l’aide de l’interface CLI

1. Récupérez l’ID du conteneur à l’aide de la `docker ps` commande.

    ```bash
    docker ps
    ```

1. Utilisez la `docker stop` commande pour arrêter le conteneur.

    ```bash
    # Swap out <the-container-id> with the ID from docker ps
    docker stop <the-container-id>
    ```

1. Une fois le conteneur arrêté, vous pouvez le supprimer à l’aide de la `docker rm` commande.

    ```bash
    docker rm <the-container-id>
    ```

> [!TIP]
> Vous pouvez arrêter et supprimer un conteneur dans une seule commande en ajoutant l’indicateur « force » à la `docker rm` commande. Par exemple : `docker rm -f <the-container-id>`

### <a name="remove-a-container-using-the-docker-view"></a>Supprimer un conteneur à l’aide de la vue Dockr

si vous ouvrez l’Extension VS Code, vous pouvez supprimer un conteneur en deux clics. Il est certainement beaucoup plus facile d’avoir à Rechercher l’ID de conteneur et à le supprimer.

1. Une fois l’extension ouverte, accédez au conteneur et cliquez avec le bouton droit.

1. Cliquez sur l’option **supprimer** .

1. Confirmez la suppression et vous avez terminé !

![Vue de l’ancreur-suppression d’un conteneur](media/vs-removing-container.png)

### <a name="start-the-updated-app-container"></a>Démarrer le conteneur d’application mis à jour

1. À présent, démarrez votre application mise à jour.

    ```bash
    docker run -dp 3000:3000 getting-started
    ```

1. Actualisez votre navigateur [http://localhost:3000](http://localhost:3000) . vous devriez voir votre texte d’aide mis à jour.

![Application mise à jour avec texte vide mis à jour](media/todo-list-updated-empty-text.png)

## <a name="recap"></a>Récapitulatif

Si vous avez pu créer une mise à jour, vous avez peut-être remarqué deux choses :

- Tous les éléments existants de votre liste TODO ont disparu ! Ce n’est pas une très bonne application ! Nous y reviendrons dans un instant.
- De *nombreuses* étapes étaient nécessaires pour une telle modification. Dans une section à venir, vous apprendrez à afficher les mises à jour du code sans avoir à recréer et à démarrer un nouveau conteneur chaque fois que vous apportez une modification.

Avant d’en savoir plus sur la persistance, vous verrez rapidement comment partager ces images avec d’autres personnes.

## <a name="next-steps"></a>Étapes suivantes

Poursuivez avec le didacticiel.

> [!div class="nextstepaction"]
> [Partage de votre application](share-your-app.md)
