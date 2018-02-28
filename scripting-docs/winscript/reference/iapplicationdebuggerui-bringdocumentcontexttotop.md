---
title: IApplicationDebuggerUI::BringDocumentContextToTop | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IApplicationDebuggerUI.BringDocumentContextToTop
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebuggerUI::BringDocumentContextToTop
ms.assetid: 7844217d-658b-42af-8d10-2714f4eded20
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2fab017ab286957cf2c4be35832b1db877b339bd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iapplicationdebuggeruibringdocumentcontexttotop"></a>IApplicationDebuggerUI::BringDocumentContextToTop
Affiche la fenêtre contenant le contexte de document donné vers le haut de l’interface utilisateur du débogueur et fait défiler la fenêtre vers le contexte.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT BringDocumentContextToTop(  
   IDebugDocumentContext*  pddc  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pddc`  
 [in] Contexte de document pour déplacer vers le haut dans l’interface utilisateur du débogueur.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_INVALIDARG`|Le contexte spécifié par `pddc` n’est pas connu.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode met la fenêtre contenant le contexte de document donné vers le haut de l’interface utilisateur du débogueur et fait défiler la fenêtre vers le contexte.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IApplicationDebuggerUI](../../winscript/reference/iapplicationdebuggerui-interface.md)