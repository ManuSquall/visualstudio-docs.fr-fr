---
title: IDebugStackFrame3::GetUnwindCodeContext | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugStackFrame3::GetUnwindCodeContext
helpviewer_keywords:
- IDebugStackFrame3::GetUnwindCodeContext method
ms.assetid: b25f7e7d-2b24-48e4-93b3-829e61d73ebf
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c5a3fdaf9ca21841a43041f0ad5c1dc7b1507085
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62546887"
---
# <a name="idebugstackframe3getunwindcodecontext"></a>IDebugStackFrame3::GetUnwindCodeContext
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Retourne le contexte de code qui représente un emplacement si l’opération de déroulement de pile s’est produite.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetUnwindCodeContext(  
   IDebugCodeContext2 **ppCodeContext  
);  
```  
  
```csharp  
int GetUnwindCodeContext(  
   out IDebugCodeContext2 ppCodeContext  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppCodeContext`  
 [out] Retourne un [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) objet qui représente l’emplacement de contexte de code si un déroulement de pile s’est produite.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Bien que cette méthode peut retourner un contexte de code pour l’emplacement après un désempilage, cela ne signifie pas nécessairement que le déroulement de pile peut réellement se produire dans le frame de pile actuel.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
