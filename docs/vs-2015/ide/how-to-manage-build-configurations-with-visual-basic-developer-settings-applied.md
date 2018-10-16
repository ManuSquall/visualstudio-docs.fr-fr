---
title: Guide pratique pour gérer des configurations de build en appliquant les paramètres du développeur Visual Basic | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio, building with Visual Basic settings
- MSBuild, debug build
- advanced build configurations
- building with Visual Basic developer settings
- debug builds
- MSBuild, release build
- release builds
ms.assetid: eaea6e0b-6c61-4869-8d63-d372c745a23c
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b191b5d4223d32e4d620c779f5813c0db651a6cc
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49300558"
---
# <a name="how-to-manage-build-configurations-with-visual-basic-developer-settings-applied"></a>Guide pratique pour gérer des configurations de build en appliquant les paramètres du développeur Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Par défaut, toutes les options de configuration de build avancées sont masquées si les paramètres du développeur [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] sont appliqués. Cette rubrique explique comment activer manuellement ces paramètres.  
  
## <a name="enabling-advanced-build-configurations"></a>Activation des configurations de build avancées  
 Par défaut, les paramètres du développeur [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] masquent l’option pour ouvrir la boîte de dialogue **Gestionnaire de configurations** et les listes **Configuration** et **Plateforme** dans le [Concepteur de projets](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).  
  
#### <a name="to-enable-advanced-build-configurations"></a>Pour activer les configurations de build avancées  
  
1.  Dans le menu **Outils** , cliquez sur **Options**.  
  
2.  Développez **Projets et solutions** et cliquez sur **Général**.  
  
    > [!NOTE]
    >  Le nœud **Général** est visible même si l’option **Afficher tous les paramètres** est désactivée. Si vous souhaitez afficher toutes les options disponibles, cliquez sur **Afficher tous les paramètres**.  
  
3.  Cliquez sur **Afficher les configurations de build avancées**.  
  
4.  Cliquez sur **OK**.  
  
     Dans le menu **Générer**, le **Gestionnaire de configurations** est maintenant disponible, et les listes **Configuration** et **Plateforme** sont visibles dans le Concepteur de projets.  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation des configurations de build](../ide/understanding-build-configurations.md)   
 [Compilation et génération](../ide/compiling-and-building-in-visual-studio.md)



