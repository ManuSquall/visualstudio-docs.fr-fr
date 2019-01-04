---
title: IEnumDebugThreads2::Clone | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEnumDebugThreads2::Clone
helpviewer_keywords:
- IEnumDebugThreads2::Clone
ms.assetid: d774322c-e72d-4df3-b317-928da39dadc5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6431651f3bfba7387256f62286bf42d4b0f99ef8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53959815"
---
# <a name="ienumdebugthreads2clone"></a>IEnumDebugThreads2::Clone
Retourne une copie de l’énumération actuelle comme un objet distinct.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Clone(  
   IEnumDebugThreads2** ppEnum  
);  
```  
  
```csharp  
int Clone(  
   out IEnumDebugThreads2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppEnum`  
 [out] Retourne une copie de cette énumération en tant qu’objet distinct.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 La copie de l’énumération a le même état que l’original au moment de que cette méthode est appelée. Toutefois, les États de la copie et la version d’origine sont distincts et peuvent être modifiées individuellement.  
  
## <a name="see-also"></a>Voir aussi  
 [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)