---
title: Introduction à Azure Functions
description: Utilisation des fonctions Azure dans Visual Studio pour Mac.
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 25CD47A4-5B32-4734-8EF3-E24A02AABF29
ms.openlocfilehash: 5d787efbd09ad7f2d4a1f5f72b8f1493d8c6c587
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
---
# <a name="introduction-to-azure-functions"></a>Introduction à Azure Functions

Azure Functions permet de créer et d’exécuter dans le cloud des fonctions, à savoir des extraits de code basés sur des événements, sans devoir provisionner ni gérer explicitement l’infrastructure. Pour plus d’informations, consultez la [documentation sur Azure Functions](https://docs.microsoft.com/azure/azure-functions/).

## <a name="requirements"></a>Configuration requise

Les outils Azure Functions sont inclus dans **Visual Studio pour Mac 7.5**.

Pour créer et déployer des fonctions, vous devez également disposer d’un abonnement Azure (disponible gratuitement sur le site [https://azure.com/free](https://azure.com/free)).

## <a name="creating-your-first-azure-functions-project"></a>Création d’un premier projet Azure Functions

1. Dans Visual Studio pour Mac, sélectionnez **Fichier > Nouvelle solution**. 
2. Dans la boîte de dialogue Nouveau projet, sélectionnez le modèle Azure Functions sous **Cloud > Général**, puis cliquez sur **Suivant** :

    ![Boîte de dialogue Nouveau projet montrant l’option Azure Functions](media/azure-functions-image1.png)

3. Entrez un **nom de projet**, puis sélectionnez **Créer**.

Visual Studio pour Mac crée un projet .NET Standard comprenant une fonction HttpTrigger par défaut. Il contient également des références NuGet à une variété de packages **AzureWebJobs**, ainsi qu’au package **Newtonsoft.Json**.

![Éditeur Visual Studio pour Mac montrant une toute nouvelle fonction Azure à partir d’un modèle](media/azure-functions-newproj.png)

Le nouveau projet contient les fichiers suivants :

* **HttpTrigger.cs** : cette classe contient du code réutilisable pour une fonction déclenchée par HTTP. Elle contient un attribut **FunctionName** avec le nom de la fonction, ainsi qu’un attribut déclencheur, **HttpTrigger**, qui spécifie que la fonction est déclenchée par une requête HTTP. Pour plus d’informations sur la méthode de fonction, consultez l’article [Informations de référence pour les développeurs C# sur Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-dotnet-class-library).
* **host.json** : ce fichier décrit les options de configuration globale pour l’hôte Functions. Pour obtenir un exemple de fichier et des informations sur les paramètres disponibles pour ce fichier, consultez [Informations de référence sur le fichier host.json pour Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-host-json).
* **local.settings.json** : ce fichier contient tous les paramètres nécessaires pour exécuter des fonctions localement. Ces paramètres sont utilisés par Azure Functions Core Tools. Pour plus d’informations, consultez [Fichier de paramètres locaux](https://docs.microsoft.com/en-us/azure/azure-functions/functions-run-local#local-settings-file) dans l’article sur Azure Functions Core Tools.

Une fois que vous avez créé votre projet Azure Functions dans Visual Studio pour Mac, vous pouvez tester la fonction déclenchée par HTTP par défaut à partir de votre ordinateur local.

<!--
## Create an Azure storage account

[Describe why this step is necessary and what it does]

1. Log on to your account at [https://portal.azure.com](https://portal.azure.com).
2. Under the **Favorites** section, located on the left of the screen, select **Storage Accounts**:
    ![]()
3. Select **Add** to create a new storage account:
    ![]()
4. Enter a globally unique name for the **Name** and reuse it for the **Resource group**. You can keep all the other items as their default.
    ![]()
5. Click **Create**. It might take a few minutes to create the storage account. You'll get a notification once it has been successfully created.
6. Select the **Go to resource** button from the notification:
    ![]()
-->

## <a name="testing-the-function-locally"></a>Test de la fonction au niveau local

Dans la mesure où Visual Studio pour Mac prend en charge Azure Functions, vous pouvez tester et déboguer votre fonction sur un ordinateur de développement local.

1. Pour tester localement votre fonction, appuyez sur le bouton **Exécuter** dans Visual Studio pour Mac :

    ![Bouton de démarrage du débogage dans Visual Studio pour Mac](media/azure-functions-run.png)

1. L’exécution du projet démarre le débogage local sur la fonction Azure et ouvre une nouvelle fenêtre de terminal, comme l’illustre l’image suivante : 

    ![Fenêtre de terminal montrant la sortie de la fonction](media/azure-functions-terminal.png) 

    Copiez l’URL de la sortie.

3. Collez l’URL de la requête HTTP dans la barre d’adresse de votre navigateur. Ajoutez la chaîne de requête `?name=<yourname>` à la fin de l’URL et exécutez la requête. L’image suivante montre la réponse dans le navigateur à la requête GET locale retournée par la fonction :

    ![Requête HTTP dans le navigateur](media/azure-functions-httpreq.png)

## <a name="creating-a-new-function"></a>Création d’une fonction

Les modèles de fonctions vous permettent de créer rapidement des fonctions à l’aide des déclencheurs et des modèles les plus courants. Quand vous créez un projet Azure Functions, il inclut automatiquement une fonction HttpTrigger. Pour créer un autre type de fonction, effectuez les étapes suivantes :

1. Supprimez le fichier **HttpTrigger.cs**. Pour cela, cliquez dessus avec le bouton droit et sélectionnez **Supprimer**. À l’apparition de l’alerte suivante, sélectionnez **Supprimer** pour supprimer le fichier du projet :

    ![Boîte de dialogue permettant de supprimer le fichier du projet](media/azure-functions-remove.png)

2. Pour ajouter une nouvelle fonction, cliquez avec le bouton droit sur le nom du projet et sélectionnez **Ajouter > Ajouter une fonction** :

    ![Action de contexte permettant d’ajouter une nouvelle fonction](media/azure-functions-addnew.png)

3. Dans la boîte de dialogue **Nouvelle fonction Azure**, sélectionnez la fonction dont vous avez besoin :

    ![Boîte de dialogue Nouvelle fonction Azure](media/azure-functions-newfunction.png)

    La section suivante contient la liste des modèles de fonctions Azure.

## <a name="available-function-templates"></a>Modèles de fonctions disponibles

- **HTTP** : déclenche l’exécution du code à l’aide d’une requête HTTP. Des modèles explicites sont disponibles pour les déclencheurs HTTP suivants :
    - Http GET CRUD
    - Http POST CRUD
    - Http Trigger with parameters
    - Http Trigger
- **Timer** : exécute le nettoyage ou d’autres tâches de traitement par lots selon une planification prédéfinie. Ce modèle accepte deux champs : un nom et une planification (expression CRON de six champs). Pour plus d’informations, consultez [l’article Azure Functions sur les minuteurs](https://docs.microsoft.com/azure/azure-functions/functions-create-scheduled-function).
- **GitHub Trigger** : répond aux événements qui se produisent dans vos dépôts GitHub. Pour plus d’informations, consultez [l’article Azure Functions sur GitHub](https://docs.microsoft.com/azure/azure-functions/functions-create-github-webhook-triggered-function).
    - GitHub commenter : cette fonction est exécutée quand elle reçoit un webhook GitHub pour un problème ou une demande de tirage (pull request), et ajoute un commentaire.
    - GitHub WebHook : cette fonction est exécutée quand elle reçoit un webhook GitHub.
- **Blob Trigger** : traite les objets blob Stockage Azure quand ils sont ajoutés à un conteneur. En plus du nom de fonction, ce modèle accepte des propriétés de chemin et de connexion. La propriété de chemin correspond au chemin dans le compte de stockage surveillé par le déclencheur. Le compte de connexion correspond au nom du paramètre d’application contenant votre chaîne de connexion de compte de stockage. Pour plus d’informations, consultez [l’article Azure Functions sur Stockage Blob](https://docs.microsoft.com/azure/azure-functions/functions-create-storage-blob-triggered-function).
- **Queue Trigger** : cette fonction répond aux messages à mesure qu’ils arrivent dans la file d’attente Stockage Azure. En plus du nom de fonction, ce modèle accepte un **chemin** (nom de la file d’attente à partir de laquelle le message est lu) et une **connexion** de compte de stockage (nom du paramètre d’application contenant votre chaîne de connexion de compte de stockage). Pour plus d’informations, consultez [l’article Azure Functions sur Stockage File d’attente](https://docs.microsoft.com/azure/azure-functions/functions-create-storage-queue-triggered-function).
- **Generic WebHook** : cette fonction simple s’exécute chaque fois qu’elle reçoit une demande d’un service prenant en charge les webhooks. Pour plus d’informations, consultez [l’article Azure Functions sur les webhooks génériques](https://docs.microsoft.com/azure/azure-functions/functions-create-generic-webhook-triggered-function).
- **Image Resizer** : cette fonction crée des images redimensionnées chaque fois qu’un objet blob est ajouté à un conteneur. Le modèle accepte un chemin et une chaîne de connexion pour le déclencheur, une petite image de sortie et une moyenne image de sortie.
- **SAS token** : cette fonction génère un jeton SAP pour un conteneur Stockage Azure et un nom d’objet blob spécifiés. En plus du nom de fonction, ce modèle accepte des propriétés de chemin et de connexion. La propriété de chemin correspond au chemin dans le compte de stockage surveillé par le déclencheur. Le compte de connexion correspond au nom du paramètre d’application contenant votre chaîne de connexion de compte de stockage. Vous devez également définir des **droits d’accès**. Le niveau d’autorisation contrôle si la fonction nécessite une clé d’API et la clé à utiliser. La fonction utilise une clé de fonction, et l’administrateur utilise votre clé principale. Pour plus d’informations, consultez l’exemple de [fonction Azure C# pour générer des jetons SAP](https://azure.microsoft.com/resources/samples/functions-dotnet-sas-token/).
- **Durable functions orchestration** : les fonctions durables vous permettent d’écrire des fonctions avec état dans un environnement serverless. L’extension gère l’état, les points de contrôle et les redémarrages pour vous. Pour plus d’informations, consultez les guides Azure Functions sur les [fonctions durables](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview).