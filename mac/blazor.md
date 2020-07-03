---
title: Créer des applications Web éblouissantes
description: Fournit des informations sur la prise en charge de éblouissants dans les applications ASP.NET Core dans Visual Studio pour Mac.
author: jongalloway
ms.author: jogallow
ms.date: 12/17/2019
ms.technology: vs-ide-general
ms.assetid: D2717D3A-9225-40A8-8155-7D0143B2CA60
ms.topic: how-to
ms.openlocfilehash: ac7fcd9044aa6367f140ac4aa96e6aaf4a9f5885
ms.sourcegitcommit: 2ce59c2ffeba5ba7f628c2e6c75cba4731deef8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "85939149"
---
# <a name="create-blazor-web-apps"></a>Créer des applications Web éblouissantes

Ce guide propose une introduction à la création de votre première application Web éblouissante. Pour obtenir des conseils détaillés, consultez [Introduction à ASP.net Core éblouissant](/aspnet/core/blazor/index).

ASP.NET Core éblouissant prend en charge deux options d’hébergement différentes ; Serveur éblouissant et webassembly éblouissant. Visual Studio pour Mac prend en charge les deux modèles d’hébergement. Visual Studio pour Mac 8.4 + prend en charge le serveur éblouissant et Visual Studio pour Mac 8.6 + prend en charge les deux. Pour plus d’informations sur les modèles d’hébergement éblouissants, consultez [ASP.net Core les modèles d’hébergement éblouissant ](https://docs.microsoft.com/aspnet/core/blazor/hosting-models?view=aspnetcore-3.1). La prise en charge du débogage des projets de webassembly éblouissants dans Visual Studio pour Mac est fournie dans une version postérieure à 8,6.

Qu’est-ce que le éblouissant ? Éblouissant est une infrastructure permettant de créer une interface utilisateur Web interactive côté client avec .NET, qui offre les avantages suivants aux développeurs Web :

* Écriture de code dans C# plutôt que dans JavaScript.
* Tirez parti de l’écosystème .NET existant des bibliothèques .NET.
* Partagez la logique de l’application sur le serveur et le client.
* Tirer parti de. Performances, fiabilité et sécurité de NET.
* Restez productif avec Visual Studio sur PC, Linux et macOS.
* Développez avec un ensemble commun de langages, de frameworks et d’outils stables, riches en fonctionnalités et faciles à utiliser.

## <a name="creating-a-new-blazor-server-project"></a>Création d’un projet de serveur éblouissant

1. Dans la **fenêtre démarrer**, sélectionnez **nouveau** pour créer un nouveau projet :

   ![Visual Studio pour Mac la fenêtre de démarrage avec la nouvelle sélection mise en surbrillance](media/blazor-new-project.png)
1. Dans la boîte de dialogue **nouveau projet** , sélectionnez application **.net Core** > **App** > pour **serveur éblouissant** , puis sélectionnez **suivant**: ![ choisir un modèle pour votre boîte de dialogue Nouveau projet avec le modèle application de serveur éblouissant sélectionné](media/blazor-project-template.png)

1. Sélectionnez .NET Core 3,1 comme Framework cible, puis sélectionnez **suivant**. 
   ![Configurer votre nouvelle boîte de dialogue d’application serveur éblouissante affichée avec la version cible de .NET Framework sélectionnée pour .NET Core 3,1](media/blazor-select-target-framework.png)

1. Choisissez un nom pour votre projet et ajoutez la prise en charge de git si vous le souhaitez. Sélectionnez **Créer** pour créer le projet.
   ![BConfigurer la boîte de dialogue de votre nouvelle application serveur éblouissante affichée lors de la saisie du nom du projet](media/blazor-name-project.png)

   Visual Studio pour Mac ouvre votre projet dans la fenêtre de mise en page du code.
1. Sélectionnez **exécuter**  >  **Démarrer sans débogage** pour exécuter l’application.

   Visual Studio démarre [Kestrel](/aspnet/core/fundamentals/servers/kestrel), ouvre un navigateur à `https://localhost:5001` et affiche votre application Web éblouissante.

   ![Application Web éblouissante dans Safari](media/blazor-new-app-in-edge.png)

## <a name="blazor-support-in-visual-studio-for-mac"></a>Prise en charge des éblouissants dans Visual Studio pour Mac

Visual Studio pour Mac (à partir de la version 8,4) comprend de nouvelles fonctionnalités qui vous aideront à créer des projets de serveur éblouissants. En outre, il vous offre la prise en charge standard attendue, comme la génération, l’exécution et le débogage de projets éblouissants. Dans Visual Studio pour Mac 8,6 la prise en charge de la création, de la génération et de l’exécution des projets éblouissants webassembly a été ajoutée.

Dans la procédure pas à pas ci-dessus, nous avons vu comment le modèle de projet d’application de serveur éblouissant vous aide à créer un projet d’application de serveur éblouissant. Jetons un coup d’œil à certaines des fonctionnalités supplémentaires de Visual Studio pour Mac pour prendre en charge le développement de projets éblouissant.

### <a name="editor-support-for-razor-files"></a>Prise en charge de l’éditeur pour les fichiers *. Razor*
Visual Studio pour Mac prend en charge la modification des fichiers. Razor, majoritairement des fichiers que vous allez utiliser lors de la création d’applications éblouissantes. La version Windows et Mac de l’IDE partagent le même éditeur pour les fichiers. Razor. Vous verrez la prise en charge complète de la colorisation et de la saisie semi-automatique de vos fichiers. Razor, notamment les saisies semi-automatiques des composants Razor déclarés dans le projet.

![Fenêtre de l’éditeur de Visual Studio pour Mac avec IntelliSense pour éblouissant](media/blazor-intellisense.png)

### <a name="publishing-blazor-applications-to-azure-app-service"></a>Publication d’applications éblouissantes à Azure App Service
Vous pouvez également publier des applications éblouissantes directement sur Azure App Service. Si vous ne disposez pas d’un compte Azure pour exécuter votre application éblouissante sur Azure, vous pouvez toujours vous [inscrire gratuitement](https://azure.microsoft.com/free) sur 12 mois, $200 crédits Azure gratuits et plus de 25 services gratuits toujours gratuits.

![Visual Studio pour Mac avec l’expérience de publication Azure](media/blazor-azure-publish.png)

## <a name="project-anatomy"></a>Anatomie du projet

Les applications Web éblouissantes incluent quelques répertoires et fichiers par défaut. Au cours de votre mise en route, Voici les principaux que vous devez connaître :

### <a name="pages-folder"></a>Dossier Pages

Ce dossier contient les pages Web d’un projet, qui utilisent une extension de fichier *. Razor* .

### <a name="shared-folder"></a>Dossier partagé

Ce dossier comprend des composants partagés, également à l’aide de l’extension *. Razor* . Vous verrez que cela comprend *MainLayout. Razor*, qui est utilisé pour définir une disposition commune à travers l’application. Il comprend également le composant partagé *NavMenu. Razor* , qui est utilisé sur toutes les pages. Si vous créez des composants réutilisables, ceux-ci sont placés dans le dossier **partagé** .

### <a name="app-settings"></a>Paramètres de l’application

Le *appSettings.js* fichier contient des données de configuration telles que des chaînes de connexion.

Pour plus d’informations sur la configuration, consultez la section [configuration dans ASP.net Guide](/aspnet/core/fundamentals/configuration/index).

### <a name="wwwroot-folder"></a>Dossier racine

Ce dossier contient des fichiers statiques, tels que des fichiers HTML, JavaScript et CSS. Pour plus d’informations, consultez [Fichiers statiques dans ASP.NET Core](/aspnet/core/fundamentals/static-files).

### <a name="programcs"></a>Program.cs

Ce fichier contient le point d’entrée du programme. Pour plus d’informations, consultez [Hôte web ASP.NET Core](/aspnet/core/fundamentals/host/web-host).

### <a name="startupcs"></a>Startup.cs

Ce fichier contient le code qui configure le comportement de l’application, par exemple si l’application requiert le consentement des cookies. Pour plus d’informations, consultez [Start-up de l’application dans ASP.NET Core](/aspnet/core/fundamentals/startup).

## <a name="summary"></a>Résumé
Dans ce didacticiel, vous avez vu comment créer une application de serveur éblouissante dans Visual Studio pour Mac et découvert certaines des fonctionnalités que Visual Studio pour Mac propose pour vous aider à créer des applications éblouissantes.

## <a name="see-also"></a>Voir aussi

Pour obtenir un guide plus complet sur la création d’applications Web éblouissantes, consultez [Présentation de ASP.net Core éblouissant](/aspnet/core/blazor/index).
