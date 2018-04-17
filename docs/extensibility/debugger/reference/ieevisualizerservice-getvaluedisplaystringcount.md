---
title: IEEVisualizerService::GetValueDisplayStringCount | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 5f67c1f0566f9e5749f4ff9233f1d2a803754550
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="ieevisualizerservicegetvaluedisplaystringcount"></a>IEEVisualizerService::GetValueDisplayStringCount
Récupère le nombre de chaînes à afficher pour la propriété spécifiée ou un champ de valeur.  
  
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
 [out] Retourne le nombre de chaînes de la valeur à afficher.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)