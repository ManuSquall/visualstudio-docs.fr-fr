---
title: prise en charge de launchSettings. JSON
description: Ce document couvre la prise en charge de launchSettings. JSON dans Visual Studio pour Mac
author: sayedihashimi
ms.author: sayedha
ms.date: 09/18/2019
ms.assetid: a556f9d7-86a8-408e-aa54-392584845889
ms.openlocfilehash: 7135dd05c687e3caed3ee64618ff71c093f4cd63
ms.sourcegitcommit: 4d2620bee4688fb881e09a07ea4a264b99f0743e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71322581"
---
# <a name="launchsettingsjson"></a>launchSettings. JSON

Lorsque vous développez des projets ASP.NET Core, vous pouvez configurer le mode de démarrage de votre projet dans les scénarios de développement en personnalisant le contenu du fichier launchSettings. JSON. Dans Visual Studio pour Mac, vous pouvez mettre à jour ce fichier à l’aide de l’interface utilisateur options du projet ou en le modifiant directement. Ce fichier est le même que celui que vous pouvez utiliser lors de l’exécution de Visual Studio sur Windows ou à partir `dotnet`de la ligne de commande. Ce fichier est stocké dans votre projet sous le dossier Propriétés.

Pour plus d’informations, consultez [utiliser plusieurs environnements dans ASP.net Core](https://docs.microsoft.com/aspnet/core/fundamentals/environments). Dans cet article, nous allons aborder la mise à jour de ce fichier dans Visual Studio pour Mac.

## <a name="update-the-start-configuration-by-using-visual-studio-for-mac"></a>Mettre à jour la configuration de démarrage à l’aide de Visual Studio pour Mac

Vous pouvez modifier directement le fichier launchSettings. JSON dans Visual Studio pour Mac, ou vous pouvez utiliser les options de projet pour le modifier. Pour accéder aux options du projet, cliquez avec le bouton droit sur votre projet et sélectionnez **options**.

![Menu contextuel du projet avec l’option « Options » sélectionnée](media/vsmac-ctx-proj-options.png)

Sélectionnez > lesconfigurationsde > série de tests**par défaut**.

![« Run », « configurations » et « default » dans les options du projet](media/vsmac-run-config-default.png)

En premier lieu, vous configurerez deux choses :

 - Variables d’environnement
 - URL de l’application pour le projet

## <a name="configure-environment-variables"></a>Configurer des variables d’environnement

Vous pouvez utiliser la grille pour spécifier des valeurs pour les variables d’environnement. Ces variables d’environnement seront définies lorsque vous démarrerez votre application dans Visual Studio pour Mac. Lorsque vous développez des applications ASP.net Core, vous devez être conscient de la `ASPNETCORE_ENVIRONMENT` variable d’environnement spéciale. Pour plus d’informations, consultez [utiliser plusieurs environnements dans ASP.net Core](https://docs.microsoft.com/aspnet/core/fundamentals/environments).


## <a name="configure-the-start-url"></a>Configurer l’URL de démarrage

Pour configurer l’URL avec laquelle l’application sera démarrée, accédez à l’onglet **ASP.net Core** .

![URL de l’application dans les options du projet](media/vsmac-run-config-default-aspnetcore.png)

Ici, vous pouvez spécifier l’URL que l’application doit écouter au démarrage.