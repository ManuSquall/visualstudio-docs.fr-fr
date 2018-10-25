---
title: IDebugCodeContext2::GetDocumentContext | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCodeContext2::GetDocumentContext
helpviewer_keywords:
- IDebugCodeContext2::GetDocumentContext
ms.assetid: d552cc92-963f-43c1-949f-ae6b63a427b8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dd0fa6dd8d587ade2ca06c3f39f65fb3a5fd295d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49822187"
---
# <a name="idebugcodecontext2getdocumentcontext"></a>IDebugCodeContext2::GetDocumentContext
Obtient le contexte de document qui correspond à ce contexte de code. Le contexte de document représente une position dans le fichier source qui correspond au code source qui a généré cette instruction.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetDocumentContext(   
   IDebugDocumentContext2** ppSrcCxt  
);  
```  
  
```csharp  
int GetDocumentContext(   
   out IDebugDocumentContext2 ppSrcCxt  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppSrcCxt`  
 [out] Retourne le [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) objet correspondant au contexte de code.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 En règle générale, le contexte de document peut être considéré comme une position dans un fichier source pendant que le contexte de code est une position d’une instruction de code dans un flux d’exécution.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)