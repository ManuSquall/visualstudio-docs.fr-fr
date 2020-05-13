---
title: lancementSettings.json support
description: Ce document couvre le support pour le lancementSettings.json dans Visual Studio pour Mac
author: sayedihashimi
ms.author: sayedha
ms.date: 09/18/2019
ms.assetid: a556f9d7-86a8-408e-aa54-392584845889
ms.openlocfilehash: d35bfed901dca960ae21b4e2cf2fa75067c1b3ee
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2020
ms.locfileid: "73715932"
---
# <a name="launchsettingsjson"></a>launchSettings.json

Lorsque vous développez ASP.NET projets Core, vous pouvez configurer comment votre projet doit être lancé dans des scénarios de développement en personnalisant le contenu du fichier launchSettings.json. Dans Visual Studio pour Mac, vous pouvez mettre à jour ce fichier en utilisant l’interface utilisateur des options de projet ou en l’éditant directement. Ce fichier est le même fichier de configuration que vous pouvez utiliser `dotnet`lors de l’exécution visual Studio sur Windows ou de la ligne de commande à travers . Ce fichier est stocké dans votre projet sous le dossier Propriétés.

Pour plus d’informations, voir [Utilisez plusieurs environnements dans ASP.NET Core](/aspnet/core/fundamentals/environments). Dans cet article, nous allons couvrir la façon de mettre à jour ce fichier dans Visual Studio pour Mac.

## <a name="update-the-start-configuration-by-using-visual-studio-for-mac"></a>Mettre à jour la configuration de départ en utilisant Visual Studio pour Mac

Vous pouvez modifier directement le fichier launchSettings.json dans Visual Studio pour Mac, ou vous pouvez utiliser les options de projet pour le modifier. Pour en arriver aux options de projet, cliquez à droite sur votre projet et sélectionnez **Options**.

![Menu raccourci de projet avec "Options" sélectionné](media/vsmac-ctx-proj-options.png)

Sélectionnez**Configurations** >  **d’exécution** > **Par défaut**.

!["Run", "Configurations" et "Default" dans les options de projet](media/vsmac-run-config-default.png)

Principalement, vous configurerez deux choses ici :

 - Variables d'environnement
 - URL de l’application pour le projet

## <a name="configure-environment-variables"></a>Configuration des variables d’environnement

Vous pouvez utiliser la grille pour spécifier des valeurs pour les variables de l’environnement. Ces variables d’environnement seront définies lorsque vous commencerez votre application dans Visual Studio pour Mac. Lorsque vous développez ASP.NET applications Core, vous devez être `ASPNETCORE_ENVIRONMENT` conscient de la variable d’environnement spéciale. Pour en savoir plus, voir [Utilisez plusieurs environnements dans ASP.NET Core](/aspnet/core/fundamentals/environments).


## <a name="configure-the-start-url"></a>Configurer l’URL de démarrage

Pour configurer l’URL avec laquelle l’application sera commencée, **rendez-vous sur l’onglet ASP.NET Core.**

![URL d’application dans les options de projet](media/vsmac-run-config-default-aspnetcore.png)

Ici, vous pouvez spécifier l’URL que l’application écoutera sur quand il est commencé.