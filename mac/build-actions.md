---
title: Actions de génération
description: Cet article décrit les différentes actions de génération que vous pouvez utiliser dans le cadre de projets C#
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.openlocfilehash: d089f38bd91eda2565f215e8d15a74cc119b8767
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "73714404"
---
# <a name="build-actions"></a>Actions de génération

Tous les fichiers d’un projet Visual Studio pour Mac ont une action de génération. L’action de génération contrôle ce qui se passe au fichier pendant une génération. 

>[!NOTE]
>Cette rubrique s’applique à Visual Studio pour Mac. Pour Visual Studio sur Windows, consultez [actions de génération](/visualstudio/ide/build-actions).

## <a name="set-a-build-action"></a>Définir une action de génération

Pour définir une action de génération pour un fichier dans Visual Studio pour Mac, vous pouvez cliquer avec le bouton droit sur n’importe quel fichier et accéder à l' **action de génération**, comme illustré ci-dessous :

![Sélection de l’action de génération Compiler dans l’Explorateur de solutions](media/projects-and-solutions-image1.png)

Les actions de génération pour ce fichier s’affichent dans le menu contextuel. 

## <a name="build-action-values"></a>Valeurs des actions de génération

Voici quelques-unes des actions de génération courantes pour les projets que vous pouvez générer dans Visual Studio pour Mac incluent :

|Action de génération | Types de projet | Description |
|--|--|--|
| **Compiler** | n'importe laquelle | Le fichier est passé au compilateur C# en tant que fichier source.|
| **Contenu** | .NET, Xamarin | Pour les projets ASP.NET, ces fichiers sont ajoutés pour faire partie du site au moment de son déploiement. Pour les projets Xamarin.iOS et Xamarin.Mac, ils sont inclus dans le bundle d’applications.|
| **Ressource incorporée** | .NET | Le fichier est passé au compilateur C# en tant que ressource à incorporer dans l’assembly. [Assembly.GetManifestResourceStream](/dotnet/api/system.reflection.assembly.getmanifestresourcestream), de l’espace de noms `System.Reflection`, peut ensuite être utilisé pour lire le fichier à partir de l’assembly.|
| **Aucun** | n'importe laquelle | Le fichier ne fait pas partie de la build et est inclus dans le projet pour faciliter l’accès à partir de l’IDE. Cette valeur peut être utilisée pour les fichiers de documentation tels que les fichiers « Lisez-moi ».|

> [!NOTE]
> D’autres actions de génération peuvent être définies pour des types de projet spécifiques. Par conséquent, la liste des actions de génération dépend du type de projet et des valeurs, qui ne figurent pas dans cette liste, peuvent apparaître.  

Les projets Xamarin.iOS ont l’action de génération **BundleResource**, qui ajoute le fichier au bundle d’applications. Pour plus d’informations sur les actions de génération spécifiques à Xamarin.Android, consultez le guide relatif au [processus de génération](/xamarin/android/deploy-test/building-apps/build-process#Build_Actions).

Il est également possible de sélectionner plusieurs fichiers dans l’Explorateur de solutions, ce qui vous permet de définir l’action de génération sur plusieurs fichiers à la fois.

## <a name="see-also"></a>Voir aussi

- [Actions de génération (Visual Studio sur Windows)](/visualstudio/ide/build-actions)