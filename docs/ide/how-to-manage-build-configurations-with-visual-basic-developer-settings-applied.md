---
title: "Guide pratique pour gérer des configurations de build en appliquant les paramètres du développeur Visual Basic | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
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
caps.latest.revision: 9
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 782d860d94cd9e7d4967076a5ea0d3fe86b29400
ms.contentlocale: fr-fr
ms.lasthandoff: 05/24/2017

---
# <a name="how-to-manage-build-configurations-with-visual-basic-developer-settings-applied"></a>Guide pratique pour gérer des configurations de build en appliquant les paramètres du développeur Visual Basic
Par défaut, toutes les options de configuration de build avancées sont masquées si les paramètres du développeur [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] sont appliqués. Cette rubrique explique comment activer manuellement ces paramètres.  
  
## <a name="enabling-advanced-build-configurations"></a>Activation des configurations de build avancées  
 Par défaut, les paramètres du développeur [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] masquent l’option pour ouvrir la boîte de dialogue **Gestionnaire de configurations** et les listes **Configuration** et **Plateforme** dans le [Concepteur de projets](..//ide/reference/application-page-project-designer-visual-basic.md).  
  
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
