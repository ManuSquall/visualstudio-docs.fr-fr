---
title: IDebugDocumentContext2::Seek | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::Seek
helpviewer_keywords:
- IDebugDocumentContext2::Seek
ms.assetid: 71501356-8a82-4d36-b354-6625bdd2baa0
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f001eb73e3c24ac1c9f15a4bd2c37c8d2cbe660e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62875686"
---
# <a name="idebugdocumentcontext2seek"></a>IDebugDocumentContext2::Seek
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Déplace le contexte de document en un nombre donné d’instructions ou des lignes.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT Seek(   
   int                      nCount,  
   IDebugDocumentContext2** ppDocContext  
);  
```  
  
```cpp#  
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
