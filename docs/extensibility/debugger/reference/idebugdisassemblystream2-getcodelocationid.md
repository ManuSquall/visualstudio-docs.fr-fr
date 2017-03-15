---
title: IDebugDisassemblyStream2::GetCodeLocationId | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
ms.assetid: 567adfb8-2f54-499a-a027-e4ecb82277ef
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: b64ad6cc146c2e2457cf9c39d5ce2c5d8f78cf65
ms.lasthandoff: 02/22/2017

---
# <a name="idebugdisassemblystream2getcodelocationid"></a>IDebugDisassemblyStream2::GetCodeLocationId
Retourne un identificateur d’emplacement de code pour un contexte de code particulière.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetCodeLocationId(   
   IDebugCodeContext2* pCodeContext,  
   UINT64*             puCodeLocationId  
);  
```  
  
```c#  
int GetCodeLocationId(   
   IDebugCodeContext2 pCodeContext,  
   out ulong          puCodeLocationId  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pCodeContext`  
 [in] Un [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) à convertir en un identificateur d’objet.  
  
 `puCodeLocationId`  
 [out] Retourne l’identificateur d’emplacement de code. Consultez la section Notes.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur. Retourne `E_CODE_CONTEXT_OUT_OF_SCOPE` si le code de contexte est valide, mais en dehors de l’étendue.  
  
## <a name="remarks"></a>Notes  
 L’identificateur d’emplacement de code est spécifique au moteur de débogage (DE) prenant en charge le code machine. Cet identificateur est utilisé en interne par le DE suivre les positions dans le code et est généralement une adresse ou le décalage d’un certain type. La seule exigence est que si le contexte du code d’un emplacement est inférieur au contexte du code d’un autre emplacement, l’identificateur d’emplacement code correspondant du premier contexte code doit également être inférieure à l’identificateur d’emplacement de code du deuxième contexte code.  
  
 Pour extraire le contexte du code d’un identificateur d’emplacement du code, appelez le [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)
