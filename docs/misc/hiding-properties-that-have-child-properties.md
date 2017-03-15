---
title: "Masquage des propri&#233;t&#233;s qui ont des propri&#233;t&#233;s enfants | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "propriétés [Kit de développement logiciel Visual Studio], masquage"
  - "fenêtre Propriétés, masquage des propriétés qui ont des propriétés enfants"
ms.assetid: 6003607e-fc19-4bf9-a299-9f6adf8e92eb
caps.latest.revision: 13
caps.handback.revision: 13
manager: "douge"
---
# Masquage des propri&#233;t&#233;s qui ont des propri&#233;t&#233;s enfants
Vous souhaitez masquer les propriétés qui ont des propriétés enfants :  
  
-   Si vous imbriquez des projets dans laquelle le projet parent contrôle par programmation certains aspects du projet enfant.  
  
-   Si vous utilisez un contrôle avec un concepteur spécialisé et vous ne souhaitez pas permettre aux développeurs de l'accès complet à toutes les propriétés du contrôle.  
  
-   Si la propriété de portée d'un objet et souhaitez limiter la vue des propriétés.  
  
### Pour masquer des propriétés qui ont des propriétés enfants  
  
1.  définissez le paramètre d' `pfDisplay` dans <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> à `FALSE`.  
  
2.  définissez le paramètre d' `pfHide` dans <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> à `TRUE`.  
  
## Voir aussi  
 [Afficher la grille Propriétés](../extensibility/internals/properties-display-grid.md)