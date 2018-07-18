---
title: IDebugDocumentContext2::Seek | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDocumentContext2::Seek
helpviewer_keywords:
- IDebugDocumentContext2::Seek
ms.assetid: 71501356-8a82-4d36-b354-6625bdd2baa0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 70ba99005bfe64782bcbaf655e659ae015a6d5c1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31104655"
---
# <a name="idebugdocumentcontext2seek"></a>IDebugDocumentContext2::Seek
Déplace le contexte de document en un nombre donné d’instructions ou des lignes.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Seek(   
   int                      nCount,  
   IDebugDocumentContext2** ppDocContext  
);  
```  
  
```cpp  
int Seek(   
   int                        nCount,  
   out IDebugDocumentContext2 ppDocContext  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `nCount`  
 [in] Nombre d’instructions ou des lignes pour passer en fonction du contexte du document.  
  
 `ppDocContext`  
 [out] Retourne un nouveau [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) objet avec la nouvelle position.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)