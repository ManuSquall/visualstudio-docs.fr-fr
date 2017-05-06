---
title: "Comment&#160;: modifier une configuration de d&#233;ploiement SharePoint"
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
  - "VS.SharePointTools.Project.DeploymentConfig"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "développement SharePoint dans Visual Studio, déployer"
ms.assetid: bff1895b-d3fe-4ec0-ba91-f8884dc35957
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Comment&#160;: modifier une configuration de d&#233;ploiement SharePoint
  Vous pouvez créer une configuration de déploiement ou en modifier une qui existe déjà.  Vous avez la possibilité, par exemple, d'exécuter une étape particulière ou de changer l'ordre des étapes dans le processus de déploiement.  Il peut être intéressant de créer ou de modifier des configurations de déploiement dans la mesure où les configurations intégrées et ajoutées par programmation ne sont pas modifiables.  
  
## Création d'une configuration de déploiement SharePoint  
  
#### Pour créer une configuration de déploiement SharePoint  
  
1.  Dans l'**Explorateur de solutions**, sélectionnez un projet SharePoint puis, dans la barre de menu cliquez sur **Projet**, *ProjectName* puis sur **Propriétés**.  
  
2.  Dans l'onglet **SharePoint**, choisissez le bouton **Nouveau**.  
  
     La boîte de dialogue **Ajouter une configuration de déploiement** apparaît.  
  
3.  Dans la zone de texte **Nom**, donnez un nom à la configuration de déploiement.  
  
4.  Dans le volet **Étapes de déploiement disponibles**, sélectionnez les étapes que vous souhaitez ajouter à la configuration de déploiement, cliquez sur le bouton \(**\>**\), puis sur le bouton **OK**.  
  
    > [!NOTE]  
    >  Si vous avez configuré une commande de prédéploiement ou une commande de post\-déploiement, ces étapes s'exécutent à condition d'être ajoutées à une configuration de déploiement personnalisée.  
  
## Modification de la configuration de déploiement active  
  
#### Pour changer la configuration de déploiement active  
  
1.  Dans l'**Explorateur de solutions**, sélectionnez un projet SharePoint puis, dans la barre de menu cliquez sur **Projet**, *ProjectName* puis sur **Propriétés**.  
  
2.  Choisissez l'onglet **SharePoint**.  
  
3.  Dans la zone de liste **Configuration de déploiement active**, sélectionnez le nom de la configuration de déploiement que vous souhaitez utiliser.  
  
## Voir aussi  
 [Empaquetage et déploiement de solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  