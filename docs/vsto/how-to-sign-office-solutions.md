---
title: "Comment&#160;: signer des solutions Office | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "certificats (développement Office dans Visual Studio), solutions Office"
  - "sécurité (développement Office dans Visual Studio), signer des solutions Office"
  - "signer des manifestes (développement Office dans Visual Studio)"
ms.assetid: d3df5ee6-f1b7-47ed-b7ee-8985679ee3af
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Comment&#160;: signer des solutions Office
  En signant une solution, vous pouvez accorder un niveau de confiance à la solution en utilisant le certificat en guise de preuve.  Vous pouvez utiliser un même certificat pour plusieurs solutions. Toutes les solutions seront approuvées sans mises à jour de stratégie de sécurité supplémentaires.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Si vous modifiez manuellement les manifestes d'application et de déploiement à l'aide de l'outil Manifest Generation and Editing \(mage.exe et mageui.exe\), vous devez signer de nouveau les manifestes avant de pouvoir les utiliser.  Pour plus d’informations, consultez [How to: Re-sign Application and Deployment Manifests](../Topic/How%20to:%20Re-sign%20Application%20and%20Deployment%20Manifests.md).  
  
## Signature à l'aide d'un certificat  
 Un certificat est un fichier qui contient une clé unique et l'identité de l'éditeur de la solution.  Vous pouvez acheter des certificats auprès d'une autorité de certification ou créer votre propre certificat et le faire signer par une autorité de certification.  
  
 Visual Studio signe des solutions Office avec un certificat temporaire pour permettre le débogage.  Vous ne devez pas utiliser le certificat temporaire comme preuve dans des solutions déployées.  
  
#### Pour signer une solution Office à l'aide d'un certificat  
  
1.  Dans le menu **Projet**, cliquez sur **Propriétés** *NomSolution*.  
  
2.  Cliquez sur l'onglet **Signature**.  
  
3.  Sélectionnez **Signer les manifestes ClickOnce**.  
  
4.  Localisez le certificat en cliquant sur **À partir du magasin** ou **À partir d'un fichier** et en naviguant jusqu'au certificat.  
  
5.  Pour vérifier que le certificat approprié est utilisé, cliquez sur **Plus de détails** afin de consulter les informations de certificat.  
  
## Voir aussi  
 [Sécurisation des solutions Office](../vsto/securing-office-solutions.md)   
 [Octroi de niveaux de confiance à des solutions Office](../vsto/granting-trust-to-office-solutions.md)   
 [Page Signature, Concepteur de projets](../ide/reference/signing-page-project-designer.md)  
  
  