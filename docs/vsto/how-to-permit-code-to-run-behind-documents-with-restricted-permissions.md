---
title: "Comment&#160;: permettre au code de s&#39;ex&#233;cuter derri&#232;re des documents dot&#233;s d&#39;autorisations restreintes | Microsoft Docs"
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
  - "code (développement Office dans Visual Studio), exécuter derrière des documents restreints"
  - "documents (développement Office dans Visual Studio), autorisations restreintes"
  - "Gestion des droits relatifs à l'information (développement Office dans Visual Studio)"
  - "IRM (développement Office dans Visual Studio)"
  - "documents Office (développement Office dans Visual Studio), autorisations restreintes"
  - "autorisations (développement Office dans Visual Studio)"
ms.assetid: d037eae5-cf83-4be0-85ba-05e9f7d570e1
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Comment&#160;: permettre au code de s&#39;ex&#233;cuter derri&#232;re des documents dot&#233;s d&#39;autorisations restreintes
  Vous pouvez utiliser la fonctionnalité Gestion des droits relatifs à l'information \(IRM\) de Microsoft Office pour restreindre les autorisations d'accès à un document ou un classeur.  Par défaut, le code sous\-jacent d'un document Microsoft Office Word ou d'un classeur Microsoft Office Excel restreint ne peut pas s'exécuter.  Vous pouvez modifier la valeur par défaut de sorte que vos extensions de code managé accèdent au modèle objet ; dès lors, votre solution pourra fonctionner.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Vous devez être l'auteur du document ou classeur, ou bien disposer d'un accès avec contrôle total pour pouvoir modifier les paramètres d'autorisation.  
  
### Pour permettre à du code d'être exécuté à partir de documents avec autorisations restreintes  
  
1.  Ouvrez le document ou le classeur dans Word ou Excel.  
  
2.  Cliquez sur l'onglet **Fichier** , pointez sur **préparez**, pointez sur **Restreindre l'autorisation**, puis cliquez sur **Accès restreint**.  
  
    > [!NOTE]  
    >  Lors de la première utilisation, vous êtes invité à installer le client Windows Rights Management.  Après avoir installé ce client, vous devrez peut\-être répéter les étapes.  
  
3.  Dans la boîte de dialogue **Autorisation**, sélectionnez **Restreindre l'autorisation à ce document**, puis cliquez sur **Autres options**.  
  
4.  Sous **Autorisations supplémentaires aux utilisateurs**, sélectionnez **Accéder au contenu via un programme**.  
  
 Word ou Excel permettront l'accès par programmation au modèle objet.  
  
## Voir aussi  
 [Vue d'ensemble de la gestion des droits relatifs à l'information et des extensions de code managé](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Protection des documents dans les solutions au niveau du document](../vsto/document-protection-in-document-level-solutions.md)   
 [Protection par mot de passe des documents Office](../vsto/password-protection-on-office-documents.md)   
 [Conception et création de solutions Office](../vsto/designing-and-creating-office-solutions.md)   
 [Sécurisation des solutions Office](../vsto/securing-office-solutions.md)   
 [Déploiement d'une solution Office](../vsto/deploying-an-office-solution.md)  
  
  