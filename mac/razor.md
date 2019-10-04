---
title: Créer des applications Web Razor
description: Fournit des informations sur la prise en charge de Razor dans les applications ASP.NET Core dans Visual Studio pour Mac.
author: sayedihashimi
ms.author: sayedha
ms.date: 05/03/2018
ms.technology: vs-ide-general
ms.assetid: F898CB6E-05ED-44CD-8DB6-427B2592CCC6
ms.openlocfilehash: d9a9df56074cde8735b54c12bbbf15a79e727497
ms.sourcegitcommit: dc12a7cb66124596089f01d3e939027ae562ede9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71962923"
---
# <a name="create-razor-web-apps"></a>Créer des applications Web Razor

Ce guide propose une introduction à la création de votre première application Web Razor. Pour obtenir des conseils détaillés, consultez [Introduction à la Razor pages dans ASP.net Core](https://docs.microsoft.com/aspnet/core/razor-pages/index).

Visual Studio pour Mac prend en charge la modification Razor, notamment IntelliSense et la coloration syntaxique dans les fichiers *.cshtml*. Nouveauté de Visual Studio 2019 pour Mac 8.3 + est la possibilité d’utiliser IntelliSense avec contexte dans un fichier Razor, afin que vous receviez IntelliSense qui corresponde à la langue que vous êtes en train de modifier dans un document.

![Modification Razor dans Visual Studio pour Mac](media/razor-2019.png)

## <a name="creating-a-new-razor-project"></a>Création d’un nouveau projet Razor

1. Dans l’écran d’accueil, sélectionnez **nouveau** pour créer un nouveau projet :

   ![Nouveau projet Visual Studio pour Mac](media/razor-new.png)
1. Dans la boîte de dialogue **nouveau projet** , accédez à **.net Core**@no__t-**2**application  > **application Web** , puis sélectionnez **suivant**:

   ![Modèle de projet Razor](media/razor-new-project1.png)
1. Sélectionnez votre infrastructure cible .NET Core (nous vous recommandons la version 2,2 ou ultérieure), puis sélectionnez **suivant**. Choisissez un nom pour votre projet et ajoutez la prise en charge de git si nécessaire. Sélectionnez **créer** pour créer le projet.

   ![Nom du projet Razor](media/razor-new-project2.png)

   Visual Studio pour Mac ouvre votre projet dans la fenêtre de mise en page du code.
1. Exécutez le projet sans débogage à l’aide de la **commande + option + F5**.

   Visual Studio démarre [Kestrel](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), ouvre un navigateur pour `https://localhost:5001` et affiche votre première application Web Razor.

   ![Application web Razor dans Safari](media/razor-webapp.png)

## <a name="project-anatomy"></a>Anatomie du projet

Les applications Web Razor incluent les composants suivants.

### <a name="pages-folder"></a>Dossier Pages

Ce dossier contient les pages Web d’un projet, ainsi que le code-behind pour chaque :
   - Un fichier \* *. cshtml* pour le balisage HTML et syntaxe Razor.
   - Un fichier *\*.cshtml.cs* pour votre C# code-behind pour gérer les événements de page.

Les fichiers de prise en charge ont des noms commençant par un trait de soulignement. Par exemple, le fichier _Layout.cshtml configure des éléments d’interface utilisateur communs à toutes les pages. Ce fichier configure le menu de navigation en haut de la page et la mention de droits d’auteur en bas. Pour plus d’informations, consultez [Disposition dans ASP.NET Core](https://docs.microsoft.com/aspnet/core/mvc/views/layout).

### <a name="launch-settings"></a>Paramètres de lancement

Le fichier *launchSettings. JSON* contient les paramètres IIS, l’URL de l’application et d’autres paramètres associés.

### <a name="app-settings"></a>Paramètres de l’application

Le fichier *appSettings. JSON* contient des données de configuration telles que des chaînes de connexion.

Pour plus d’informations sur la configuration, consultez la section [configuration dans ASP.net Guide](https://docs.microsoft.com/aspnet/core/fundamentals/configuration/index).

### <a name="wwwroot-folder"></a>Dossier racine

Ce dossier contient des fichiers statiques, tels que des fichiers HTML, JavaScript et CSS. Pour plus d’informations, consultez [Fichiers statiques dans ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/static-files).

### <a name="programcs"></a>Program.cs

Ce fichier contient le point d’entrée du programme. Pour plus d’informations, consultez [Hôte web ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/host/web-host).

### <a name="startupcs"></a>Startup.cs

Ce fichier contient le code qui configure le comportement de l’application, par exemple si l’application requiert le consentement des cookies. Pour plus d’informations, consultez [Start-up de l’application dans ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/startup).

## <a name="see-also"></a>Voir aussi

Pour obtenir un guide plus complet sur la création d’applications Web Razor, consultez [Présentation de la Razor pages dans ASP.net Core](https://docs.microsoft.com/aspnet/core/razor-pages/index).
