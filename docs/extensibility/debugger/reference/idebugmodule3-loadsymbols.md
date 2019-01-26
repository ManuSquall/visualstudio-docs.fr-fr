---
title: IDebugModule3::LoadSymbols | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugModule3::LoadSymbols
helpviewer_keywords:
- IDebugModule3::LoadSymbols
ms.assetid: 7548c8c1-cbc6-48aa-a845-19058d4a85bb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a14406d0aeb58cead006ef9f1d5485a053d4a72c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55021060"
---
# <a name="idebugmodule3loadsymbols"></a>IDebugModule3::LoadSymbols
Charge les symboles pour le module actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT LoadSymbols(  
   void  
);  
```  
  
```csharp  
int LoadSymbols();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Si la méthode réussit, elle retourne `S_OK`. En cas d’échec, elle retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Cette méthode charge les symboles à partir du chemin de recherche actuel (qui peut être modifié en appelant le [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md) méthode).  
  
 Cette méthode est recommandée sur le [ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)   
 [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)