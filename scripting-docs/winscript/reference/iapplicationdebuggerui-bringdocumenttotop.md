---
title: 'IApplicationDebuggerUI :: BringDocumentToTop | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: b51e7b588750fc72e61840c4748c006eea732c22
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577798"
---
# <a name="iapplicationdebuggeruibringdocumenttotop"></a>IApplicationDebuggerUI::BringDocumentToTop
Affiche la fenêtre contenant le document de débogage spécifié en haut de l’interface utilisateur du débogueur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT BringDocumentToTop(  
   IDebugDocumentText*  pddt  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pddt`  
 dans Déboguez le document à afficher dans la partie supérieure de l’interface utilisateur du débogueur.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_INVALIDARG`|Le document n’est pas connu.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode amène la fenêtre contenant le document de débogage spécifié en haut de l’interface utilisateur du débogueur.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IApplicationDebuggerUI](../../winscript/reference/iapplicationdebuggerui-interface.md)