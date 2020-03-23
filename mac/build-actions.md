---
title: Actions de génération
description: Cet article décrit les différentes actions de génération que vous pouvez utiliser dans le cadre de projets C#
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.openlocfilehash: d089f38bd91eda2565f215e8d15a74cc119b8767
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2020
ms.locfileid: "73714404"
---
# <a name="build-actions"></a>Actions de génération

Tous les fichiers d’un projet Visual Studio pour Mac ont une action de génération. L’action de construction contrôle ce qui arrive au fichier pendant une build. 

>[!NOTE]
>Cette rubrique s’applique à Visual Studio pour Mac. Pour Visual Studio sur Windows, voir [actions Build](/visualstudio/ide/build-actions).

## <a name="set-a-build-action"></a>Définir une action de génération

Pour définir une action de build pour un fichier dans Visual Studio pour Mac, vous pouvez cliquer à droite sur n’importe quel fichier et naviguer pour **construire l’action**, comme illustré ci-dessous:

![Sélection de l’action de génération Compiler dans l’Explorateur de solutions](media/projects-and-solutions-image1.png)

Les actions de construction pour ce fichier seront affichées dans le menu flyout. 

## <a name="build-action-values"></a>Valeurs des actions de génération

Voici quelques-unes des actions de construction communes pour des projets que vous pouvez construire dans Visual Studio for Mac :

|Action de génération | Types de projet | Description |
|--|--|--|
| **Compiler** | n'importe laquelle | Le fichier est transmis au compilateur Cmd comme fichier source.|
| **Contenu** | .NET, Xamarin | Pour les projets ASP.NET, ces fichiers sont ajoutés pour faire partie du site au moment de son déploiement. Pour les projets Xamarin.iOS et Xamarin.Mac, ils sont inclus dans le bundle d’applications.|
| **Ressource incorporée** | .NET | Le fichier est transmis au compilateur Cmd comme une ressource à intégrer dans l’assemblage. [Assembly.GetManifestResourceStream](/dotnet/api/system.reflection.assembly.getmanifestresourcestream), de l’espace de noms `System.Reflection`, peut ensuite être utilisé pour lire le fichier à partir de l’assembly.|
| **Aucun** | n'importe laquelle | Le fichier ne fait pas partie de la construction en aucune façon et est inclus dans le projet pour un accès facile à partir de l’IDE. Cette valeur peut être utilisée pour les fichiers de documentation tels que les fichiers « Lisez-moi ».|

> [!NOTE]
> D’autres actions de génération peuvent être définies pour des types de projet spécifiques. Par conséquent, la liste des actions de génération dépend du type de projet et des valeurs, qui ne figurent pas dans cette liste, peuvent apparaître.  

Les projets Xamarin.iOS ont l’action de génération **BundleResource**, qui ajoute le fichier au bundle d’applications. Pour plus d’informations sur les actions de génération spécifiques à Xamarin.Android, consultez le guide relatif au [processus de génération](/xamarin/android/deploy-test/building-apps/build-process#Build_Actions).

Il est également possible de sélectionner plus d’un fichier dans l’explorateur de la solution, vous permettant de définir l’action de construction à de nombreux fichiers à la fois.

## <a name="see-also"></a>Voir aussi

- [Actions de génération (Visual Studio sur Windows)](/visualstudio/ide/build-actions)