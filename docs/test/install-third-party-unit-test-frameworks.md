---
title: Installer des frameworks de tests unitaires tierces | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 47893b70-46f8-49dc-84bd-ec820178f683
caps.latest.revision: "10"
ms.author: douge
manager: douge
ms.openlocfilehash: 343935b46b17f876b6bde65d3bd1547069447730
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="install-third-party-unit-test-frameworks"></a>Installer des frameworks de tests unitaires tierces
L'Explorateur de tests Visual Studio peut exécuter n'importe quel framework de tests unitaires ayant développé une interface d'adaptateur pour l'Explorateur. Le programme d'installation du framework installe les fichiers binaires et ajoute des modèles de projet Visual Studio pour les langages qu'il prend en charge. Lorsque vous créez un projet avec le modèle, le framework est inscrit avec l'Explorateur de tests. Une solution Visual Studio peut contenir des projets de test unitaire qui utilisent des frameworks différents et qui sont destinés à des langages différents. L'Explorateur de tests les exécute tous.  
  
 **Requirements**  
  
-   Visual Studio Enterprise, Visual Studio Professional  
  
## <a name="acquiring-third-party-frameworks"></a>Obtention de frameworks tiers  
 Vous pouvez télécharger et installer plusieurs frameworks de test unitaire tiers avec le gestionnaire d’extensions de Visual Studio ou à partir de Visual Studio Marketplace. Il est également possible de télécharger des frameworks à partir d'autres sites tels que le site web du framework.  
  
### <a name="installing-from-visual-studio"></a>Installation à partir de Visual Studio  
  
1.  Choisissez **Outils** dans le menu standard, puis choisissez **Extensions et mises à jour**.  
  
2.  Développez **En ligne**, **Visual Studio Marketplace**, **Outils**. Choisissez **Test**.  
  
3.  Parcourez la liste pour rechercher le framework.  
  
4.  Sélectionnez le framework, puis choisissez **Télécharger**.  
  
 Pour plus d’informations, consultez [Recherche et utilisation des extensions Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).  
  
### <a name="installing-from-the-web"></a>Installation à partir du web  
 Si vous savez quel framework vous intéresse :  
  
1.  Ouvrez [Visual Studio Marketplace ](https://marketplace.visualstudio.com/vs).  
  
2.  Tapez le nom du framework dans la zone **Rechercher**.  
  
3.  Choisissez le framework dans la liste des résultats pour accéder à la page de Visual Studio Marketplace correspondant à l’outil.  
  
 Pour parcourir la liste des frameworks ainsi que d'autres outils de test :  
  
1.  Ouvrez [Visual Studio Marketplace ](https://marketplace.visualstudio.com/vs).  
  
2.  Dans **Filtrer par catégorie/collection**, choisissez **Tout afficher**.  
  
3.  Dans la liste **Catégorie** (libellée **Affichage**), développez le nœud **Outils**, puis choisissez **Test**.  
  
4.  Choisissez un framework dans la liste des résultats pour accéder à la page de Visual Studio Marketplace correspondant à l’outil.  
  
## <a name="see-also"></a>Voir aussi  
 [Tests unitaires sur votre code](../test/unit-test-your-code.md)
