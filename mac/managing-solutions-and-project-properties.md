---
title: "Gestion des propriétés des projets et des solutions | Microsoft Docs"
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 75247EB8-323A-4AFD-A451-6703A03D5D1F
ms.openlocfilehash: 8871ab002a94a9c0bbc0063a25b4dea9cb271142
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="managing-project-and-solution-properties"></a>Gestion des propriétés des projets et des solutions

## <a name="project-options"></a>Options de projet

Les options de projet sont spécifiques à chaque projet, et affectent la façon dont le projet est écrit, généré et exécuté. Ceci contraste avec les préférences de Visual Studio pour Mac, qui définissent des options spécifiques à l’utilisateur, et avec les options des solutions, qui définissent des options pour l’ensemble de la solution. Les options de projet sont stockées dans le fichier projet (.csproj), de façon que les autres développeurs puissent créer et exécuter le projet correctement. Ceci permet à de nombreux développeurs de travailler sur le même document sans compromettre la mise en forme du fichier.

Vous pouvez accéder aux options de projet dans Visual Studio pour Mac en double-cliquant sur le nom du projet, ou en cliquant avec le bouton droit pour ouvrir le menu contextuel et en sélectionnant **Options** :

 ![Option dans le menu contextuel](media/projects-and-solutions-image2.png)

Les options modifiables sont notamment celles qui sont utilisées pour générer, exécuter et définir le code source, ainsi que les options de gestion de versions.

Les options de projet sont organisées en cinq catégories différentes, qui ont les fonctionnalités suivantes :

* **Général** : les informations du projet, comme le nom, la description et l’espace de noms par défaut, peuvent être définies ici, ainsi que l’emplacement du projet.
* **Build** : ces options permettent aux développeurs de définir ou de modifier des profils PCL pour les bibliothèques de classes portables. Elles permettent également de définir des commandes, des configurations et des options de compilateur personnalisées. Le chemin de sortie et le nom des assemblys peuvent également être définis ici.
* **Exécuter** : vous permet de créer des configurations de séries de tests personnalisées par projet.
* **Code source** : vous permet de contrôler la mise en forme de nombreux types de fichiers différents et les conventions de nommage. Vous pouvez également définir ici les stratégies de nommage et les styles d’en-tête par défaut.
* **Gestion de version** : vous permet de modifier le style du message de validation lors de l’utilisation de la gestion de versions avec votre projet.

Chaque projet peut également contenir des options de projet spécifiques qui dépendent de la plateforme. Par exemple, un projet Xamarin.Android, comme celui qui est illustré ci-dessous, a des options relatives à la génération Android, comme les options de l’éditeur de liens, et à l’application, comme les autorisations :

 ![Options de projet Android](media/projects-and-solutions-image5.png)

Xamarin.iOS contient des options relatives à la signature des bundles, comme le profil d’approvisionnement nécessaire à utiliser, et des options relatives à l’empaquetage IPA :

 ![Options de projet iOS](media/projects-and-solutions-image6.png)

## <a name="solution-options"></a>Options de la solution 

Les options de solution sont similaires aux options de projet, mais elles couvrent les solutions entières. Elles permettent de définir les informations sur l’auteur, les paramètres de génération, les styles de mise en forme du code et la gestion de versions, et d’affecter le projet de démarrage dans la solution.  La boîte de dialogue Options de la solution est accessible à partir de l’élément de menu **Projet > Options de la solution**, à partir de l’élément de menu contextuel **Options** sur la solution dans le panneau Solution, ou en double-cliquant sur la solution dans le panneau Solution :

 ![Options de la solution](media/projects-and-solutions-image7.png)
