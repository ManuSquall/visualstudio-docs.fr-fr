---
title: Créer des applications Web Razor
description: Fournit des informations sur le support Razor dans ASP.NET applications Core dans Visual Studio pour Mac.
author: sayedihashimi
ms.author: sayedha
ms.date: 05/03/2018
ms.technology: vs-ide-general
ms.assetid: F898CB6E-05ED-44CD-8DB6-427B2592CCC6
ms.openlocfilehash: fe9ef921ccfc42b77bd08925805aeac6f4aec777
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2020
ms.locfileid: "73715873"
---
# <a name="create-razor-web-apps"></a>Créer des applications Web Razor

Ce guide offre une introduction à la création de votre première application Web Razor. Pour des conseils plus approfondis, voir [Introduction to Razor Pages dans ASP.NET Core](/aspnet/core/razor-pages/index).

Visual Studio pour Mac prend en charge la modification Razor, notamment IntelliSense et la coloration syntaxique dans les fichiers *.cshtml*. Nouveau dans Visual Studio 2019 pour Mac 8.3 est la possibilité d’avoir le contexte conscient IntelliSense dans un fichier Razor, de sorte que vous recevez IntelliSense qui correspond à la langue que vous modifiez actuellement dans un document.

![Modification Razor dans Visual Studio pour Mac](media/razor-2019.png)

## <a name="creating-a-new-razor-project"></a>Création d’un nouveau projet Razor

1. Sur l’écran d’accueil, sélectionnez **Nouveau** pour créer un nouveau projet :

   ![Nouveau projet Visual Studio pour Mac](media/razor-new.png)
1. Dans la nouvelle boîte de dialogue **project,** **rendez-vous** > sur .NET Core**App** > **Web Application** et sélectionnez **Next**:

   ![Modèle de projet Razor](media/razor-new-project1.png)
1. Sélectionnez votre cadre cible .NET Core (nous recommandons la version 2.2 ou plus tard), puis sélectionnez **Next**. Choisissez un nom pour votre projet et ajoutez le support Git si nécessaire. Sélectionnez **Créer** pour créer le projet.

   ![Nom du projet Razor](media/razor-new-project2.png)

   Visual Studio pour Mac ouvre votre projet dans la fenêtre de mise en page Code.
1. Exécuter le projet sans débogage en utilisant **Command-Option-F5**.

   Visual Studio démarre [Kestrel](/aspnet/core/fundamentals/servers/kestrel), `https://localhost:5001`ouvre un navigateur à , et affiche votre première application Web Razor.

   ![Application web Razor dans Safari](media/razor-webapp.png)

## <a name="project-anatomy"></a>Anatomie du projet

Les applications Web Razor incluent les composants suivants.

### <a name="pages-folder"></a>Dossier Pages

Ce dossier contient les pages Web d’un projet, ainsi que le code-behind pour chacun :
   - Un fichier * \*.cshtml* pour la balisage HTML et la syntaxe Razor.
   - Un fichier * \*.cshtml.cs* pour votre code C pour le traitement des événements de la page.

Les fichiers de prise en charge ont des noms commençant par un trait de soulignement. Par exemple, le fichier _Layout.cshtml configure des éléments d’interface utilisateur communs à toutes les pages. Ce fichier définit le menu de navigation en haut de la page et l’avis de copyright en bas. Pour plus d’informations, consultez [Disposition dans ASP.NET Core](/aspnet/core/mvc/views/layout).

### <a name="launch-settings"></a>Paramètres de lancement

Le *fichier launchSettings.json* contient les paramètres DE l’IIS, l’URL de l’application et d’autres paramètres connexes.

### <a name="app-settings"></a>Paramètres de l’application

Le fichier *appSettings.json* contient des données de configuration telles que des chaînes de connexion.

Pour plus d’informations sur la configuration, voir la [configuration dans ASP.NET guide](/aspnet/core/fundamentals/configuration/index).

### <a name="wwwroot-folder"></a>Dossier racine

Ce dossier contient des fichiers statiques, tels que les fichiers HTML, JavaScript et CSS. Pour plus d’informations, consultez [Fichiers statiques dans ASP.NET Core](/aspnet/core/fundamentals/static-files).

### <a name="programcs"></a>Program.cs

Ce fichier contient le point d’entrée pour le programme. Pour plus d’informations, consultez [Hôte web ASP.NET Core](/aspnet/core/fundamentals/host/web-host).

### <a name="startupcs"></a>Startup.cs

Ce fichier contient du code qui configure le comportement de l’application, par exemple si l’application nécessite le consentement pour les cookies. Pour plus d’informations, consultez [Start-up de l’application dans ASP.NET Core](/aspnet/core/fundamentals/startup).

## <a name="see-also"></a>Voir aussi

Pour un guide plus complet pour créer des applications Web Razor, voir [Introduction to Razor Pages in ASP.NET Core](/aspnet/core/razor-pages/index).
