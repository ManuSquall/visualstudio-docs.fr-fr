---
title: "Actions de génération"
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.openlocfilehash: 347378da197b5c6d22bbd145c2ac8673d53a63bf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="build-actions"></a>Actions de génération 

Tous les fichiers d’un projet Visual Studio pour Mac ont une action de génération qui détermine comment ils sont traités pendant une génération. Vous pouvez définir ces actions en cliquant avec le bouton droit sur n’importe quel fichier et en accédant à **Action de génération**, comme illustré ci-dessous :

![](media/projects-and-solutions-image1.png)

Voici quelques-unes des actions de génération courantes pour les projets C# :

* **Aucune** : le fichier ne fait en rien partie de la génération, il est dans le projet seulement pour un accès facile à partir de l’IDE.
* **Compiler** : le fichier est passé comme fichier source au compilateur C#.
* **EmbeddedResource** : le fichier est passé au compilateur C# comme ressource à incorporer dans l’assembly. L’espace de noms `System.Reflection` peut ensuite être utilisé pour lire le fichier à partir de l’assembly.
* **Contenu** : pour les projets ASP.NET, ces fichiers sont ajoutés pour faire partie du site lors de son déploiement. Pour les projets Xamarin.iOS et Xamarin.Mac, ils sont intégrés au bundle de l’application.

Il est possible de sélectionner plusieurs fichiers dans l’Explorateur de solutions, ce qui vous permet de définir l’action de génération pour de nombreux fichiers à la fois.

Des actions de génération existent également pour des projets spécifiques. Par exemple, les projets Xamarin.iOS ont l’action de génération **BundeledResource**, qui ajoute le fichier au bundle de l’application. Pour plus d’informations sur les actions de génération spécifiques à Xamarin.Android, consultez le guide [Build Process](https://developer.xamarin.com/guides/android/under_the_hood/build_process/#Build_Actions) sur le site developer.xamarin.com.