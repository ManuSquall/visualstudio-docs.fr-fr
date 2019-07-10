---
title: Actions de génération
description: Cet article décrit les différentes actions de génération que vous pouvez utiliser dans le cadre de projets C#
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.openlocfilehash: 54e341b4e5961623f41963bb90c2e5d60b110cf4
ms.sourcegitcommit: 7fbfb2a1d43ce72545096c635df2b04496b0be71
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67691196"
---
# <a name="build-actions"></a>Actions de génération

Tous les fichiers d’un projet Visual Studio pour Mac ont une action de génération. Elle contrôle le traitement du fichier pendant une build. Vous pouvez définir ce comportement en cliquant avec le bouton droit sur un fichier et en accédant à **Action de génération**, comme illustré ci-dessous :

![Sélection de l’action de génération Compiler dans l’Explorateur de solutions](media/projects-and-solutions-image1.png)

Voici quelques-unes des actions de génération courantes pour les projets C# :

* **Aucune** - Le fichier ne fait pas partie de la build, il est inclus dans le projet uniquement pour faciliter l’accès à partir de l’IDE.
* **Compiler** : le fichier est passé comme fichier source au compilateur C#.
* **EmbeddedResource** : le fichier est passé au compilateur C# comme ressource à incorporer dans l’assembly. [Assembly.GetManifestResourceStream](https://docs.microsoft.com/dotnet/api/system.reflection.assembly.getmanifestresourcestream), de l’espace de noms `System.Reflection`, peut ensuite être utilisé pour lire le fichier à partir de l’assembly.
* **Contenu** : pour les projets ASP.NET, ces fichiers sont ajoutés pour faire partie du site lors de son déploiement. Pour les projets Xamarin.iOS et Xamarin.Mac, ils sont inclus dans le bundle d’applications.

Il est possible de sélectionner plusieurs fichiers dans l’Explorateur de solutions, ce qui vous permet de définir l’action de génération pour de nombreux fichiers à la fois.

Des actions de génération existent également pour des projets spécifiques. Les projets Xamarin.iOS ont l’action de génération **BundleResource**, qui ajoute le fichier au bundle d’applications. Pour plus d’informations sur les actions de génération spécifiques à Xamarin.Android, consultez le guide relatif au [processus de génération](/xamarin/android/deploy-test/building-apps/build-process#Build_Actions).

## <a name="see-also"></a>Voir aussi

- [Actions de génération (Visual Studio sur Windows)](/visualstudio/ide/build-actions)