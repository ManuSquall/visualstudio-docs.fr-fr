---
title: IDebugEngine2::ContinueFromSynchronousEvent | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine2::ContinueFromSynchronousEvent
helpviewer_keywords:
- IDebugEngine2::ContinueFromSynchronousEvent
ms.assetid: 9a57dfcd-df8e-4be5-b1fe-bd853e3c6bb2
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 75c359f8d7f7c0c5e9d335de296fe252b30d1c3d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58947799"
---
# <a name="idebugengine2continuefromsynchronousevent"></a>IDebugEngine2::ContinueFromSynchronousEvent
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Appelé par le Gestionnaire de session de débogage (SDM) pour indiquer qu’un événement de débogage synchrone, précédemment envoyé par le moteur de débogage (dé) pour le SDM, a été reçu et traité.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT ContinueFromSynchronousEvent(   
   IDebugEvent2* pEvent  
);  
```  
  
```csharp  
HRESULT ContinueFromSynchronousEvent(   
   IDebugEvent2 pEvent  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pEvent`  
 [in] Un [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) objet qui représente l’événement synchrone précédemment envoyé à partir de laquelle le débogueur doit se poursuivre.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Le DE doit vérifier qu’il était la source de l’événement représenté par le `pEvent` paramètre.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment implémenter cette méthode pour une simple `CEngine` objet qui implémente le [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) interface.  
  
```cpp#  
HRESULT CEngine::ContinueFromSynchronousEvent(IDebugEvent2* pEvent)  
{  
   HRESULT hr;  
  
   // Create a pointer to a unique event interface defined for batch file  
   // breaks.    
   IAmABatchFileEvent *pBatEvent;  
   // Check for successful query for the unique batch file event  
   // interface.  
   if (SUCCEEDED(pEvent->QueryInterface(IID_IAmABatchFileEvent,  
                                       (void **)&pBatEvent)))  
   {  
      // Release the result of the QI.  
      pBatEvent->Release();  
      // Check thread message for notification to continue.  
      if (PostThreadMessage(GetCurrentThreadId(),  
                            WM_CONTINUE_SYNC_EVENT,  
                            0,  
                            0))  
      {    
         hr = S_OK;  
      }  
      else  
      {  
         hr = HRESULT_FROM_WIN32(GetLastError());  
      }  
   }  
   else  
   {  
      hr = E_INVALIDARG;  
   }  
   return hr;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
