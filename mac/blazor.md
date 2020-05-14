---
title: Créer des applications Web Blazor
description: Fournit des informations sur le support Blazor dans ASP.NET applications Core dans Visual Studio pour Mac.
author: jongalloway
ms.author: jogallow
ms.date: 12/17/2019
ms.technology: vs-ide-general
ms.assetid: D2717D3A-9225-40A8-8155-7D0143B2CA60
ms.openlocfilehash: dbc49a0ea9b4e4fa7880b6226331d447339b6575
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75737585"
---
# <a name="create-blazor-web-apps"></a>Créer des applications Web Blazor

Ce guide propose une introduction à la création de votre première application Web Blazor. Pour plus de conseils en profondeur, voir [Introduction à ASP.NET Core Blazor](/aspnet/core/blazor/index).

Visual Studio for Mac (à partir de la version 8.4) comprend la prise en charge du développement et de la publication de ASP.NET applications Core Blazor Server. Blazor est un cadre pour la construction d’interface utilisateur web interactive côté client avec .NET, qui offre les avantages suivants aux développeurs web:

* Écriture de code dans C# plutôt que dans JavaScript.
* Tirez parti de l’écosystème .NET existant des bibliothèques .NET.
* Partagez la logique de l’application sur le serveur et le client.
* Bénéficiez de . Les performances, la fiabilité et la sécurité de NET.
* Restez productif avec Visual Studio sur PC, Linux et macOS.
* Développez avec un ensemble commun de langages, de frameworks et d’outils stables, riches en fonctionnalités et faciles à utiliser.

## <a name="creating-a-new-blazor-project"></a>Création d’un nouveau projet Blazor

1. Sur la **fenêtre de départ**, sélectionnez **Nouveau** pour créer un nouveau projet :

   ![Studio visuel pour Mac Start Window avec une nouvelle sélection mise en évidence](media/blazor-new-project.png)
1. Dans la nouvelle boîte de dialogue **project,** sélectionnez **.NET Core** > **App** > **Blazor Server App** et sélectionnez **Next**: ![Choisissez un modèle pour votre nouveau dialogue de projet avec le modèle d’application De serveur Blazor sélectionné](media/blazor-project-template.png)

1. Sélectionnez .NET Core 3.1 comme cadre cible, puis sélectionnez **Next**. 
   ![Configurez votre nouveau dialogue Blazor Server App affiché avec Target Framework sélectionné pour .NET Core 3.1](media/blazor-select-target-framework.png)

1. Choisissez un nom pour votre projet et ajoutez le support Git si désiré. Sélectionnez **Créer** pour créer le projet.
   ![BConfigure votre nouveau dialogue Blazor Server App affiché lors de la saisie du nom du projet](media/blazor-name-project.png)

   Visual Studio pour Mac ouvre votre projet dans la fenêtre de mise en page Code.
1. Sélectionnez **Run** > **Start Sans déboguer** pour exécuter l’application.

   Visual Studio démarre [Kestrel](/aspnet/core/fundamentals/servers/kestrel), `https://localhost:5001`ouvre un navigateur à , et affiche votre application Web Blazor.

   ![Application web Blazor dans Safari](media/blazor-new-app-in-edge.png)

## <a name="blazor-support-in-visual-studio-for-mac"></a>Soutien de Blazor dans Visual Studio pour Mac

Visual Studio for Mac (à partir de la version 8.4) comprend de nouvelles fonctionnalités pour vous aider à créer de nouveaux projets de serveurs Blazor. En outre, il vous fournit le soutien standard que vous attendez, comme la construction, la gestion et le débogage des projets Blazor. 

Dans la procédure pas à pas ci-dessus, nous avons vu comment le modèle de projet Blazor Server App vous aide à créer un nouveau projet Blazor Server App. Jetons un coup d’oeil à quelques-unes des fonctionnalités supplémentaires dans Visual Studio pour Mac pour soutenir le développement du projet de serveur Blazor.

### <a name="editor-support-for-razor-files"></a>Soutien de l’éditeur pour les fichiers *.razor*
Visual Studio pour Mac comprend la prise en charge de l’édition de fichiers .razor - la majorité des fichiers que vous allez utiliser lors de la création d’applications Blazor. La version Windows et Mac de l’IDE partagent le même éditeur pour les fichiers .razor. Vous verrez la colorisation complète et le support d’achèvement pour vos fichiers .razor, y compris les achèvements pour les composants Razor déclarés dans le projet.

![Visual Studio pour mac fenêtre de l’éditeur montrant Intellisense pour Blazor](media/blazor-intellisense.png)

### <a name="publishing-blazor-applications-to-azure-app-service"></a>Publication des applications Blazor à Azure App Service
Vous pouvez également publier des applications Blazor directement sur Azure App Service. Si vous n’avez pas de compte Azure pour exécuter votre application Blazor sur Azure, vous pouvez toujours vous [inscrire à un](https://azure.microsoft.com/free) compte gratuit ici qui vient également 12 mois de services populaires gratuits, 200 $ de crédits Azure gratuits, et plus de 25 services toujours gratuits.

![Visual Studio pour Mac montrant l’expérience d’édition Azure](media/blazor-azure-publish.png)

## <a name="project-anatomy"></a>Anatomie du projet

Les applications Web Blazor comprennent quelques répertoires et fichiers par défaut. Au fur et à mesure que vous commencez, voici les principaux que vous devrez connaître :

### <a name="pages-folder"></a>Dossier Pages

Ce dossier contient les pages Web d’un projet, qui utilisent une extension de fichier *.razor.*

### <a name="shared-folder"></a>Dossier partagé

Ce dossier comprend des composants partagés, également en utilisant l’extension *.razor.* Vous verrez que cela inclut *MainLayout.razor*, qui est utilisé pour définir la mise en page commune à travers l’application. Il comprend également le composant *navMenu.razor* partagé, qui est utilisé sur toutes les pages. Si vous créez des composants réutilisables, ils iront dans le dossier **partagé.**

### <a name="app-settings"></a>Paramètres de l’application

Le fichier *appSettings.json* contient des données de configuration telles que des chaînes de connexion.

Pour plus d’informations sur la configuration, voir la [configuration dans ASP.NET guide](/aspnet/core/fundamentals/configuration/index).

### <a name="wwwroot-folder"></a>Dossier racine

Ce dossier contient des fichiers statiques, tels que les fichiers HTML, JavaScript et CSS. Pour plus d’informations, consultez [Fichiers statiques dans ASP.NET Core](/aspnet/core/fundamentals/static-files).

### <a name="programcs"></a>Program.cs

Ce fichier contient le point d’entrée pour le programme. Pour plus d’informations, consultez [Hôte web ASP.NET Core](/aspnet/core/fundamentals/host/web-host).

### <a name="startupcs"></a>Startup.cs

Ce fichier contient du code qui configure le comportement de l’application, par exemple si l’application nécessite le consentement pour les cookies. Pour plus d’informations, consultez [Start-up de l’application dans ASP.NET Core](/aspnet/core/fundamentals/startup).

## <a name="summary"></a>Résumé
Dans ce tutoriel, vous avez vu comment créer une nouvelle application Blazor Server en studio visuel pour Mac, et a appris certaines des fonctionnalités que Visual Studio pour Mac offre pour vous aider à créer des applications Blazor.

## <a name="see-also"></a>Voir aussi

Pour un guide plus complet pour créer des applications Web Blazor, voir [Introduction à ASP.NET Core Blazor](/aspnet/core/blazor/index).
