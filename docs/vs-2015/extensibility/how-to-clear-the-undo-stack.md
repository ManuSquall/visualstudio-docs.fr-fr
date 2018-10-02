---
title: 'Comment : effacer la pile d’annulations | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - clear undo stack
ms.assetid: 2200d2d4-7f58-401c-87fc-ddd32d368193
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 75b821a757f466045b27b7f52e1900ece3f0b0d2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47506683"
---
# <a name="how-to-clear-the-undo-stack"></a>Comment : effacer la pile d’annulation
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Comment : effacer la pile Annuler](https://docs.microsoft.com/visualstudio/extensibility/how-to-clear-the-undo-stack).  
  
La procédure suivante ci-dessous explique comment effacer la pile d’annulation.  
  
### <a name="to-clear-the-undo-stack"></a>Pour effacer la pile d’annulation  
  
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
 [Guide pratique pour implémenter la gestion des opérations d’annulation](../extensibility/how-to-implement-undo-management.md)

