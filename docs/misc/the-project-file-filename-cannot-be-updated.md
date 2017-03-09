---
title: "The project file &#39;&lt;filename&gt;&#39; cannot be updated | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.UpgradeErrors"
ms.assetid: ecd1e161-c51c-4aaa-ab80-8fc443bdad81
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The project file &#39;&lt;filename&gt;&#39; cannot be updated
Vous tentez d'ouvrir un projet créé dans une version antérieure de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Le projet doit être mis à jour au format actuel, mais cette opération est impossible car le fichier projet spécifié \(.vbproj\) est marqué comme étant en lecture seule ou il est placé sous le contrôle de code source et est actuellement verrouillé par un autre utilisateur.  
  
### Pour corriger cette erreur  
  
1.  Dans l'Explorateur de fichiers, recherchez le fichier projet spécifié.  
  
2.  Dans le menu **Fichier**, choisissez **Propriétés**.  
  
3.  Dans la boîte de dialogue **Propriétés**, désactivez l'attribut **Lecture seule**.  
  
 Si le fichier est sous le contrôle de code source et est verrouillé par un autre utilisateur, attendez qu'il soit disponible et extrayez\-le localement.  
  
## Voir aussi  
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/fr-fr/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)