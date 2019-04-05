---
title: IDebugStackFrame2::GetDocumentContext | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetDocumentContext
helpviewer_keywords:
- IDebugStackFrame2::GetDocumentContext
ms.assetid: 69e81439-1238-4f18-9028-6fd1c1ba5e4a
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 35ec80a005a3f004de00a12908de38082c405849
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58949503"
---
# <a name="idebugstackframe2getdocumentcontext"></a>IDebugStackFrame2::GetDocumentContext
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtient le contexte de document pour ce frame de pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetDocumentContext (   
   IDebugDocumentContext2** ppCxt  
);  
```  
  
```csharp  
int GetDocumentContext (   
   out IDebugDocumentContext2 ppCxt  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppCxt`  
 [out] Retourne un [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) objet qui représente la position actuelle dans un document source.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Cette méthode est plus rapide que l’appel le [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md) (méthode), puis en appelant le [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) méthode sur le contexte de code. Toutefois, il n’est pas garanti que chaque moteur de débogage (dé) implémente cette méthode.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)
