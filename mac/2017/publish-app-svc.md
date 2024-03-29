---
title: Publier sur Azure App Service
description: Vous pouvez utiliser l’outil Publier pour publier des applications ASP.NET Core sur Azure App Service.
ms.date: 01/17/2019
helpviewer_keywords:
- deployment, website
ms.assetid: 8524a4c5-97a9-41ac-a2a0-034efb9bfc57
author: sayedihashimi
ms.author: sayedha
manager: unniravindranathan
ms.prod: visual-studio-mac
ms.custom: video
ms.topic: how-to
ms.workload:
- azure
ms.openlocfilehash: e0fdabe38f2696540db1a3b629609dbc1c42d821
ms.sourcegitcommit: 155d5f0fd54ac1d20df2f5b0245365924faa3565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/31/2021
ms.locfileid: "106083627"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio-for-mac"></a>Publier une application web sur Azure App Service à l’aide de Visual Studio pour Mac

Vous pouvez utiliser l’outil Publier pour publier des applications ASP.NET Core sur Azure App Service.

## <a name="prerequisites"></a>Prérequis

- [Visual Studio 2017 pour Mac](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs4mac2017) installé et ASP.NET Core activé.
- Un abonnement Azure. Si vous n’avez pas encore d’abonnement, [inscrivez-vous gratuitement](https://azure.microsoft.com/free/dotnet/) et bénéficiez de 200 $ de crédit pendant 30 jours et de 12 mois de services gratuits.
- Un projet ASP.NET Core. Si vous n’avez pas encore de projet, vous pouvez en [créer un](./create-new-projects.md?view=vsmac-2017&preserve-view=true).

## <a name="publish-to-azure-app-service"></a>Publier sur Azure App Service

 1. Dans le panneau Solutions, cliquez avec le bouton droit sur le projet, puis choisissez **Publier**.

    ![Menu contextuel de publication](media/publish-context-menu.png)

 2. Si vous avez déjà publié ce projet sur Azure App Service, vous voyez le profil de publication apparaître dans le menu. Sélectionnez ce profil de publication pour démarrer le processus de publication.

 3. Pour publier ce projet sur App Service pour la première fois, sélectionnez **Publier sur Azure**.

    ![Menu contextuel de publication sur App Service](media/publish-to-azure-context-menu.png)

 4. La boîte de dialogue **Publier sur Azure App Service** apparaît, et les services d’application existants sont affichés. Pour publier sur un service d’application existant, sélectionnez-le dans la liste, puis cliquez sur **Publier**.

    ![Boîte de dialogue Publier sur Azure App Service](media/publish-to-app-service-dialog.png)

 5. Pour créer un service d’application, cliquez sur le bouton **Nouveau**.

    ![Boîte de dialogue de publication sur App Service](media/publish-to-app-service-dialog-new-selected.png)

 6. La boîte de dialogue **Nouvel App Service** apparaît. Dans cette boîte de dialogue, vous pouvez configurer les paramètres de votre nouveau service d’application.

    ![Boîte de dialogue Nouvel App Service](media/publish-new-app-service.png)

    Il existe ici quelques options que vous pouvez personnaliser. Le nom du service d’application correspond par défaut au nom du projet. Si le nom n’est pas disponible, un signe d’avertissement s’affiche à droite du champ d’entrée. Le nom du service d’application est utilisé dans l’URL de votre site web. Ce nom doit donc être valide pour pouvoir être utilisé dans une URL.

    Vous pouvez changer l’abonnement auquel le service d’application est associé à l’aide de la liste déroulante **Abonnement**.

    Vous pouvez sélectionner un **groupe de ressources** existant à l’aide de la liste déroulante ou en créer un autre à l’aide du bouton **+**.

    Pour le plan App Service, sélectionnez un plan existant, ou créez-en un en sélectionnant la case d’option **Personnalisé**.

    Pour créer votre service d’application et y publier votre projet, cliquez sur **Créer**.

    Une fois que vous avez cliqué sur **Créer**, la boîte de dialogue **Nouvel App Service** se ferme, et le message suivant s’affiche pour vous indiquer que la création du service d’application a démarré.

      ![Message de création de service App Service](media/publish-create-app-service-message.png)

    Une fois que vous avez cliqué sur **OK**, le message est ignoré, et vous pouvez continuer à travailler sur votre projet. Vous pouvez consulter l’état du processus de publication dans la barre d’état située en haut de l’IDE. Une fois votre application web publiée avec succès, le site s’ouvre dans votre navigateur par défaut.

## <a name="related-video"></a>Vidéo associée

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Publish-to-Azure/player]