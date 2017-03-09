---
title: "CA2220&#160;: Les finaliseurs doivent appeler le finaliseur de leur classe de base | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2220"
  - "FinalizersShouldCallBaseClassFinalizer"
helpviewer_keywords: 
  - "CA2220"
  - "FinalizersShouldCallBaseClassFinalizer"
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2220&#160;: Les finaliseurs doivent appeler le finaliseur de leur classe de base
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|FinalizersShouldCallBaseClassFinalizer|  
|CheckId|CA2220|  
|Catégorie|Microsoft.Usage|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Un type qui substitue <xref:System.Object.Finalize%2A?displayProperty=fullName> n'appelle pas la méthode <xref:System.Object.Finalize%2A> dans sa classe de base.  
  
## Description de la règle  
 La finalisation doit être propagée par le biais de la hiérarchie d'héritage.  Pour garantir ce procédé, les types doivent appeler leur méthode <xref:System.Object.Finalize%2A> de classe de base à partir de leur propre méthode <xref:System.Object.Finalize%2A>.  Le compilateur C\# ajoute automatiquement l'appel au finaliseur de classe de base.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, appelez la méthode <xref:System.Object.Finalize%2A> du type de base de votre méthode <xref:System.Object.Finalize%2A>.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  Certains compilateurs qui ciblent le Common Language Runtime insèrent un appel au finaliseur du type de base dans le langage intermédiaire de Microsoft, MSIL \(MicroSoft Intermediate Language\).  Si un avertissement issu de cette règle est rapporté, votre compilateur n'insère pas l'appel, et vous devez l'ajouter à votre code.  
  
## Exemple  
 L'exemple Visual Basic suivant présente un type `TypeB` qui appelle correctement la méthode <xref:System.Object.Finalize%2A> dans sa classe de base.  
  
 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2220-finalizers-should-call-base-class-finalizer_1.vb)]  
  
## Voir aussi  
 [Modèle de suppression](../Topic/Dispose%20Pattern.md)