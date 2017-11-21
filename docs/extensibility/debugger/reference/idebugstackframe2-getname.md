---
title: IDebugStackFrame2::GetName | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugStackFrame2::GetName
helpviewer_keywords: IDebugStackFrame2::GetName
ms.assetid: 069d4f96-363f-404e-9c89-5318c4c9821b
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a2d5949ab1f5e070d172aaca85d11cca09b1d73c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugstackframe2getname"></a>IDebugStackFrame2::GetName
Obtient le nom du frame de pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetName (   
   BSTR* pbstrName  
);  
```  
  
```csharp  
int GetName (   
   out string pbstrName  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pbstrName`  
 [out] Retourne le nom du frame de pile.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Le nom d’un frame de pile est généralement le nom de la méthode en cours d’exécution.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)