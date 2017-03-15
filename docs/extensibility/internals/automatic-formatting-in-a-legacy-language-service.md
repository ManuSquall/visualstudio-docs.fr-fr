---
title: "Mise en forme dans un Service de langage h&#233;rit&#233; automatique | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "la mise en forme automatique, services de langage"
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Mise en forme dans un Service de langage h&#233;rit&#233; automatique
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Avec la mise en forme automatique, un service de langage insère automatiquement un extrait de code lorsqu'un utilisateur démarre à taper une construction de code.  
  
## comportement de mise en forme automatique  
 Par exemple, lorsque vous tapez `if`, le service de langage insère automatiquement l'accolade correspondante, ou si vous appuyez sur la touche ENTRÉE, le service de langage force le point d'insertion sur la nouvelle ligne au niveau de retrait approprié, selon que la ligne précédente ouvrez une nouvelle portée.  
  
 Le filtre de commande utilisé pour le reste du service de langage peut également être utilisé pour la mise en forme automatique.  vous pouvez également mettre en surbrillance l'accolade correspondante par <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>appelant.  
  
## Voir aussi  
 [Développement d'un Service de langage](../../extensibility/internals/developing-a-legacy-language-service.md)