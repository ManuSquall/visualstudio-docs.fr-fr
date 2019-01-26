---
title: IDebugModuleLoadEvent2::GetModule | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugModuleLoadEvent2::GetModule
helpviewer_keywords:
- IDebugModuleLoadEvent2::GetModule
ms.assetid: c86482bb-9ce5-4e63-bbe0-969b50169424
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 88a3ff6ae5416ff4c734ab4cf88bacb4cfa5d494
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55007616"
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
 [out] Retourne un [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) objet qui représente le module qui est de chargement ou de déchargement.  
  
 `pbstrDebugMessage`  
 [in, out] Retourne un message facultatif décrivant cet événement. Si ce paramètre est une valeur null, aucun message n’est demandée.  
  
 `pbLoad`  
 [in, out] Différent de zéro (`TRUE`) si le module est égal à zéro et chargement (`FALSE`) si le déchargement du module est en cours. Si ce paramètre est une valeur null, aucun état n’est demandée.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)