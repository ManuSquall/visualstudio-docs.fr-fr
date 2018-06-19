---
title: IApplicationDebuggerUI::BringDocumentToTop | Documents Microsoft
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
ms.openlocfilehash: 57b76f44eeeaad1946d40435c770b0687b82fd17
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725309"
---
# <a name="iapplicationdebuggeruibringdocumenttotop"></a>IApplicationDebuggerUI::BringDocumentToTop
Met la fenêtre contenant le document de débogage spécifiés vers le haut dans le débogueur de l’interface utilisateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT BringDocumentToTop(  
   IDebugDocumentText*  pddt  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pddt`  
 [in] Déboguer le document à déplacer vers le haut dans l’interface utilisateur du débogueur.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_INVALIDARG`|Le document n’est pas connu.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode affiche la fenêtre contenant le document de débogage spécifiés vers le haut dans le débogueur de l’interface utilisateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IApplicationDebuggerUI](../../winscript/reference/iapplicationdebuggerui-interface.md)