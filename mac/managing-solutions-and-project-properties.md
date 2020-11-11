---
title: Gestion des propriétés des projets et des solutions
description: Cet article explique comment gérer les propriétés des projets et des solutions dans Visual Studio pour Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/09/2020
ms.assetid: 75247EB8-323A-4AFD-A451-6703A03D5D1F
ms.openlocfilehash: 0c3277df3be22658acf85a4f0607ed9ad0308b5c
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94492995"
---
# <a name="managing-project-and-solution-properties"></a>Gestion des propriétés des projets et des solutions

## <a name="project-options"></a>Options de projet

Les options de projet sont spécifiques à chaque projet, et affectent la façon dont le projet est écrit, généré et exécuté. Contrairement à Visual Studio pour Mac préférences qui sont des paramètres spécifiques à l’utilisateur, les options de projet sont stockées dans le fichier projet (. csproj), afin que d’autres développeurs puissent générer et exécuter le projet correctement. Le fait de disposer d’options de projet spécifiques permet à de nombreux développeurs de travailler sur le même document sans compromettre la mise en forme du fichier.

Pour ouvrir les options de projet dans Visual Studio pour Mac, double-cliquez sur le nom du projet, ou cliquez avec le bouton droit afin d’ouvrir le menu contextuel, puis sélectionnez **Options**  :

![Option dans le menu contextuel](media/projects-and-solutions-image2.png)

Les options modifiables incluent les options utilisées pour générer, exécuter et définir le code source ainsi que la gestion de versions.

Les options de projet sont organisées en cinq catégories différentes :

* **Général**  : les informations du projet, comme le nom, la description et l’espace de noms par défaut, sont définies ici, ainsi que l’emplacement du projet.
* **Build** : utilisé pour définir ou modifier des profils PCL pour les bibliothèques de classes portables. Elles permettent également de définir des commandes, des configurations et des options de compilateur personnalisées. Le chemin de sortie et le nom des assemblys peuvent également être définis ici.
* **Exécuter** : permet de créer des configurations d’exécution personnalisées pour chaque projet.
* **Code source** : contrôle la mise en forme de nombreux types de fichiers et conventions de nommage différents. Vous pouvez également définir ici les stratégies de nommage et les styles d’en-tête par défaut.
* **Contrôle de version** -options pour définir le style des messages de validation lors de l’utilisation du contrôle de version avec votre projet.

Chaque projet peut contenir des options de projet spécifiques qui dépendent de la plateforme. Par exemple, un projet Xamarin.Android, comme celui qui est illustré dans l’image suivante, a des options relatives à la build Android (par exemple les options d’éditeur de liens), et à l’application (par exemple les autorisations) :

![Options de projet Android](media/projects-and-solutions-image5.png)

Xamarin.iOS contient des options relatives à la signature des bundles, comme le profil d’approvisionnement nécessaire à utiliser :

![Options de projet iOS](media/projects-and-solutions-image6.png)

## <a name="solution-options"></a>Options de la solution

Les options de solution sont similaires aux options de projet, mais elles couvrent les solutions entières. Elles permettent de définir les informations sur l’auteur, les paramètres de génération, les styles de mise en forme du code et la gestion de versions, et d’affecter le projet de démarrage dans la solution.  Vous pouvez accéder à la boîte de dialogue Options de la solution à partir de l’élément de menu **projet > options** de la solution, à partir de l’élément de menu contextuel **options** de la solution dans la fenêtre de la solution, ou en double-cliquant sur la solution dans la fenêtre de la solution :

![Options de la solution](media/projects-and-solutions-image7.png)

## <a name="see-also"></a>Voir aussi

* [Gérer les propriétés des projets et des solutions (Visual Studio sur Windows)](/visualstudio/ide/managing-project-and-solution-properties)