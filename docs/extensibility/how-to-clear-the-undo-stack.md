---
title: "Comment : effacer la pile d&#39;annulation | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs (Visual Studio SDK), hérités - effacer la pile d'annulation"
ms.assetid: 2200d2d4-7f58-401c-87fc-ddd32d368193
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# Comment : effacer la pile d&#39;annulation
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La procédure suivante ci\-dessous explique comment désactiver la pile d'annulations.  
  
### Pour désactiver la pile d'annulations  
  
1.  Pour désactiver l'utilisation de la pile d'annulations la méthode d' [IOleUndoManager : : DiscardFrom](http://msdn.microsoft.com/library/windows/desktop/ms693799) .  Voici un exemple de la façon suivante :  
  
    ```  
    HRESULT CCmdWindow::ClearUndoStack()  
    {  
      HRESULT hr = S_OK;  
  
      if (m_pUndoMgr == NULL)  
        {  
        IfFailGo(m_pTextLines->GetUndoManager(&m_pUndoMgr));  
        ASSERT(m_pUndoMgr != NULL, "",;);  
        }  
  
      IfFailGo(m_pUndoMgr->DiscardFrom(NULL));  
  
    Error:  
      return hr;  
    }  
    ```  
  
## Voir aussi  
 [Comment : implémenter la gestion de l'annulation](../extensibility/how-to-implement-undo-management.md)