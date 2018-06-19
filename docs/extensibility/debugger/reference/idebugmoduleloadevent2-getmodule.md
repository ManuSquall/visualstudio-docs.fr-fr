---
title: IDebugModuleLoadEvent2::GetModule | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugModuleLoadEvent2::GetModule
helpviewer_keywords:
- IDebugModuleLoadEvent2::GetModule
ms.assetid: c86482bb-9ce5-4e63-bbe0-969b50169424
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b6188ba6842a922fa0758a21c0f496f50889f8b3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31114529"
---
# <a name="idebugmoduleloadevent2getmodule"></a>IDebugModuleLoadEvent2::GetModule
Obtient le module est chargé ou déchargé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetModule(   
   IDebugModule2** pModule,  
   BSTR*           pbstrDebugMessage,  
   BOOL*           pbLoad  
);  
```  
  
```csharp  
int GetModule(   
   out IDebugModule2 pModule,  
   ref string        pbstrDebugMessage,  
   ref int           pbLoad  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pModule`  
 [out] Retourne un [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) objet qui représente le module de chargement ou de déchargement.  
  
 `pbstrDebugMessage`  
 [dans, out] Retourne un message facultatif décrivant cet événement. Si ce paramètre est une valeur null, aucun message n’est demandée.  
  
 `pbLoad`  
 [dans, out] Différent de zéro (`TRUE`) si le module est chargé et zéro (`FALSE`) si le déchargement du module est en cours. Si ce paramètre est une valeur null, aucun état n’est demandée.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)