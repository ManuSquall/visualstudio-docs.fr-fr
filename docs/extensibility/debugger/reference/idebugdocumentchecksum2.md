---
title: "IDebugDocumentChecksum2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interface de IDebugDocumentChecksum2"
ms.assetid: 6d22fa94-21aa-46cb-b5b5-32a6399ebb20
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugDocumentChecksum2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Représente un checksum pour un document de débogage et permet de passer la somme de contrôle entre les composants.  
  
## Syntaxe  
  
```  
IDebugDocumentChecksum2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Cette interface peut être implémentée par tout composant qui expose l'interface d' [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) .  Toutefois, il est principalement implémenté par les moteurs de débogage afin que le checksum incorporée dans un fichier de symboles \(\* .pdb\) peut être retournée à l'IDE et être utilisée en recherchant une source.  
  
## Méthodes  
 Le tableau suivant répertorie les méthodes d' `IDebugDocumentChecksum2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetChecksumAndAlgorithmId](../../../extensibility/debugger/reference/idebugdocumentchecksum2-getchecksumandalgorithmid.md)|Extrait l'identificateur de checksum et de l'algorithme de document donné nombre maximal d'octets à utiliser.|  
  
## Configuration requise  
 en\-tête : Msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll