---
title: prise en charge de launchSettings. JSON
description: Ce document couvre la prise en charge de launchSettings. JSON dans Visual Studio pour Mac
author: sayedihashimi
ms.author: sayedha
ms.date: 09/18/2019
ms.assetid: a556f9d7-86a8-408e-aa54-392584845889
ms.openlocfilehash: e7de368dd26bf2724a7bc060dade46422817da1e
ms.sourcegitcommit: ea182703e922c74725045afc251bcebac305068a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71213758"
---
# <a name="launchsettingsjson"></a>launchSettings. JSON

Lorsque vous développez des projets ASP.net Core, vous pouvez configurer le mode de démarrage de votre projet dans les scénarios de développement en `launchSettings.json` personnalisant le contenu du fichier. Dans Visual Studio pour Mac, vous pouvez mettre à jour ce fichier à l’aide de l’interface utilisateur options du `launchSettings.json` projet ou en modifiant directement le fichier. Ce fichier est le même fichier de configuration qui peut être utilisé lors de l’exécution de Visual Studio sur Windows ou à `dotnet`partir de la ligne de commande à l’aide de. Ce fichier est stocké dans votre projet sous `Properties` le dossier.

Pour obtenir des informations plus détaillées, vous pouvez [utiliser plusieurs environnements dans ASP.net Core](https://docs.microsoft.com/aspnet/core/fundamentals/environments). Dans ce document, nous allons aborder la mise à jour de ce fichier dans Visual Studio pour Mac.

## <a name="updating-start-configuration-using-visual-studio-for-mac"></a>Mise à jour de la configuration de démarrage à l’aide de Visual Studio pour Mac

Vous pouvez modifier directement le `launchSettings.json` dans Visual Studio pour Mac ou vous pouvez utiliser les options de projet pour le modifier. Pour accéder aux options du projet, cliquez avec le bouton droit sur votre projet et sélectionnez Options. Consultez l’image ci-dessous.

![options du menu contextuel du projet sélectionnées](media/vsmac-ctx-proj-options.png)

Une fois que vous accédez à cette boîte de dialogue, accédez à exécuter > configurations > par défaut.

![valeurs par défaut des configurations d’exécution](media/vsmac-run-config-default.png)

Il existe principalement deux choses que vous allez configurer ici.

 - Variables d’environnement qui sont définies au démarrage
 - URL de démarrage du projet

## <a name="configure-environment-variables"></a>Configurer des variables d’environnement

Vous pouvez utiliser la grille pour spécifier des valeurs pour les variables d’environnement. Ces variables d’environnement seront définies lorsque vous démarrerez votre application dans Visual Studio pour Mac. Lorsque vous développez des applications ASP.net Core, vous devez être conscient `ASPNETCORE_ENVIRONMENT` de la variable d’environnement spéciale. Pour plus d’informations, consultez [utiliser plusieurs environnements dans ASP.net Core](https://docs.microsoft.com/aspnet/core/fundamentals/environments).


## <a name="configure-start-url"></a>Configurer l’URL de démarrage

Pour configurer l’URL à laquelle l’application sera lancée, accédez à l’onglet ASP.NET Core.

![URL de début des options du proj](media/vsmac-run-config-default-aspnetcore.png)

Ici, vous pouvez spécifier la ou les URL que l’application doit écouter au démarrage.