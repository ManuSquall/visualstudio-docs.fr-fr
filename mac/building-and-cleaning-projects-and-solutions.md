---
title: Génération et nettoyage de projets et de solutions dans Visual Studio pour Mac
description: Cet article décrit comment générer un projet dans Visual Studio pour Mac
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.assetid: E4B6CB42-9FE2-43B9-93B7-BD4BD50518B1
ms.openlocfilehash: 686735df963f2cdb3f85e4328299b609d5fbe08d
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33876928"
---
# <a name="building-and-cleaning-projects-and-solutions"></a>Génération et nettoyage des projets et des solutions

Suivez les étapes décrites dans cet article pour savoir comment générer, regénérer et nettoyer votre solution et votre projet.

## <a name="to-build-rebuild-or-clean-an-entire-solution"></a>Pour générer, régénérer ou nettoyer une solution entière

Pour générer, regénérer ou nettoyer une solution entière :

1. Sélectionnez le nœud Solution dans le panneau Solution :

    ![Sélection du nœud de solution](media/compiling-and-building-image1.png)

2. Sélectionnez le Menu Générer dans la barre de menus et sélectionnez une des options suivantes :

    ![Sélection de l’élément de menu Générer tout](media/compiling-and-building-image2.png)

    * **Générer tout** : tente de générer tous les fichiers du projet qui ont été modifiés dans le projet depuis la build la plus récente.
    * **Régénérer tout** : nettoie la solution, puis la génère.
    * **Nettoyer tout** : supprime tous les produits de la génération de votre solution.



## <a name="to-build-or-rebuild-a-single-project"></a>Pour générer ou régénérer un projet unique

1. Dans le panneau Solution, sélectionnez le projet.

2. Dans la barre de menus, choisissez Générer, puis choisissez Générer[nom_projet], Régénérer[nom_projet] ou Nettoyer[nom_projet].


## <a name="to-stop-a-build"></a>Pour arrêter une génération

Pour arrêter une génération, cliquez sur le carré rouge dans la zone d’état :

 ![Cliquer sur le carré rouge pour arrêter la génération](media/compiling-and-building-image3.png)