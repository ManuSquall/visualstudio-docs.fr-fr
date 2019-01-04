---
title: IEEVisualizerService::GetValueDisplayStringCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IEEVisualizerService::GetValueDisplayStringCount
- GetValueDisplayStringCount
ms.assetid: d683a833-fbfb-4042-84df-6905124a268a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8af1b785e56d5efba2505b0cdbd5a9474b5c261b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53957947"
---
# <a name="ieevisualizerservicegetvaluedisplaystringcount"></a>IEEVisualizerService::GetValueDisplayStringCount
Récupère le nombre de chaînes de valeur à afficher pour la propriété spécifiée ou du champ.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetValueDisplayStringCount (  
   DWORD         displayKind,   
   IDebugField * propertyOrField,   
   ULONG *       pcelt  
);  
```  
  
```csharp  
int GetValueDisplayStringCount (  
   uint        displayKind,   
   IDebugField propertyOrField,   
   out ulong   pcelt  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `displayKind`  
 [in] Valeur à partir de la [DisplayKind](../../../extensibility/debugger/reference/displaykind.md) énumération.  
  
 `propertyOrField`  
 [in] Un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interface qui représente une propriété ou un champ.  
  
 `pcelt`  
 [out] Retourne le nombre de chaînes de valeur à afficher.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)