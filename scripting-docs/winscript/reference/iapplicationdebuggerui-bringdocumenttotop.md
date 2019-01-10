---
title: IApplicationDebuggerUI::BringDocumentToTop | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebuggerUI.BringDocumentToTop
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebuggerUI::BringDocumentToTop
ms.assetid: ef5fe1e7-4381-4409-a0d7-58f993abe84e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5c77c87011c539e02f92aa2aedfdcd7659466d37
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096250"
---
# <a name="iapplicationdebuggeruibringdocumenttotop"></a>IApplicationDebuggerUI::BringDocumentToTop
Apporte la fenêtre contenant le document de débogage spécifié vers le haut dans le débogueur de l’interface utilisateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT BringDocumentToTop(  
   IDebugDocumentText*  pddt  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pddt`  
 [in] Déboguer le document à placer en haut de l’interface utilisateur du débogueur.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_INVALIDARG`|Le document n’est pas connu.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode affiche la fenêtre contenant le document de débogage spécifié vers le haut dans le débogueur de l’interface utilisateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IApplicationDebuggerUI](../../winscript/reference/iapplicationdebuggerui-interface.md)