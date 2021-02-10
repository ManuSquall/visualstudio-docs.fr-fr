---
title: 'Démarrage rapide : créer votre première application Vue.js'
description: Dans ce guide de démarrage rapide, vous allez créer une application Vue.js dans Visual Studio à l’aide des outils Node.js pour Visual Studio.
ms.custom: ''
ms.date: 10/31/2019
ms.topic: quickstart
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: ee855700502469783a8eab60bb24a28c2e30a9c8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950638"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-vuejs-app"></a>Démarrage rapide : utiliser Visual Studio pour créer votre première application Vue.js

Dans cette présentation de 5-10 minutes de l’environnement de développement intégré (IDE) de Visual Studio, vous allez créer et exécuter une application web Vue.js simple.

> [!IMPORTANT]
> Le modèle Vue.js, disponible à partir de Visual Studio 2017 version 15.8, est nécessaire pour cet article.

## <a name="prerequisites"></a>Prérequis

* Au préalable, vous devez avoir installé Visual Studio et la charge de travail de développement Node.js.

    ::: moniker range=">=vs-2019"
    Si vous n’avez pas encore installé Visual Studio 2019, accédez à la page [téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/) pour l’installer gratuitement.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Si vous n’avez pas encore installé Visual Studio 2017, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/) pour l’installer gratuitement.
    ::: moniker-end

    Si vous devez installer la charge de travail mais que vous disposez déjà de Visual Studio, accédez à **Outils**  >  **obtenir des outils et des fonctionnalités...**, qui ouvre le Visual Studio installer. Choisissez la charge de travail **Développement Node.js**, puis choisissez **Modifier**.

    ![Charge de travail Node.js dans Visual Studio Installer](../ide/media/quickstart-nodejs-workload.png)

* Le runtime Node.js doit être installé.

    Si vous ne l’avez pas installé, nous vous recommandons d’installer la version LTS à partir du site Web [Node.js](https://nodejs.org/en/download/) pour une meilleure compatibilité avec les frameworks et les bibliothèques externes. Node.js est conçu pour les architectures 32 bits et 64 bits. Les outils de Node.js dans Visual Studio, inclus dans la charge de travail Node.js, prennent en charge les deux versions. Une seule est requise et le programme d’installation de Node.js ne prend en charge qu’une seule installation à la fois.
    
    En règle générale, Visual Studio détecte automatiquement le runtime Node.js installé. S’il ne détecte pas un Runtime installé, vous pouvez configurer votre projet pour référencer le Runtime installé dans la page Propriétés (après avoir créé un projet, cliquer avec le bouton droit sur le nœud du projet, choisir **Propriétés** et définir le **chemin d’accèsNode.exe**). Vous pouvez utiliser une installation globale de Node.js ou vous pouvez spécifier le chemin d’accès à un interpréteur local dans chacun de vos projets Node.js. 

## <a name="create-a-project"></a>Créer un projet

Vous allez d’abord créer un projet d’application web Vue.js.

1. Si le runtime Node.js n’est pas déjà installé, installez la version LTS à partir du site web [Node.js](https://nodejs.org/en/download/).

    Pour plus d’informations, voir les Conditions préalables.

1. Ouvrez Visual Studio.

1. Créez un projet.

    ::: moniker range=">=vs-2019"
    Appuyez sur **Échap** pour fermer la fenêtre de démarrage. Tapez **Ctrl+Q** pour ouvrir la zone de recherche, tapez **Basic Vue.js**, puis choisissez **Application web Vue.js de base** (JavaScript ou TypeScript). Dans la boîte de dialogue qui s’affiche, tapez le nom **basic-vuejs**, puis choisissez **Créer**.

    ![Modèle Vue.js](../javascript/media/vs-2019/vuejs-template.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    Dans la barre de menus supérieure, choisissez **fichier**  >  **nouveau**  >  **projet**. Dans le volet gauche de la boîte de dialogue **Nouveau projet**, développez **JavaScript** ou **TypeScript**, puis choisissez **Node.js**. Dans le volet central, choisissez **Application web Vue.js de base**, tapez le nom **basic-vuejs**, puis choisissez **OK**.

    ![Modèle Vue.js](../javascript/media/vuejs-template.png)
    ::: moniker-end
    Si vous ne voyez pas le modèle de projet **Application web Vue.js de base**, vous devez ajouter la charge de travail **Développement Node.js**. Pour obtenir des instructions détaillées, consultez les [Prérequis](#prerequisites).

    Visual Studio crée le nouveau projet. Le nouveau projet s’ouvre dans l’Explorateur de solutions (volet droit).

1. Vérifiez la progression de l’installation des packages npm nécessaires pour l’application dans la fenêtre Sortie (volet inférieur).

1. Dans l’Explorateur de solutions, ouvrez le nœud **npm** et vérifiez que tous les packages npm répertoriés sont installés.

    S’il manque des packages (icône de point d’exclamation), vous pouvez cliquer avec le bouton droit sur le nœud **npm** et choisir **Installer les packages npm manquants**.

## <a name="explore-the-ide"></a>Explorer l’IDE

1. Observez **l’Explorateur de solutions** dans le volet droit.

     ![Solution Vue.js](../javascript/media/vuejs-solution.png)

   - Votre projet mis en gras, avec le nom que vous avez donné dans la boîte de dialogue **Nouveau projet**. Sur le disque, ce projet est représenté par un. fichier *njsproj* dans votre dossier de projet.

   - Au niveau le plus élevé figure une solution, qui a par défaut le même nom que votre projet. Solution, représentée par un. *sln* sur le disque, est un conteneur pour un ou plusieurs projets connexes.

   - Le nœud **NPM** affiche tous les packages NPM installés. Vous pouvez cliquer avec le bouton droit sur le nœud npm pour rechercher et installer des packages npm à l’aide d’une boîte de dialogue.

2. Si vous souhaitez installer des packages npm ou exécuter des commandes Node.js à partir d’une invite de commandes, cliquez avec le bouton droit sur le nœud du projet et choisissez **Ouvrir l’invite de commandes ici**.

## <a name="add-a-vue-file-to-the-project"></a>Ajouter un fichier .vue au projet

1. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur n’importe quel dossier, par exemple le dossier *src/components*, puis choisissez **Ajouter** > **Nouvel élément**.

1. Sélectionnez **Composant monofichier Vue JavaScript** ou **Composant monofichier Vue TypeScript**, puis cliquez sur **Ajouter**.

    Visual Studio ajoute le nouveau fichier au projet.

## <a name="build-the-project"></a>Créer le projet

::: moniker range=">=vs-2019"
1. Ensuite, choisissez **Générer** > **Générer la solution** pour générer le projet.

1. Consultez la fenêtre **Sortie** pour afficher les résultats de la génération, puis choisissez **Build** dans la liste **Afficher la sortie à partir de**.
::: moniker-end
::: moniker range="vs-2017"
1. (Projet TypeScript uniquement) À partir de Visual Studio, choisissez **Générer** > **Nettoyer la solution**.

1. Ensuite, choisissez **Générer** > **Générer la solution** pour générer le projet.

1. Consultez la fenêtre **Sortie** pour afficher les résultats de la génération, puis choisissez **Build** dans la liste **Afficher la sortie à partir de**.
::: moniker-end

Le modèle de projet Vue.js JavaScript (et les versions antérieures du modèle de machine à écrire) utilisent le `build` script NPM en configurant un événement de publication. Si vous souhaitez modifier ce paramètre, ouvrez le fichier projet (*\<projectname\> . njsproj*) à partir de l’Explorateur Windows et recherchez la ligne de code suivante :

```xml
<PostBuildEvent>npm run build</PostBuildEvent>
```

## <a name="run-the-application"></a>Exécution de l'application

1. Appuyez sur **CTRL** + **F5** (ou **déboguez > exécuter sans débogage**) pour exécuter l’application.

   Dans la console, un message signalant le *démarrage du serveur de développement* s’affiche.

   Ensuite, l’application s’ouvre dans un navigateur.
   
   Si vous ne voyez pas l’application en cours d’exécution, actualisez la page.

   ![Application Vue.js en cours d’exécution dans le navigateur](../javascript/media/vuejs-running-app.png)

1. Fermez le navigateur web.

Félicitations ! Vous avez terminé ce guide de démarrage rapide. Nous espérons que vous en avez appris un peu plus sur l’utilisation de l’IDE de Visual Studio avec Vue.js. Si vous souhaitez en savoir plus sur ses fonctionnalités, poursuivez avec l’un des tutoriels de la section **Tutoriels** dans la table des matières.

## <a name="next-steps"></a>Étapes suivantes

- Parcourir l’article pour [Vue.js](create-application-with-vuejs.md)
- Suivre le [tutoriel pour Node.js et Express](tutorial-nodejs.md)
- [Déployer l’application sur Linux App Service](../javascript/publish-nodejs-app-azure.md)