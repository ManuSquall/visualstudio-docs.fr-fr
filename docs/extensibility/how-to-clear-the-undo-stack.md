---
title: 'Procédure : Effacer la pile d’annulations | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - clear undo stack
ms.assetid: 2200d2d4-7f58-401c-87fc-ddd32d368193
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 14cf2af71f492dc4a82f6d8d9cf05fadcb0dcda2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53827545"
---
# <a name="how-to-clear-the-undo-stack"></a>Procédure : Effacer la pile d’annulation
La procédure suivante ci-dessous explique comment effacer la pile d’annulation.  
  
## <a name="to-clear-the-undo-stack"></a>Pour effacer la pile d’annulation  
  
1.  Pour effacer la pile d’annulation utilisent le [IOleUndoManager::DiscardFrom](/windows/desktop/api/ocidl/nf-ocidl-ioleundomanager-discardfrom) (méthode). Voici un exemple de ceci :  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour Gestion d’annulation implémenter](../extensibility/how-to-implement-undo-management.md)