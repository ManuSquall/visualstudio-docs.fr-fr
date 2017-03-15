---
title: "Comment&#160;: g&#233;rer des configurations de build en appliquant les param&#232;tres du d&#233;veloppeur Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "configurations de build avancées"
  - "générer avec des paramètres de développeur Visual Basic"
  - "versions debug"
  - "MSBuild, version debug"
  - "MSBuild, version release"
  - "versions release"
  - "Visual Studio, générer avec les paramètres de Visual Basic"
ms.assetid: eaea6e0b-6c61-4869-8d63-d372c745a23c
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# Comment&#160;: g&#233;rer des configurations de build en appliquant les param&#232;tres du d&#233;veloppeur Visual Basic
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Par défaut, toutes les options de configuration de build avancées sont masquées si les paramètres du développeur [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] sont appliqués.  Cette rubrique explique comment activer manuellement ces paramètres.  
  
## Activation des configurations de build avancées  
 Par défaut, les paramètres du développeur [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] masquent l'option pour ouvrir la boîte de dialogue **Gestionnaire de configurations** et les listes **Configuration** et **Plateforme** dans le [Concepteur de projets](http://msdn.microsoft.com/fr-fr/898dd854-c98d-430c-ba1b-a913ce3c73d7).  
  
#### Pour activer les configurations de build avancées  
  
1.  Dans le menu **Outils**, cliquez sur **Options**.  
  
2.  Développez **Projets et solutions**, et cliquez sur **Général**.  
  
    > [!NOTE]
    >  Le nœud **Général** est visible même si l'option **Afficher tous les paramètres** est désactivée.  Si vous souhaitez afficher toutes les options disponibles, cliquez sur **Afficher tous les paramètres**.  
  
3.  Cliquez sur **Afficher les configurations de build avancées**.  
  
4.  Cliquez sur **OK**.  
  
     Dans le menu **Générer**, le **Gestionnaire de configurations** est maintenant disponible, et les listes **Configuration** et **plateforme** sont visibles dans le Concepteur de projets.  
  
## Voir aussi  
 [Présentation des configurations de build](../ide/understanding-build-configurations.md)   
 [Génération d'applications dans Visual Studio](../ide/compiling-and-building-in-visual-studio.md)