---
title: Actions de génération
description: Cet article décrit les différentes actions de génération que vous pouvez utiliser dans le cadre de projets C#
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.openlocfilehash: 889414d391a4a894879399317d782df58a8bacb3
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33865004"
---
# <a name="build-actions"></a>Actions de génération

Tous les fichiers d’un projet Visual Studio pour Mac ont une action de génération qui détermine comment ils sont traités pendant une génération. Vous pouvez définir ces actions en cliquant avec le bouton droit sur n’importe quel fichier et en accédant à **Action de génération**, comme illustré ci-dessous :

![Sélection de l’action de génération Compiler dans l’Explorateur de solutions](media/projects-and-solutions-image1.png)

Voici quelques-unes des actions de génération courantes pour les projets C# :

* **Aucune** : le fichier ne fait en rien partie de la génération, il est dans le projet seulement pour un accès facile à partir de l’IDE.
* **Compiler** : le fichier est passé comme fichier source au compilateur C#.
* **EmbeddedResource** : le fichier est passé au compilateur C# comme ressource à incorporer dans l’assembly. L’espace de noms `System.Reflection` peut ensuite être utilisé pour lire le fichier à partir de l’assembly.
* **Contenu** : pour les projets ASP.NET, ces fichiers sont ajoutés pour faire partie du site lors de son déploiement. Pour les projets Xamarin.iOS et Xamarin.Mac, ils sont intégrés au bundle de l’application.

Il est possible de sélectionner plusieurs fichiers dans l’Explorateur de solutions, ce qui vous permet de définir l’action de génération pour de nombreux fichiers à la fois.

Des actions de génération existent également pour des projets spécifiques. Par exemple, les projets Xamarin.iOS ont l’action de génération **BundleResource**, qui ajoute le fichier au bundle de l’application. Pour plus d’informations sur les actions de génération spécifiques à Xamarin.Android, consultez le guide relatif au [processus de génération](/xamarin/android/deploy-test/building-apps/build-process#Build_Actions).