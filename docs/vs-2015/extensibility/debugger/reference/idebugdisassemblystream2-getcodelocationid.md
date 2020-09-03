---
title: 'IDebugDisassemblyStream2 :: GetCodeLocationId | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
ms.assetid: 567adfb8-2f54-499a-a027-e4ecb82277ef
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ebb2280f814985e2352413921a00268d96761b7d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196225"
---
# <a name="idebugdisassemblystream2getcodelocationid"></a>IDebugDisassemblyStream2::GetCodeLocationId
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Retourne un identificateur d’emplacement du code pour un contexte de code particulier.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetCodeLocationId(   
   IDebugCodeContext2* pCodeContext,  
   UINT64*             puCodeLocationId  
);  
```  
  
```csharp  
int GetCodeLocationId(   
   IDebugCodeContext2 pCodeContext,  
   out ulong          puCodeLocationId  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pCodeContext`  
 dans Objet [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) à convertir en identificateur.  
  
 `puCodeLocationId`  
 à Retourne l’identificateur de l’emplacement du code. Consultez la section Notes.  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur. Retourne `E_CODE_CONTEXT_OUT_OF_SCOPE` si le contexte de code est valide mais en dehors de la portée.  
  
## <a name="remarks"></a>Notes  
 L’identificateur d’emplacement du code est spécifique au moteur DE débogage (DE) qui prend en charge le code machine. Cet identificateur d’emplacement est utilisé en interne par le DE pour effectuer le suivi des positions dans le code et est généralement une adresse ou un décalage d’un genre. La seule exigence est que si le contexte de code d’un emplacement est inférieur au contexte de code d’un autre emplacement, l’identificateur de l’emplacement du code correspondant du premier contexte de code doit également être inférieur à l’identificateur de l’emplacement du code du deuxième contexte de code.  
  
 Pour récupérer le contexte de code d’un identificateur d’emplacement du code, appelez la méthode [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md) .  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)
