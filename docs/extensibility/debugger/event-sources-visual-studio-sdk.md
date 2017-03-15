---
title: "Sources d&#39;&#233;v&#233;nements (Kit de d&#233;veloppement logiciel Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "débogage [Debugging SDK], sources d'événements"
ms.assetid: b9ba0908-ae4c-4a64-aab1-bee453dd7a22
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Sources d&#39;&#233;v&#233;nements (Kit de d&#233;veloppement logiciel Visual Studio)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Il existe deux sources d'événements : le moteur \(DE\) de débogage et la session particulière nécessite le \(SDM\) gestionnaire.  les événements envoyés d'un De ont un moteur non null, alors que les événements envoyés du SDM ont un moteur NULL.  
  
## Exemple  
 L'exemple suivant montre comment envoyer **IDebugProgramCreateEvent2** De au SDM.  
  
```  
CDebugProgramCreateEvent* pProgramCreateEvent = new CDebugProgramCreateEvent();  
if (FAILED(pCallback->Event(m_pEngine, NULL, m_pProgram, NULL, pProgramCreateEvent, IID_IDebugProgramCreateEvent2, EVENT_ASYNCHRONOUS)))  
{  
   // Handle failure here.  
}  
]  
  
CEvent * pProgCreate = new CEvent(IID_IDebugProgramCreateEvent2, EVENT_ASYNCHRONOUS);    
pProgCreate->SendEvent(pCallback, m_pEngine, (IDebugProgram2 *)this, NULL);  
  
HRESULT CEvent::SendEvent(IDebugEventCallback2 *pCallback, IDebugEngine2 *pEngine, IDebugProgram2 *pProgram, IDebugThread2 *pThread) {    
   HRESULT hr;    
  
   if (m_dwAttrib & EVENT_STOPPING)    
   {    
      hr = SendStoppingEvent(pCallback, pEngine, pProgram, pThread);    
   }    
   else if (m_dwAttrib & EVENT_SYNCHRONOUS)    
   {    
      hr = SendSynchronousEvent(pCallback, pEngine, pProgram, pThread);    
   }    
   else    
   {    
      assert(m_dwAttrib == 0);    
      hr = SendAsynchronousEvent(pCallback, pEngine, pProgram, pThread);    
   }    
  
   return hr;    
}    
  
HRESULT CEvent::SendAsynchronousEvent(IDebugEventCallback2 *pCallback, IDebugEngine2 *pEngine, IDebugProgram2 *pProgram, IDebugThread2 *pThread) {    
  
    HRESULT hr;    
  
   // Make sure the CEvent object running this code is not deleted until the code completes.    
   AddRef();    
  
   pCallback->Event(pEngine, NULL, pProgram, pThread, (IDebugEvent2 *)this, m_riid, m_dwAttrib);    
  
   // No error recovery here.    
   hr = S_OK;     
  
   Release();    
   return hr;    
}  
  
```  
  
## Voir aussi  
 [L'envoi d'événements](../../extensibility/debugger/sending-events.md)