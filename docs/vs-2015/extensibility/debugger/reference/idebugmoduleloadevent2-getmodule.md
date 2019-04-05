---
title: IDebugModuleLoadEvent2::GetModule | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugModuleLoadEvent2::GetModule
helpviewer_keywords:
- IDebugModuleLoadEvent2::GetModule
ms.assetid: c86482bb-9ce5-4e63-bbe0-969b50169424
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0083946051fe78fc1bd19ea877475465e0b6477f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58948930"
---
# <a name="idebugmoduleloadevent2getmodule"></a>IDebugModuleLoadEvent2::GetModule
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtient le module est chargé ou déchargé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
