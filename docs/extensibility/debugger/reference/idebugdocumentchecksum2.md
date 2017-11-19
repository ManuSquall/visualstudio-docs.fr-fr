---
title: IDebugDocumentChecksum2 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugDocumentChecksum2 interface
ms.assetid: 6d22fa94-21aa-46cb-b5b5-32a6399ebb20
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d70923fa450f79aacd059ebb4d2fde753fb13564
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugdocumentchecksum2"></a>IDebugDocumentChecksum2
Représente une somme de contrôle pour un document de débogage et permet le transfert de la somme de contrôle entre les composants.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugDocumentChecksum2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Cette interface peut être implémentée par un composant qui expose la [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) interface. Toutefois, il est principalement implémenté par les moteurs de débogage pour que la somme de contrôle incorporé dans un fichier de symboles (*.pdb) peut être passé à l’IDE et utilisée lors de la recherche d’une source.  
  
## <a name="methods"></a>Méthodes  
 Le tableau suivant présente les méthodes de `IDebugDocumentChecksum2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetChecksumAndAlgorithmId](../../../extensibility/debugger/reference/idebugdocumentchecksum2-getchecksumandalgorithmid.md)|Récupère l’identificateur de somme de contrôle et l’algorithme de document donné le nombre maximal d’octets à utiliser.|  
  
## <a name="requirements"></a>Spécifications  
 En-tête : Msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll