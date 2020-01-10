---
title: Créer des applications Web éblouissantes
description: Fournit des informations sur la prise en charge de éblouissants dans les applications ASP.NET Core dans Visual Studio pour Mac.
author: jongalloway
ms.author: jogallow
ms.date: 12/17/2019
ms.technology: vs-ide-general
ms.assetid: D2717D3A-9225-40A8-8155-7D0143B2CA60
ms.openlocfilehash: dbc49a0ea9b4e4fa7880b6226331d447339b6575
ms.sourcegitcommit: d04441e3c5f2eff3a63f7aca35ccf7ecac90fb44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737585"
---
# <a name="create-blazor-web-apps"></a>Créer des applications Web éblouissantes

Ce guide propose une introduction à la création de votre première application Web éblouissante. Pour obtenir des conseils détaillés, consultez [Introduction à ASP.net Core éblouissant](/aspnet/core/blazor/index).

Visual Studio pour Mac (à partir de la version 8,4) prend en charge le développement et la publication d’ASP.NET Core applications serveur éblouissantes. Éblouissant est une infrastructure permettant de créer une interface utilisateur Web interactive côté client avec .NET, qui offre les avantages suivants aux développeurs Web :

* Écriture de code dans C# plutôt que dans JavaScript.
* Tirez parti de l’écosystème .NET existant des bibliothèques .NET.
* Partagez la logique de l’application sur le serveur et le client.
* Tirer parti de. Performances, fiabilité et sécurité de NET.
* Restez productif avec Visual Studio sur PC, Linux et macOS.
* Développez avec un ensemble commun de langages, de frameworks et d’outils stables, riches en fonctionnalités et faciles à utiliser.

## <a name="creating-a-new-blazor-project"></a>Création d’un projet éblouissant

1. Dans la **fenêtre démarrer**, sélectionnez **nouveau** pour créer un nouveau projet :

   ![Visual Studio pour Mac la fenêtre de démarrage avec la nouvelle sélection mise en surbrillance](media/blazor-new-project.png)
1. Dans la boîte de dialogue **nouveau projet** , sélectionnez **.net Core** > **application** > **application de serveur éblouissant** , puis sélectionnez **suivant**: ![choisir un modèle pour votre boîte de dialogue Nouveau projet avec le modèle application serveur éblouissant sélectionné](media/blazor-project-template.png)

1. Sélectionnez .NET Core 3,1 comme Framework cible, puis sélectionnez **suivant**. 
   ![configurer votre nouvelle boîte de dialogue d’application serveur éblouissante affichée avec la version cible de .NET Framework sélectionnée pour .NET Core 3,1](media/blazor-select-target-framework.png)

1. Choisissez un nom pour votre projet et ajoutez la prise en charge de git si vous le souhaitez. Sélectionnez **Créer** pour créer le projet.
   ![bConfiguration de la boîte de dialogue de votre nouvelle application serveur éblouissante lors de la saisie du nom du projet](media/blazor-name-project.png)

   Visual Studio pour Mac ouvre votre projet dans la fenêtre de mise en page du code.
1. Sélectionnez **exécuter** > **Démarrer sans débogage** pour exécuter l’application.

   Visual Studio démarre [Kestrel](/aspnet/core/fundamentals/servers/kestrel), ouvre un navigateur pour `https://localhost:5001`et affiche votre application Web éblouissante.

   ![Application Web éblouissante dans Safari](media/blazor-new-app-in-edge.png)

## <a name="blazor-support-in-visual-studio-for-mac"></a>Prise en charge des éblouissants dans Visual Studio pour Mac

Visual Studio pour Mac (à partir de la version 8,4) comprend de nouvelles fonctionnalités qui vous aideront à créer des projets de serveur éblouissants. En outre, il vous offre la prise en charge standard attendue, comme la génération, l’exécution et le débogage de projets éblouissants. 

Dans la procédure pas à pas ci-dessus, nous avons vu comment le modèle de projet d’application de serveur éblouissant vous aide à créer un projet d’application de serveur éblouissant. Jetons un coup d’œil à certaines des fonctionnalités supplémentaires de Visual Studio pour Mac pour prendre en charge le développement de projets de serveur éblouissant.

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

Le fichier *appSettings. JSON* contient des données de configuration telles que des chaînes de connexion.

Pour plus d’informations sur la configuration, consultez la section [configuration dans ASP.net Guide](/aspnet/core/fundamentals/configuration/index).

### <a name="wwwroot-folder"></a>Dossier racine

Ce dossier contient des fichiers statiques, tels que des fichiers HTML, JavaScript et CSS. Pour plus d’informations, consultez [Fichiers statiques dans ASP.NET Core](/aspnet/core/fundamentals/static-files).

### <a name="programcs"></a>Program.cs

Ce fichier contient le point d’entrée du programme. Pour plus d’informations, consultez [Hôte web ASP.NET Core](/aspnet/core/fundamentals/host/web-host).

### <a name="startupcs"></a>Startup.cs

Ce fichier contient le code qui configure le comportement de l’application, par exemple si l’application requiert le consentement des cookies. Pour plus d’informations, consultez [Start-up de l’application dans ASP.NET Core](/aspnet/core/fundamentals/startup).

## <a name="summary"></a>Récapitulatif
Dans ce didacticiel, vous avez vu comment créer une application de serveur éblouissante dans Visual Studio pour Mac et découvert certaines des fonctionnalités que Visual Studio pour Mac propose pour vous aider à créer des applications éblouissantes.

## <a name="see-also"></a>Voir aussi

Pour obtenir un guide plus complet sur la création d’applications Web éblouissantes, consultez [Présentation de ASP.net Core éblouissant](/aspnet/core/blazor/index).
