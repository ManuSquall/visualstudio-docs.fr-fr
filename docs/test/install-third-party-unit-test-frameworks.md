---
title: "Installer des infrastructures de tests unitaires tierces | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 47893b70-46f8-49dc-84bd-ec820178f683
caps.latest.revision: 10
ms.author: "mlearned"
manager: "douge"
caps.handback.revision: 10
---
# Installer des infrastructures de tests unitaires tierces
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'Explorateur de tests Visual Studio peut exécuter n'importe quelle infrastructure de tests unitaires ayant développé une interface d'adaptateur pour l'Explorateur.  Le programme d'installation de l'infrastructure installe les fichiers binaires et ajoute des modèles de projet Visual Studio pour les langages qu'il prend en charge.  Lorsque vous créez un projet avec le modèle, l'infrastructure est inscrite avec l'Explorateur de tests.  Une solution Visual Studio peut contenir des projets de test unitaire qui utilisent des infrastructures différentes et qui sont destinés à des langages différents.  L'Explorateur de tests les exécute tous.  
  
 **Spécifications**  
  
-   Visual Studio Enterprise, Visual Studio Professional  
  
## Obtention d'infrastructures tierces  
 Vous pouvez télécharger et installer plusieurs infrastructures de test unitaire tierces à l'aide du gestionnaire d'extensions de Visual Studio ou à partir de la galerie Visual Studio sur le site web MSDN.  Il est également possible de télécharger des infrastructures à partir d'autres sites tels que le site web de l'infrastructure.  
  
### Installation à partir de Visual Studio  
  
1.  Choisissez **Outils** dans le menu standard, puis choisissez **Extensions et mises à jour**.  
  
2.  Développez **En ligne**, **Galerie Visual Studio**, **Outils**.  Choisissez **Test**.  
  
3.  Parcourez la liste pour rechercher l'infrastructure.  
  
4.  Sélectionnez l'infrastructure, puis choisissez **Télécharger**.  
  
 Pour plus d'informations, consultez [Recherche et utilisation des extensions Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).  
  
### Installation à partir du web  
 Si vous savez quelle infrastructure vous intéresse :  
  
1.  Ouvrez la [Galerie Visual Studio](http://go.microsoft.com/fwlink/?LinkId=236267) sur le site web MSDN.  
  
2.  Tapez le nom de l'infrastructure dans la zone **Rechercher**.  
  
3.  Choisissez l'infrastructure dans la liste des résultats pour accéder à la page de la galerie Visual Studio correspondant à l'outil.  
  
 Pour parcourir la liste des infrastructures ainsi que d'autres outils de test :  
  
1.  Ouvrez la [Galerie Visual Studio](http://go.microsoft.com/fwlink/?LinkId=236267) sur le site web MSDN.  
  
2.  Choisissez **Parcourir**.  
  
3.  Dans la liste **Catégorie**, développez le nœud **Outils**, puis choisissez **Test**.  
  
4.  Choisissez une infrastructure dans la liste des résultats pour accéder à une page de la galerie Visual Studio correspondant à l'outil.  
  
## Voir aussi  
 [Tests unitaires sur votre code](../test/unit-test-your-code.md)