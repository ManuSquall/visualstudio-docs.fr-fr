---
title: Publier une application Node.js sur App Service Linux
description: Vous pouvez publier des applications Node.js créées dans Visual Studio sur App Service Linux sur Azure.
ms.date: 11/1/2018
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 20df5476a2ca6cf8fb0ffbf22e8106e51d17128d
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58070306"
---
# <a name="publish-a-nodejs-application-to-azure-linux-app-service"></a>Publier une application Node.js sur Azure (App Service Linux)

Ce tutoriel explique comment créer une application simple Node.js et la publier sur Azure.

Quand vous publiez une application Node.js sur Azure, plusieurs options s’offrent à vous. Il existe notamment Azure App Service, machine virtuelle exécutant un système d’exploitation de votre choix, Azure Container Service (AKS) pour la gestion avec Kubernetes, instance de conteneur utilisant Docker, et bien plus encore. Pour plus d’informations sur chacune de ces options, consultez [Calcul](https://azure.microsoft.com/product-categories/compute/).

Pour ce tutoriel, vous déployez l’application sur [App Service Linux](/azure/app-service/containers/app-service-linux-intro).
App Service Linux déploie un conteneur Linux Docker pour exécuter l’application Node.js (par opposition à App Service Windows, qui exécute des applications Node.js derrière IIS sur Windows).

Ce tutoriel montre comment créer une application Node.js à partir d’un modèle installé avec les outils Node.js pour Visual Studio, pousser le code vers un dépôt sur GitHub, puis provisionner Azure App Service par le biais du portail web Azure afin de pouvoir procéder au déploiement à partir du dépôt GitHub. Pour utiliser la ligne de commande afin de provisionner Azure App Service et d’envoyer le code à partir d’un dépôt Git local, consultez [Créer une application Node.js](/azure/app-service/containers/quickstart-nodejs).

Dans ce didacticiel, vous apprendrez à :
> [!div class="checklist"]
> * Créer un projet Node.js
> * Créer un dépôt GitHub pour le code
> * Créer un service d’applications Linux sur Azure
> * Déployer sur Linux

## <a name="prerequisites"></a>Prérequis

* Au préalable, vous devez avoir installé Visual Studio et la charge de travail de développement Node.js. 

    ::: moniker range=">=vs-2019"
    Si vous n’avez pas encore installé Visual Studio 2019, accédez à la page  [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/)  pour l’installer gratuitement.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Si vous n’avez pas encore installé Visual Studio 2017, accédez à la page  [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/)  pour l’installer gratuitement.
    ::: moniker-end

    Si vous devez installer la charge de travail, mais que vous avez déjà installé Visual Studio, cliquez sur **Outils** > **Obtenir les outils et fonctionnalités...**, qui ouvre Visual Studio Installer. Choisissez la charge de travail **Développement Node.js**, puis choisissez **Modifier**.

    ![Charge de travail Node.js dans Visual Studio Installer](../ide/media/quickstart-nodejs-workload.png)

* Le runtime Node.js doit être installé.

    Si vous ne l’avez pas déjà fait, installez la version LTS à partir du site web [Node.js](https://nodejs.org/en/download/). En règle générale, Visual Studio détecte automatiquement le runtime Node.js installé. S’il ne détecte aucun runtime installé, vous pouvez configurer votre projet pour référencer le runtime installé dans la page de propriétés (après avoir créé un projet, cliquez avec le bouton droit sur le nœud de projet, puis choisissez **Propriétés**).

## <a name="create-a-nodejs-project-to-run-in-azure"></a>Créer un projet Node.js à exécuter dans Azure

1. Ouvrez Visual Studio.

1. Dans la barre de menus supérieure, choisissez **Fichier** > **Nouveau** > **Projet**.

1. Créez une application TypeScript Express.

    ::: moniker range=">=vs-2019"
    Dans la boîte de dialogue **Créer un projet**, tapez **javascript** dans la zone de recherche pour filtrer les résultats, choisissez **Application Azure Node.js Express 4 de base**, puis choisissez **Suivant**. Choisissez ensuite **Créer**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Dans la boîte de dialogue **Nouveau projet**, dans le volet gauche, développez **JavaScript**, puis choisissez **Node.js**. Dans le volet central, choisissez **Application Azure Node.js Express 4 de base**, puis **OK**.

    ![Créer une application TypeScript Express](../javascript/media/azure-ts-express-app.png)
    ::: moniker-end
    Si vous ne voyez pas le modèle de projet **Application Azure Node.js Express 4 de base**, vous devez ajouter la charge de travail **Développement Node.js**. Pour obtenir des instructions détaillées, consultez les [Prérequis](#prerequisites).

    Visual Studio crée le projet et l’ouvre dans l’Explorateur de solutions (volet droit).

1. Appuyez sur **F5** pour générer et exécuter l’application, et vérifiez que tout s’exécute comme prévu.

1. Sélectionnez **Fichier** > **Ajouter au contrôle de code source** pour créer un dépôt Git local pour le projet.

    À ce stade, une application Node.js utilisant le framework Express et écrite en TypeScript fonctionne et est archivée dans le contrôle de code source local.

1. Modifiez le projet comme vous le souhaitez avant de procéder aux étapes suivantes.

## <a name="push-code-from-visual-studio-to-github"></a>Pousser le code de Visual Studio vers GitHub

Pour configurer GitHub pour Visual Studio

1. Vérifiez que l’[Extension GitHub pour Visual Studio](https://visualstudio.github.com/) est installée et activée à l’aide de l’élément de menu **Outils** > **Extensions et mises à jour**.

2. Dans le menu, sélectionnez **Affichage** > **Autres fenêtres** > **GitHub**.

    La fenêtre GitHub s’ouvre.

3. Si vous ne voyez pas le bouton **Prise en main** dans la fenêtre GitHub, cliquez sur **Fichier** > **Ajouter au contrôle de code source** et attendez que l’interface utilisateur soit mise à jour.

    ![Ouvrir la fenêtre GitHub](../javascript/media/azure-github-get-started.png)

4. Cliquez sur **Prise en main**.

    Si vous êtes déjà connecté à GitHub, la boîte à outils apparaît, comme illustré ci-dessous.

    ![Paramètres du dépôt GitHub](../javascript/media/azure-github-publish.png)

5. Renseignez les champs du nouveau dépôt à publier, puis cliquez sur **Publier**.

    Après quelques instants, une bannière « Création réussie du dépôt » s’affiche.

    Dans la section suivante, vous allez découvrir comment publier à partir de ce dépôt vers Azure App Service sur Linux.

## <a name="create-a-linux-app-service-in-azure"></a>Créer un service d’applications Linux dans Azure

1. Connectez-vous au [portail Azure](https://portal.azure.com).

2. Sélectionnez **App Services** dans la liste des services sur la gauche, puis cliquez sur **Ajouter**.

3. Si nécessaire, créez un groupe de ressources et un plan App Service pour héberger la nouvelle application.

4. Veillez à choisir **Linux** comme **Système d’exploitation** et à sélectionner la version requise de Node.js comme **Pile d’exécution**, comme indiqué dans l’illustration.

    ![Créer un service d’applications Linux](../javascript/media/azure-create-appservice-annotated.png)

5. Cliquez sur **Créer** pour créer le service d’applications.

    Le déploiement peut prendre quelques minutes.

6. Une fois le déployé terminé, accédez à la section **Paramètres d’application** et ajoutez un paramètre avec le nom `SCM_SCRIPT_GENERATOR_ARGS` et la valeur `--node`.

    ![Paramètres d’application](../javascript/media/azure-script-generator-args.png)

    > [!WARNING]
    > Le processus de déploiement du service d’applications utilise un ensemble de paramètres heuristiques pour déterminer le type d’application à essayer d’exécuter. Si un fichier *.sln* est détecté dans le contenu déployé, il part du principe qu’un projet basé sur MSBuild est déployé. Le paramètre ajouté ci-dessus remplace cette logique et spécifie explicitement qu’il s’agit d’une application Node.js. Sans ce paramètre, le déploiement de l’application Node.js échoue si le fichier *.sln* fait partie du dépôt en cours de déploiement sur le service d’applications.

7. Après le déploiement, ouvrez le service d’applications et sélectionnez **Options de déploiement**.

    ![Options de déploiement](../javascript/media/azure-deployment-options.png)

8. Cliquez sur **Choisir une source**, choisissez **GitHub**, puis configurez les autorisations requises.

    ![Autorisations GitHub](../javascript/media/azure-choose-source.png)

9. Sélectionnez le dépôt et la branche à publier, puis sélectionnez **OK**.

    ![Publier sur App Service Linux](../javascript/media/azure-repo-and-branch.png)

    La page **Options de déploiement** s’affiche pendant la synchronisation.

    ![Déploiement et synchronisation avec GitHub](../javascript/media/azure-deployment-options-sync.png)

    Une fois la synchronisation terminée, une coche s’affiche.

    Le site exécute maintenant l’application Node.js à partir du dépôt GitHub. Elle est accessible via l’URL créée pour le service d’applications Azure (par défaut le nom donné au service d’applications Azure, suivi de « .azurewebsites.net »).

## <a name="modify-your-app-and-push-changes"></a>Modifier votre application et pousser les modifications

1. Ajoutez le code présenté ici dans *app.ts* après la ligne `app.use('/users', users);`. Une API REST est ajoutée dans l’URL */api*.

    ```typescript
    app.use('/api', (req, res, next) => {
        res.json({"result": "success"});
    });
    ```

2. Générez le code et testez-le localement, puis archivez-le et poussez-le vers GitHub.

    Dans le portail Azure, quelques instants sont nécessaires pour détecter les modifications dans le dépôt GitHub, puis une nouvelle synchronisation du déploiement démarre. Cela doit ressembler à l’illustration suivante.

    ![Modifier et synchroniser](../javascript/media/azure-changes-detected.png)

3. Une fois le déploiement terminé, accédez au site public et ajoutez */api* à l’URL. La réponse JSON est retournée.

## <a name="troubleshooting"></a>Résolution des problèmes

* Si le processus node.exe s’arrête (autrement dit, si une exception non gérée se produit), le conteneur redémarre.
* Quand le conteneur démarre, il passe par diverses méthodes heuristiques pour déterminer comment démarrer le processus Node.js. Vous pouvez consulter les détails de l’implémentation dans [generateStartupCommand.js](https://github.com/Azure-App-Service/node/blob/master/8.9.4/startup/generateStartupCommand.js).
* Vous pouvez vous connecter au conteneur en cours d’exécution par le biais du protocole SSH si vous souhaitez effectuer un examen approfondi. Cette opération peut s’effectuer facilement à l’aide du portail Azure. Sélectionnez le service d’applications et faites défiler la liste des outils jusqu’à atteindre **SSH** sous la section **Outils de développement**.
* Pour faciliter le dépannage, accédez aux paramètres de **Journaux de diagnostic** du service d’applications et faites passer le paramètre **Journalisation de conteneur Docker** de **Désactivé** à **Système de fichiers**. Les journaux sont créés dans le conteneur sous */home/LogFiles/*_docker.log* et sont accessibles à l’aide de SSH ou FTP(S).
* Vous pouvez assigner un nom de domaine personnalisé au site, à la place de l’URL *. azurewebsites.net affectée par défaut. Pour plus d’informations, consultez la rubrique [Mapper un domaine personnalisé](/azure/app-service/app-service-web-tutorial-custom-domain).
* Le déploiement sur un site de préproduction afin de procéder à d’autres tests avant de passer en production constitue une bonne pratique. Pour plus d’informations sur la façon de configurer cela, consultez la rubrique [Créer des environnements intermédiaires](/azure/app-service/web-sites-staged-publishing).
* Pour obtenir des réponses aux questions les plus fréquentes, consultez le [FAQ d’Azure App Service sur Linux](/azure/app-service/containers/app-service-linux-faq).

## <a name="next-steps"></a>Étapes suivantes

Dans ce tutoriel, vous avez découvert comment créer un service d’applications Linux et déployer une application Node.js sur le service. Vous souhaiterez peut-être en savoir plus sur App Service Linux.

> [!div class="nextstepaction"]
> [App Service Linux](/azure/app-service/containers/app-service-linux-intro)
