---
title: Introduction à Azure Functions
description: Prise en main de Azure Functions dans Visual Studio pour Mac.
author: jmatthiesen
ms.author: jomatthi
ms.date: 04/02/2019
ms.technology: vs-ide-install
ms.assetid: 25CD47A4-5B32-4734-8EF3-E24A02AABF29
ms.topic: how-to
ms.openlocfilehash: 69ecab4f4d3dd7d99821b384dbda0c8986297282
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94492839"
---
# <a name="introduction-to-azure-functions"></a>Introduction à Azure Functions

Azure Functions permet de créer et d’exécuter dans le cloud des fonctions, à savoir des extraits de code basés sur des événements, sans devoir provisionner ni gérer explicitement l’infrastructure. Pour plus d’informations, consultez la [documentation sur Azure Functions](/azure/azure-functions/).

## <a name="requirements"></a>Configuration requise

Les outils Azure Functions sont inclus dans **Visual Studio pour Mac 7.5** et ultérieur.

Pour créer et déployer des fonctions, vous avez également besoin d’un abonnement Azure. Si vous n’avez pas de compte Azure, vous pouvez vous inscrire dès aujourd’hui gratuitement et recevoir 12 mois de services populaires gratuits, un crédit gratuit de $200 et 25 services gratuits gratuits-> [https://azure.com/free](https://azure.com/free/dotnet) .

## <a name="creating-your-first-azure-functions-project"></a>Création d’un premier projet Azure Functions

1. Dans Visual Studio pour Mac, sélectionnez **fichier > nouvelle solution**.
2. Dans la boîte de dialogue Nouveau projet, sélectionnez le modèle Azure Functions sous **Cloud > Général** , puis cliquez sur **Suivant** :

    ![Boîte de dialogue Nouveau projet montrant l’option Azure Functions](media/azure-functions-image1.png)

3. Sélectionnez le modèle Azure Functions initial à utiliser, entrez le nom de la fonction, puis cliquez sur **Suivant**.

    ![Boîte de dialogue Nouveau projet montrant les modèles de fonctions Azure Functions](media/azure-functions-image2.png)

    > [!TIP]
    > Même si le runtime et les modèles (CLI) d’Azure Functions en bundle sont conservés autant que possible à jour, ils deviennent inévitablement obsolètes. Quand vous créez un projet Functions, Visual Studio pour Mac recherche des mises à jour de l’interface CLI et vous avise, comme indiqué dans l’image ci-dessous. Cliquez simplement sur le bouton pour télécharger les modèles mis à jour.
    > ![Boîte de dialogue Nouveau projet montrant que des mises à jour Azure Functions sont disponibles](media/azure-functions-update.png)

    Selon le type de fonction que vous sélectionnez, la page suivante vous invite à saisir des informations, par exemple les droits d’accès, comme illustré dans l’image qui suit :

    ![Boîte de dialogue Nouveau projet montrant une option supplémentaire](media/azure-functions-image3.png)

    Pour plus d’informations sur les différents types de modèle Azure Functions et les propriétés de liaison nécessaires à la configuration de chaque modèle, consultez la section [Modèles de fonctions disponibles](#available-function-templates). Pour cet exemple, nous utilisons un déclencheur HTTP auquel nous affectons des droits d’accès de type anonyme.

4. Une fois les paramètres définis, choisissez l’emplacement du projet, puis cliquez sur **Créer**.

Visual Studio pour Mac crée un projet .NET Standard qui inclut une fonction par défaut. Il contient également des références NuGet à une variété de packages **AzureWebJobs** , ainsi qu’au package **Newtonsoft.Json**.

![Éditeur Visual Studio pour Mac montrant une toute nouvelle fonction Azure à partir d’un modèle](media/azure-functions-newproj.png)

Le nouveau projet contient les fichiers suivants :

* **votre-nom-de-fonction.cs**  - cette classe contient du code réutilisable pour la fonction que vous avez sélectionnée. Elle contient un attribut **FunctionName** avec le nom de la fonction, ainsi qu’un attribut déclencheur, qui spécifie ce qui déclenche la fonction (par exemple une requête HTTP). Pour plus d’informations sur la méthode de fonction, consultez l’article [Informations de référence pour les développeurs C# sur Azure Functions](/azure/azure-functions/functions-dotnet-class-library).
* **host.json** : ce fichier décrit les options de configuration globale pour l’hôte Functions. Pour obtenir un exemple de fichier et des informations sur les paramètres disponibles pour ce fichier, consultez [Informations de référence sur le fichier host.json pour Azure Functions](/azure/azure-functions/functions-host-json).
* **local.settings.json** : ce fichier contient tous les paramètres nécessaires pour exécuter des fonctions localement. Ces paramètres sont utilisés par Azure Functions Core Tools. Pour plus d’informations, consultez [Local settings file](/azure/azure-functions/functions-run-local#local-settings-file) (Fichier de paramètres local) dans l’article Azure Functions Core Tools.

Une fois que vous avez créé votre projet Azure Functions dans Visual Studio pour Mac, vous pouvez tester la fonction déclenchée par HTTP par défaut à partir de votre ordinateur local.

## <a name="testing-the-function-locally"></a>Test de la fonction au niveau local

Dans la mesure où Visual Studio pour Mac prend en charge Azure Functions, vous pouvez tester et déboguer votre fonction sur un ordinateur de développement local.

1. Pour tester localement votre fonction, appuyez sur le bouton **Exécuter** dans Visual Studio pour Mac :

    ![Bouton de démarrage du débogage dans Visual Studio pour Mac](media/azure-functions-run.png)

1. L’exécution du projet démarre le débogage local sur la fonction Azure et ouvre une nouvelle fenêtre de terminal, comme l’illustre l’image suivante :

    ![Fenêtre de terminal montrant la sortie de la fonction](media/azure-functions-terminal.png)

    Copiez l’URL de la sortie.

3. Collez l’URL de la demande HTTP dans la barre d’adresses de votre navigateur. Ajoutez la chaîne de requête `?name=<yourname>` à la fin de l’URL et exécutez la requête. L’image suivante montre la réponse dans le navigateur à la requête GET locale retournée par la fonction :

    ![Requête HTTP dans le navigateur](media/azure-functions-httpreq.png)

## <a name="adding-another-function-to-your-project"></a>Ajout d’une autre fonction à votre projet

Les modèles de fonctions vous permettent de créer rapidement des fonctions à l’aide des déclencheurs et des modèles les plus courants. Pour créer un autre type de fonction, effectuez les étapes suivantes :

1. Pour ajouter une nouvelle fonction, cliquez avec le bouton droit sur le nom du projet et sélectionnez **Ajouter > Ajouter une fonction** :

    ![Action de contexte permettant d’ajouter une nouvelle fonction](media/azure-functions-addnew.png)

2. Dans la boîte de dialogue **Nouvelle fonction Azure** , sélectionnez la fonction dont vous avez besoin :

    ![Boîte de dialogue Nouvelle fonction Azure](media/azure-functions-image4.png)

    Une liste de modèles Azure Functions est fournie dans la section [Modèles de fonctions disponibles](#available-function-templates).

Vous pouvez utiliser la procédure ci-dessus pour ajouter des fonctions à votre projet d’application de fonction. Chaque fonction dans le projet peut avoir un déclencheur différent, mais une fonction ne doit avoir qu’un seul déclencheur. Pour plus d’informations, consultez [Concepts des déclencheurs et liaisons Azure Functions](/azure/azure-functions/functions-triggers-bindings).

## <a name="publish-to-azure"></a>Publication dans Azure

1. Cliquez avec le bouton droit sur le nom du projet et sélectionnez **publier > publier sur Azure** :  ![ menu contextuel avec publier > publier sur Azure... option mise en surbrillance](media/azure-functions-image5.png)
2. Si vous avez déjà connecté votre compte Azure à Visual Studio pour Mac, une liste des services d’application disponibles s’affiche. Si vous ne vous êtes pas connecté, vous êtes invité à le faire.
3. Dans la boîte de dialogue **Publier sur Azure App Service** , sélectionnez un service d’application existant, ou créez un service en cliquant sur **Nouveau**.
4. Dans la boîte de dialogue **créer un app service** , entrez vos paramètres :  ![ boîte de dialogue Nouveau App service, avec les champs nom du service, abonnement, groupe de ressources et plan de service.](media/azure-functions-image7.png)

    |Paramètre  |Description  |
    |---------|---------|
    |**Nom de l’App Service**|Nom global unique qui identifie votre nouvelle application de fonction.|
    |**Abonnement**|Sélectionnez l’abonnement Azure à utiliser.|
    |**[Groupe de ressources](/azure/azure-resource-manager/resource-group-overview)**|Nom du groupe de ressources où créer votre application de fonction. Choisissez **+** de créer un nouveau groupe de ressources.|
    |**[Plan de service](/azure/azure-functions/functions-scale)**|Choisissez un plan existant, ou créez un plan personnalisé. Choisissez un emplacement dans une région proche de chez vous, ou proche d’autres services auxquels vos fonctions ont accès.|

5. Cliquez sur **Suivant** pour créer un compte de stockage. Un compte de stockage Azure est obligatoire par le runtime Functions. Cliquez sur **Personnalisé** pour créer un compte de stockage à usage général, ou utilisez un compte existant :

    ![Boîte de dialogue Nouveau App Service avec l’invite de nom du compte de stockage.](media/azure-functions-image8.png)

6. Cliquez sur **Créer** pour créer une application de fonctions et les ressources associées dans Azure avec ces paramètres et déployer votre code de projet de fonction.

7. Durant la publication, une boîte de dialogue vous invite éventuellement à « Mettre à jour la version de Functions sur Azure ». Cliquez sur **Oui** :

    ![Vous êtes invité à « mettre à jour les paramètres d’application Azure pour qu’ils correspondent à la version des fonctions locales ? » avec les options Oui et non.](media/azure-functions-image12.png)

## <a name="function-app-settings"></a>Paramètres Function App

Les paramètres que vous avez ajoutés au fichier local.settings.json doivent être également ajoutés à l’application de fonction dans Azure. Ces paramètres ne sont pas chargés automatiquement quand vous publiez le projet.

Pour accéder aux paramètres de votre application, accédez au Portail Azure à l’adresse [https://ms.portal.azure.com/](https://ms.portal.azure.com/) . Sous **Function Apps** , sélectionnez **Function Apps** , puis sélectionnez le nom de votre fonction :

![menu Azure Functions](media/azure-functions-image9.png)

Sous l’onglet **Vue d’ensemble** , sélectionnez **Paramètres de l’application** sous **Fonctionnalités configurées**  :

![Onglet Vue d’ensemble d’Azure Functions](media/azure-functions-image10.png)

À partir de cet emplacement, vous pouvez définir les paramètres d’application de l’application de fonction. Vous pouvez ensuite ajouter de nouveaux paramètres d’application ou modifier ceux qui existent déjà :

![zone des paramètres d’application du portail Azure](media/azure-functions-image11.png)

Vous pouvez être amené à définir un paramètre important : `FUNCTIONS_EXTENSION_VERSION`. Quand vous publiez à partir de Visual Studio pour Mac, cette valeur doit correspondre à **beta**.

## <a name="available-function-templates"></a>Modèles de fonctions disponibles

- **GitHub Trigger** : répond aux événements qui se produisent dans vos dépôts GitHub. Pour plus d’informations, consultez [l’article Azure Functions sur GitHub](/azure/azure-functions/functions-create-github-webhook-triggered-function).
  - GitHub commenter : cette fonction est exécutée quand elle reçoit un webhook GitHub pour un problème ou une demande de tirage (pull request), et ajoute un commentaire.
  - WebHook GitHub - Cette fonction est exécutée quand elle reçoit un Webhook GitHub.

- **HTTP** : déclenche l’exécution du code à l’aide d’une requête HTTP. Des modèles explicites sont disponibles pour les déclencheurs HTTP suivants :
  - Http Trigger
  - Http GET CRUD
  - Http POST CRUD
  - Http Trigger with parameters

- **Timer** : exécute le nettoyage ou d’autres tâches de traitement par lots selon une planification prédéfinie. Ce modèle accepte deux champs : un nom et une planification (expression CRON de six champs). Pour plus d’informations, consultez [l’article Azure Functions sur les minuteurs](/azure/azure-functions/functions-create-scheduled-function).

- **Queue Trigger** : cette fonction répond aux messages à mesure qu’ils arrivent dans la file d’attente Stockage Azure. En plus du nom de fonction, ce modèle accepte un **chemin** (nom de la file d’attente à partir de laquelle le message est lu) et une **connexion** de compte de stockage (nom du paramètre d’application contenant votre chaîne de connexion de compte de stockage). Pour plus d’informations, consultez [l’article Azure Functions sur Stockage File d’attente](/azure/azure-functions/functions-create-storage-queue-triggered-function).

- **Blob Trigger** : traite les objets blob Stockage Azure quand ils sont ajoutés à un conteneur. En plus du nom de fonction, ce modèle accepte des propriétés de chemin et de connexion. La propriété de chemin correspond au chemin dans le compte de stockage surveillé par le déclencheur. Le compte de connexion correspond au nom du paramètre d’application contenant votre chaîne de connexion de compte de stockage. Pour plus d’informations, consultez [l’article Azure Functions sur Stockage Blob](/azure/azure-functions/functions-create-storage-blob-triggered-function).

- **Generic WebHook** : cette fonction simple s’exécute chaque fois qu’elle reçoit une demande d’un service prenant en charge les webhooks. Pour plus d’informations, consultez l’[article Azure Functions sur les Webhooks génériques](/azure/azure-functions/functions-create-generic-webhook-triggered-function).

- **Durable functions orchestration** : les fonctions durables vous permettent d’écrire des fonctions avec état dans un environnement serverless. L’extension gère l’état, les points de contrôle et les redémarrages à votre place. Pour plus d’informations, consultez les guides Azure Functions sur [Durable Functions](/azure/azure-functions/durable-functions-overview).

- **Image Resizer** : cette fonction crée des images redimensionnées chaque fois qu’un objet blob est ajouté à un conteneur. Le modèle accepte un chemin et une chaîne de connexion pour le déclencheur, une petite image de sortie et une moyenne image de sortie.

- **SAS token** : cette fonction génère un jeton SAP pour un conteneur Stockage Azure et un nom d’objet blob spécifiés. En plus du nom de fonction, ce modèle accepte des propriétés de chemin et de connexion. La propriété de chemin correspond au chemin dans le compte de stockage surveillé par le déclencheur. Le compte de connexion correspond au nom du paramètre d’application contenant votre chaîne de connexion de compte de stockage. Vous devez également définir des **droits d’accès**. Le niveau d’autorisation contrôle si la fonction requiert une clé API et la clé à utiliser ; La fonction utilise une touche de fonction ; L’administrateur utilise votre clé d’accès au compte. Pour plus d’informations, consultez l’exemple de [fonction Azure C# pour générer des jetons SAP](https://github.com/Azure-Samples/functions-dotnet-sas-token/).
