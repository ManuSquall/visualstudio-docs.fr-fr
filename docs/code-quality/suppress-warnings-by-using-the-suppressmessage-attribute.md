---
title: "Supprimer des avertissements &#224; l&#39;aide de l&#39;attribut SuppressMessage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCFxCopTool.InputAssemblyFileName"
  - "VC.Project.VCFxCopTool.FxCopModuleSuppressionsFile"
  - "VC.Project.VCFxCopTool.FxCopUseTypeNameInSuppression"
  - "VC.Project.VCFxCopTool.OutputFile"
helpviewer_keywords: 
  - "analyse du code, suppression de la source"
  - "analyse du code, SuppressMessage (attribut)"
  - "suppression de la source"
  - "SuppressMessage (attribut)"
ms.assetid: a38c57a2-d29d-43c0-84ff-3308b2484ce6
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# Supprimer des avertissements &#224; l&#39;aide de l&#39;attribut SuppressMessage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il est souvent utile d'indiquer que l'avertissement ne peut pas être utilisé pour informer les membres de l'équipe que le code a été révisé et qu'il en est ressorti que l'avertissement doit être supprimé.  ISS \(In Source Suppression\) permet à un développeur de placer l'attribut qui supprime un avertissement près de l'emplacement de génération de l'avertissement.  Vous pouvez ajouter directement l'attribut ISS au fichier source, ou vous pouvez utiliser le menu contextuel dans l'IDE de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Dans cette section  
  
|||  
|-|-|  
|[Vue d’ensemble de la suppression à la source](../code-quality/in-source-suppression-overview.md)|Pour en savoir plus sur ISS sur son utilisation dans votre code.|  
|[Comment : supprimer des avertissements à l’aide de l’élément de menu](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)|Apprenez comment supprimer les avertissements dans l'IDE de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] à l'aide du menu contextuel.|  
  
## Rubriques connexes  
 [Analyse de la qualité d’un code managé](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)