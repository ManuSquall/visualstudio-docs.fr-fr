---
title: "Comment&#160;: ajouter et supprimer des fonctionnalit&#233;s et des &#233;l&#233;ments dans un package &#224; l&#39;aide de l&#39;Explorateur de package | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.RAD.PackagingExplorer"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "développement SharePoint dans Visual Studio, packages"
ms.assetid: 549d5848-f0c9-42c6-b7f5-bc1e626a30e6
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Comment&#160;: ajouter et supprimer des fonctionnalit&#233;s et des &#233;l&#233;ments dans un package &#224; l&#39;aide de l&#39;Explorateur de package
  Pour configurer un package en vue de déployer des éléments et des fonctionnalités SharePoint, servez\-vous de l'Explorateur de package.  Vous pouvez peaufiner les éléments de projet et les fonctionnalités SharePoint à l'intérieur de votre fichier .wsp.  
  
 Vous disposez également d'un outil très pratique \(Concepteur de packages\) pour examiner et réorganiser les fonctionnalités lorsque vous souhaitez modifier l'ordre d'activation.  Pour plus d'informations, consultez [Comment : ajouter et supprimer des fonctionnalités et des éléments dans un package à l'aide du Concepteur de packages](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).  
  
## Ouverture de l'Explorateur de package  
 Procédez de la façon suivante pour ouvrir l'Explorateur de package, si votre solution Visual Studio comporte au moins un projet SharePoint.  Vous pouvez également accéder automatiquement à l'Explorateur de package en ouvrant un Concepteur de fonctionnalités ou un Concepteur de packages.  De la même manière, il suffit de fermer tous les concepteurs de fonctionnalités et de packages pour quitter l'Explorateur de package.  
  
#### Pour ouvrir l'Explorateur de package  
  
1.  Dans la barre de menus, choisissez **Afficher**, **Autres fenêtres**, **Explorateur de package**.  
  
     L'**Explorateur de package** apparaît dans la **Boîte à outils**.  
  
## Ajout d'une fonctionnalité à un package  
 L'Explorateur de package permet de compléter un package par des fonctionnalités nouvelles ou déjà créées.  
  
#### Pour ajouter une fonctionnalité SharePoint  
  
1.  Ouvrez l'**Explorateur de package**, ouvrez le menu contextuel du projet, puis sélectionnez **Ajouter un composant**.  
  
#### Pour déplacer une fonctionnalité SharePoint existante  
  
1.  Ouvrez **Explorateur de package**, puis effectuez l'une des opérations suivantes :  
  
    -   Faites glisser un **composant** d'un projet dans un autre projet.  
  
    -   Ouvrez le menu contextuel pour un composant, choisissez **Couper**, ouvrez le menu contextuel du projet dans lequel vous souhaitez déplacer le composant, puis choisissez **Coller**.  
  
    > [!NOTE]  
    >  Utilisez de préférence cette procédure si votre solution est constituée de plusieurs projets SharePoint.  
  
## Validation d'une fonctionnalité ou d'un package  
 Vous pouvez identifier des problèmes potentiels dans les fonctionnalités et les packages SharePoint en validant les fichiers.  Les avertissements et les erreurs sont affichés dans la fenêtre Sortie et dans la fenêtre Liste d'erreurs.  
  
#### Pour valider une fonctionnalité ou un package SharePoint  
  
1.  Ouvrez l'**Explorateur de package**.  
  
2.  Ouvrez un menu contextuel pour un composant ou un package, puis sélectionnez **Validation**.  
  
## Voir aussi  
 [Empaquetage et déploiement de solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  