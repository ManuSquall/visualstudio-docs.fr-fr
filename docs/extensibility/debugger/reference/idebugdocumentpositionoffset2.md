---
title: "IDebugDocumentPositionOffset2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interface de IDebugDocumentPositionOffset2"
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugDocumentPositionOffset2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Représente une position dans un fichier source comme un offset de caractère.  
  
## Syntaxe  
  
```  
IDebugDocumentPositionOffset2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Implémenté par l'IDE et consommé par les moteurs de débogage.  
  
## Méthodes  
 Le tableau suivant répertorie les méthodes d' `IDebugDocumentPositionOffset2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetRange](../Topic/IDebugDocumentPositionOffset2::GetRange.md)|Extrait la plage de la position de document actif.|  
  
## Notes  
 Cela retourne les mêmes informations qu' [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md) mais dans les offsets de `char` du début du document.  Cela présente le document comme il existerait sur un disque, c. autrement dit., un tableau unidimensionnel de caractères, au lieu de la ligne et des informations sur les colonnes qui sont couramment retournées.  
  
## Configuration requise  
 en\-tête : Msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)