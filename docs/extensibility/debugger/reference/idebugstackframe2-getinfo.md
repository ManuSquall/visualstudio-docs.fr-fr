---
title: IDebugStackFrame2::GetInfo | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugStackFrame2::GetInfo
helpviewer_keywords: IDebugStackFrame2::GetInfo
ms.assetid: 19c6870b-b94e-453c-bf19-82ce95b79d26
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b97acf264bfede855d96be90565e84b197e3e139
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugstackframe2getinfo"></a>IDebugStackFrame2::GetInfo
Obtient une description du frame de pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
 [in] Une combinaison d’indicateurs à partir de la [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) énumération qui spécifie les champs de la `pFrameInfo` paramètre doivent être renseignés.  
  
 `nRadix`  
 [in] La base à utiliser dans toutes les informations numériques de mise en forme.  
  
 `pFrameInfo`  
 [out] A [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) structure est remplie avec la description du frame de pile.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)