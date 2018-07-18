---
title: IDebugBreakpointChecksumRequest2 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugBreakpointChecksumRequest2 interface
ms.assetid: 9cfdbca5-052c-48e9-8411-e2e9e4065d00
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cb319b14e1d373abe3c0634c768bfe1dcb04f539
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31101116"
---
# <a name="idebugbreakpointchecksumrequest2"></a>IDebugBreakpointChecksumRequest2
Représente une somme de contrôle du document pour une demande de point d’arrêt.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugBreakpointChecksumRequest2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Implémenté par le [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] déboguer le package et consommé par les moteurs de débogage.  
  
## <a name="methods"></a>Méthodes  
 Le tableau suivant présente les méthodes de `IDebugBreakpointChecksumRequest2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetChecksum](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-getchecksum.md)|Récupère la somme de contrôle du document pour une demande de point d’arrêt étant donnée l’identificateur unique de l’algorithme de somme de contrôle à utiliser.|  
|[IsChecksumEnabled](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-ischecksumenabled.md)|Détermine si la somme de contrôle est activé pour ce document.|  
  
## <a name="requirements"></a>Spécifications  
 En-tête : Msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll