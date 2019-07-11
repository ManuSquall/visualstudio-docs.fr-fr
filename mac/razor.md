---
title: Razor
description: Informations sur la prise en charge de Razor dans les applications ASP.NET Core dans Visual Studio pour Mac
author: sayedihashimi
ms.author: sayedha
ms.date: 05/03/2018
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: F898CB6E-05ED-44CD-8DB6-427B2592CCC6
ms.openlocfilehash: 9e5a3f61ee7065a0615a381bdcc03dafc3566893
ms.sourcegitcommit: 7fbfb2a1d43ce72545096c635df2b04496b0be71
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67691266"
---
# <a name="razor"></a>Razor

Visual Studio pour Mac prend en charge la modification Razor, notamment IntelliSense et la coloration syntaxique dans les fichiers *.cshtml*.

![Modification Razor dans Visual Studio pour Mac](media/razor-editor.png)

Ce guide fournit une introduction à la création de votre première application web Razor. Pour obtenir un guide détaillé, consultez le [Pages Razor dans la documentation .NET Core](/aspnet/core/razor-pages/index).

## <a name="creating-a-new-razor-project"></a>Création d’un nouveau projet Razor

* Sur l’écran d’accueil, sélectionnez **Nouveau** pour créer un nouveau projet :

![Nouveau projet Visual Studio pour Mac](media/razor-new.png)

* Dans la boîte de dialogue Nouveau projet, accédez à **.NET Core** > **Application** > **Application web** et sélectionnez le bouton **Suivant** :

![Modèle de projet Razor](media/razor-new-project1.png)

* Sélectionnez votre version cible de .Net Framework nécessaire (version recommandée 2.2 ou version ultérieure) et sélectionnez **Suivant**.  Choisissez un nom pour votre projet et ajoutez le support git si nécessaire. Sélectionnez **Créer** pour créer le projet.

![Nom du projet Razor](media/razor-new-project2.png)

Visual Studio pour Mac ouvre votre projet dans la disposition du Code.

* Exécutez le projet sans débogage à l’aide de **Cmd-Opt-F5**

Visual Studio démarre [Kestral](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel) et lance un navigateur pour `https://localhost:5001` et affiche votre première application web Razor :

![Application web Razor dans Safari](media/razor-webapp.png)

## <a name="project-anatomy"></a>Anatomie du projet

Les applications web Razor comprennent les composants suivants :

### <a name="pages-folder"></a>Dossier Pages

Vous trouverez les pages web dans le dossier Pages au sein du projet, ainsi que le code-behind pour chacun :
* Un fichier * *.cshtml* pour la balise HTML et la syntaxe Razor.
* Un fichier * *.cshtml.cs* pour votre code-behind C# pour gérer des événements de page.

Les fichiers de prise en charge ont des noms commençant par un trait de soulignement. Par exemple, le fichier _Layout.cshtml configure des éléments d’interface utilisateur communs à toutes les pages. Ce fichier définit le menu de navigation en haut de la page et la mention de copyright au bas de la page. Pour plus d’informations, consultez [Disposition dans ASP.NET Core](https://docs.microsoft.com/aspnet/core/mvc/views/layout).

### <a name="launch-settings"></a>Paramètres de lancement

Le fichier *launchSettings.json* contient les paramètres IIS, l’URL de l’application et d’autres paramètres connexes.

### <a name="app-settings"></a>Paramètres de l’application

Le fichier *appSettings.json* contient des données de configuration, comme les chaînes de connexion.

Pour plus d’informations sur la configuration, consultez le [guide Configuration dans ASP.NET](https://docs.microsoft.com/aspnet/core/fundamentals/configuration/index).

### <a name="wwwroot-folder"></a>Dossier racine

Contient des fichiers statiques, tels que les fichiers HTML, JavaScript et CSS. Pour plus d’informations, consultez [Fichiers statiques dans ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/static-files).

### <a name="programcs"></a>Program.cs

Contient le point d’entrée pour le programme. Pour plus d’informations, consultez [Hôte web ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/host/web-host).

### <a name="startupcs"></a>Startup.cs

Contient le code qui configure le comportement de l’application, comme le fait qu’elle exige un consentement pour les cookies. Pour plus d’informations, consultez [Start-up de l’application dans ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/startup).

## <a name="see-aso"></a>Consultez également

Pour obtenir un guide plus complet sur la création d’applications web Razor consultez [Introduction à Razor Pages dans ASP.NET Core](https://docs.microsoft.com/aspnet/core/razor-pages/index).
