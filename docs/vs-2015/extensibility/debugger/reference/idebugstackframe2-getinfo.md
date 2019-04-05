---
title: IDebugStackFrame2::GetInfo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetInfo
helpviewer_keywords:
- IDebugStackFrame2::GetInfo
ms.assetid: 19c6870b-b94e-453c-bf19-82ce95b79d26
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f6ebfda26b58bb1e7048b969133fa1672edad8a9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58950096"
---
# <a name="idebugstackframe2getinfo"></a>IDebugStackFrame2::GetInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtient une description du frame de pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetInfo (   
   FRAMEINFO_FLAGS dwFieldSpec,  
   UINT            nRadix,  
   FRAMEINFO*      pFrameInfo  
);  
```  
  
```csharp  
int GetInfo (   
   enum_FRAMEINFO_FLAGS dwFieldSpec,  
   uint                 nRadix,  
   FRAMEINFO[]          pFrameInfo  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwFieldSpec`  
 [in] Une combinaison d’indicateurs de la [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) énumération qui spécifie les champs de la `pFrameInfo` paramètre doivent être renseignés.  
  
 `nRadix`  
 [in] La base à utiliser dans toutes les informations numériques de mise en forme.  
  
 `pFrameInfo`  
 [out] Un [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) structure est remplie avec la description du frame de pile.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
