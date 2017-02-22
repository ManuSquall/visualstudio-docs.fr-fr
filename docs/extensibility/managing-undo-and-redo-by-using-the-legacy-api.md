---
title: "Gestion Annuler et r&#233;tablir &#224; l&#39;aide de l&#39;API h&#233;rit&#233;e | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs (Visual Studio SDK), hérités - Annuler gestion"
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Gestion Annuler et r&#233;tablir &#224; l&#39;aide de l&#39;API h&#233;rit&#233;e
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les éditeurs doivent prendre en charge les opérations d'annulation qui permet aux utilisateurs d'annuler leurs modifications récentes lorsqu'ils modifient le code. La plupart des éditeurs implémentés sous [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] peuvent avoir des annulations prise en charge automatiquement par l'environnement de développement intégré \(IDE\).  
  
## Dans cette section  
 [Comment : implémenter la gestion de l'annulation](../extensibility/how-to-implement-undo-management.md)  
 Fournit la fonction d'annulation pour les éditeurs d'avec un ou plusieurs vues.  
  
 [Comment : effacer la pile d'annulation](../extensibility/how-to-clear-the-undo-stack.md)  
 Décrit comment supprimer une pile d'annulation.  
  
 [Comment : utiliser la gestion de l'opération d'annulation liée](../extensibility/how-to-use-linked-undo-management.md)  
 Inclut une gestion d'annulation liée dans votre éditeur.  
  
## Référence  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
 Fournit un éditeur qui prend en charge plusieurs vues de gestion Annuler.  
  
## Rubriques connexes