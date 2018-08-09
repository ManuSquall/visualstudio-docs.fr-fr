---
title: 'Comment : effacer la pile d’annulations | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - clear undo stack
ms.assetid: 2200d2d4-7f58-401c-87fc-ddd32d368193
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 59f8d57c0ba0e84107cd0d0290b950b335e5f2b0
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639469"
---
# <a name="how-to-clear-the-undo-stack"></a>Comment : effacer la pile d’annulation
La procédure suivante ci-dessous explique comment effacer la pile d’annulation.  
  
## <a name="to-clear-the-undo-stack"></a>Pour effacer la pile d’annulation  
  
1.  Pour effacer la pile d’annulation utilisent le [IOleUndoManager::DiscardFrom](http://msdn.microsoft.com/library/windows/desktop/ms693799) (méthode). Voici un exemple de ceci :  
  
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
 [Comment : gestion d’annulation implémenter](../extensibility/how-to-implement-undo-management.md)