---
title: IDebugDocumentContext2::Seek | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDocumentContext2::Seek
helpviewer_keywords:
- IDebugDocumentContext2::Seek
ms.assetid: 71501356-8a82-4d36-b354-6625bdd2baa0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 85ab2a7d81fb2c4b0d9963c57d7c85bdb9d5515c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54974917"
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
 [in] Nombre d’instructions ou des lignes pour passer, en fonction du contexte de document.  
  
 `ppDocContext`  
 [out] Retourne un nouvel [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) objet avec la nouvelle position.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)