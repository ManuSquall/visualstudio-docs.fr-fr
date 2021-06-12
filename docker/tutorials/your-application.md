---
title: 'Didacticiel de l’ancrage-partie 1 : générer et exécuter l’exemple d’application de liste TODO'
description: Vue d’ensemble de l’exemple d’application de liste de tâches qui s’exécute dans Node.js.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 00eb3a7cff3ffeaac783b929a000d9258fae7e63
ms.sourcegitcommit: 4b2b6068846425f6964c1fd867370863fc4993ce
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2021
ms.locfileid: "112042940"
---
# <a name="build-and-run-the-todo-sample-app"></a>Générer et exécuter l’exemple d’application TODO

Pour le reste de ce didacticiel, vous utiliserez un gestionnaire de liste de tâches simple qui s’exécute dans Node.js. Si vous n’êtes pas familiarisé avec Node.js, ne vous inquiétez pas ! Aucune expérience JavaScript réelle n’est nécessaire.

À ce stade, votre équipe de développement est relativement petite et vous créez simplement une application pour prouver votre MVP (produit minimum viable). Vous souhaitez montrer son fonctionnement et ce qu’il peut faire sans avoir à réfléchir à son fonctionnement pour une équipe de grande taille, plusieurs développeurs, etc.

![Capture d’écran du gestionnaire de liste de tâches](media/todo-list-sample.png)

## <a name="get-the-app"></a>Obtenir l’application

Avant de pouvoir exécuter l’application, vous devez récupérer le code source de l’application sur votre ordinateur. Pour les projets réels, vous allez généralement cloner le référentiel. Toutefois, pour ce didacticiel, nous avons créé un fichier ZIP contenant l’application.

1. Assurez-vous que Docker pour Windows ou l’édition Community de l’Ancrable est installé sur l’ordinateur local. Consultez [docker pour Windows documentation sur l’installation](https://docs.docker.com/docker-for-windows/install/). Le processus d’installation rend le fichier ZIP contenant l’exemple disponible à l’adresse localhost.

1. Téléchargez la source de l’application à partir du référentiel d' [ancrage](https://github.com/docker/getting-started) . Vous pouvez télécharger le fichier ZIP pour référentiel. Pour télécharger le fichier ZIP, utilisez le bouton de **code** vert et choisissez **Télécharger zip**. Ouvrez le fichier ZIP et extrayez tout pour extraire la source de l’application à partir du dossier de l' *application* vers un dossier sur votre disque dur.

   ![Capture d’écran montrant le bouton de code vert et l’option Télécharger ZIP](media/download-zip.png)

1. Une fois l’extraction effectuée, utilisez votre éditeur de code favori pour ouvrir le projet. Si vous avez besoin d’un éditeur, vous pouvez utiliser [Visual Studio code](https://code.visualstudio.com/). Vous devez voir le `package.json` et les deux sous-répertoires ( `src` et `spec` ).

    ![Capture d’écran de Visual Studio Code ouverts avec l’application chargée](media/ide-screenshot.png)

## <a name="building-the-apps-container-image"></a>Génération de l’image conteneur de l’application

Pour générer l’application, vous devez utiliser un `Dockerfile` . Un fichier dockerfile est simplement un script textuel d’instructions qui est utilisé pour créer une image de conteneur. Si vous avez créé fichiers dockerfile avant, vous pouvez voir quelques défauts dans le fichier dockerfile ci-dessous. Mais ne vous inquiétez pas ! Nous allons les passer en revue.

1. Créez un fichier nommé `Dockerfile` dans le même dossier que le fichier `package.json` avec le contenu suivant.

    ```dockerfile
    FROM node:12-alpine
    WORKDIR /app
    COPY . .
    RUN yarn install --production
    CMD ["node", "/app/src/index.js"]
    ```

    Vérifiez que le fichier n' `Dockerfile` a pas d’extension de fichier comme `.txt` . Certains éditeurs peuvent ajouter cette extension de fichier automatiquement, ce qui génère une erreur à l’étape suivante.

1. Si vous ne l’avez pas déjà fait, ouvrez un terminal et accédez au `app` répertoire à l’aide de la `Dockerfile` . À présent, générez l’image conteneur à l’aide de la `docker build` commande.

    ```bash
    docker build -t getting-started .
    ```

    Vous pouvez également cliquer avec le bouton droit sur fichier dockerfile et choisir générer une **image...** , puis spécifier la balise à l’invite.

    Cette commande utilisait le fichier dockerfile pour générer une nouvelle image de conteneur. Vous avez peut-être remarqué qu’un grand nombre de « couches » ont été téléchargées. Cela est dû au fait que vous avez demandé au générateur que vous vouliez démarrer à partir de l' `node:12-alpine` image. Toutefois, étant donné que vous ne l’avez pas sur votre ordinateur, cette image devait être téléchargée.

    Une fois l’image téléchargée, vous l’avez copiée dans votre application et vous l’avez utilisée `yarn` pour installer les dépendances de votre application. La `CMD` directive spécifie la commande par défaut à exécuter lors du démarrage d’un conteneur à partir de cette image.

    Enfin, l' `-t` indicateur balise votre image. Imaginez simplement comme un nom explicite pour l’image finale. Étant donné que vous avez nommé l’image `getting-started` , vous pouvez faire référence à cette image quand vous exécutez un conteneur.

    Le `.` à la fin de la `docker build` commande indique à l’ancrage qu’il doit rechercher le `Dockerfile` dans le répertoire actif.

## <a name="starting-an-app-container"></a>Démarrage d’un conteneur d’application

Maintenant que vous avez une image, exécutez l’application ! Pour ce faire, utilisez la `docker run` commande (Rappelez-vous qu’à partir d’une version antérieure ?).

1. Démarrez votre conteneur à l’aide de la `docker run` commande et spécifiez le nom de l’image que vous venez de créer :

    ```bash
    docker run -dp 3000:3000 getting-started
    ```

    Vous vous souvenez des `-d` `-p` indicateurs et ? Vous exécutez le nouveau conteneur en mode « détaché » (en arrière-plan) et en créant un mappage entre le port 3000 de l’ordinateur hôte et le port 3000 du conteneur. Sans le mappage de port, vous ne seriez pas en mesure d’accéder à l’application.

1. Après quelques secondes, ouvrez votre navigateur Web sur [http://localhost:3000](http://localhost:3000) .
    Vous devez voir l’application !

    ![Liste TODO vide](media/todo-list-empty.png)

1. Continuez et ajoutez un ou deux éléments et voyez qu’ils fonctionnent comme prévu. Vous pouvez marquer les éléments comme étant terminés et supprimer des éléments. Votre serveur frontal stocke correctement les éléments dans le backend. Assez rapide et facile, n’est-ce pas ?

À ce stade, vous devez avoir un gestionnaire de liste de tâches en cours d’exécution avec quelques éléments que vous avez créés par vous-même ! À présent, nous allons apporter quelques modifications et apprendre à gérer vos conteneurs.

Si vous examinez rapidement l’extension VS Code, vous devriez voir vos deux conteneurs s’exécuter maintenant (ce didacticiel et votre nouveau conteneur d’application lancé) !

![Extension d’ancrage avec didacticiel et conteneurs d’applications exécutant](media/vs-two-containers.png)

## <a name="recap"></a>Récapitulatif

Dans cette petite section, vous avez appris les principes fondamentaux de la création d’une image de conteneur et de la création d’un fichier dockerfile pour le faire. Une fois que vous avez créé une image, vous avez démarré le conteneur et vu l’application en cours d’exécution !

Ensuite, vous allez apporter une modification à l’application et apprendre à mettre à jour l’application en cours d’exécution avec une nouvelle image. En cours de route, vous apprendrez quelques autres commandes utiles.

## <a name="next-steps"></a>Étapes suivantes

Poursuivez avec le didacticiel.

> [!div class="nextstepaction"]
> [Mise à jour de votre application](update-your-app.md)
