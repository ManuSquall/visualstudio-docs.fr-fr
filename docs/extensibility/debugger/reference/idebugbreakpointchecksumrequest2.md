---
title: IDebugBreakpointChecksumRequest2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugBreakpointChecksumRequest2 interface
ms.assetid: 9cfdbca5-052c-48e9-8411-e2e9e4065d00
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8ff19ac7cfc05e198e49dccdc0a24f198cd1be02
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55013247"
---
# <a name="idebugbreakpointchecksumrequest2"></a>IDebugBreakpointChecksumRequest2
Représente une somme de contrôle de document pour une demande de point d’arrêt.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugBreakpointChecksumRequest2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 Implémentée par le [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] déboguer le package et consommées par les moteurs de débogage.  
  
## <a name="methods"></a>Méthodes  
 Le tableau suivant présente les méthodes de `IDebugBreakpointChecksumRequest2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetChecksum](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-getchecksum.md)|Récupère la somme de contrôle de document pour une demande de point d’arrêt étant donnée l’identificateur unique de l’algorithme de checksum à utiliser.|  
|[IsChecksumEnabled](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-ischecksumenabled.md)|Détermine si la somme de contrôle est activé pour ce document.|  
  
## <a name="requirements"></a>Spécifications  
 En-tête : Msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll