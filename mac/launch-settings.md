---
title: Prise en charge de launchSettings.json
description: Ce document couvre la prise en charge de launchSettings.jsdans Visual Studio pour Mac
author: sayedihashimi
ms.author: sayedha
ms.date: 09/18/2019
ms.assetid: a556f9d7-86a8-408e-aa54-392584845889
ms.openlocfilehash: df702b5d49e5204e65675c1c57d222e490a33824
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88247927"
---
# <a name="launchsettingsjson"></a>launchSettings.json

Lorsque vous développez des projets ASP.NET Core, vous pouvez configurer le mode de démarrage de votre projet dans les scénarios de développement en personnalisant le contenu du launchSettings.jssur le fichier. Dans Visual Studio pour Mac, vous pouvez mettre à jour ce fichier à l’aide de l’interface utilisateur options du projet ou en le modifiant directement. Ce fichier est le même que celui que vous pouvez utiliser lors de l’exécution de Visual Studio sur Windows ou à partir de la ligne de commande `dotnet` . Ce fichier est stocké dans votre projet sous le dossier Propriétés.

Pour plus d’informations, consultez [utiliser plusieurs environnements dans ASP.net Core](/aspnet/core/fundamentals/environments). Dans cet article, nous allons aborder la mise à jour de ce fichier dans Visual Studio pour Mac.

## <a name="update-the-start-configuration-by-using-visual-studio-for-mac"></a>Mettre à jour la configuration de démarrage à l’aide de Visual Studio pour Mac

Vous pouvez modifier directement le launchSettings.jssur le fichier dans Visual Studio pour Mac, ou vous pouvez utiliser les options de projet pour le modifier. Pour accéder aux options du projet, cliquez avec le bouton droit sur votre projet et sélectionnez **options**.

![Menu contextuel du projet avec l’option « Options » sélectionnée](media/vsmac-ctx-proj-options.png)

Sélectionnez les configurations de **série de tests**  >  **Configurations**  >  **par défaut**.

![« Run », « configurations » et « default » dans les options du projet](media/vsmac-run-config-default.png)

En premier lieu, vous configurerez deux choses :

- Variables d'environnement
- URL de l’application pour le projet

## <a name="configure-environment-variables"></a>Configuration des variables d’environnement

Vous pouvez utiliser la grille pour spécifier des valeurs pour les variables d’environnement. Ces variables d’environnement seront définies lorsque vous démarrerez votre application dans Visual Studio pour Mac. Lorsque vous développez des applications ASP.NET Core, vous devez être conscient de la `ASPNETCORE_ENVIRONMENT` variable d’environnement spéciale. Pour plus d’informations, consultez [Utilisation de plusieurs environnements dans ASP.NET Core](/aspnet/core/fundamentals/environments).


## <a name="configure-the-start-url"></a>Configurer l’URL de démarrage

Pour configurer l’URL avec laquelle l’application sera démarrée, accédez à l’onglet **ASP.net Core** .

![URL de l’application dans les options du projet](media/vsmac-run-config-default-aspnetcore.png)

Ici, vous pouvez spécifier l’URL que l’application doit écouter au démarrage.
