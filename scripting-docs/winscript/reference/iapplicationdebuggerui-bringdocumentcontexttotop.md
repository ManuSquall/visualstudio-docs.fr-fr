---
title: 'IApplicationDebuggerUI :: BringDocumentContextToTop | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebuggerUI.BringDocumentContextToTop
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebuggerUI::BringDocumentContextToTop
ms.assetid: 7844217d-658b-42af-8d10-2714f4eded20
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8648a4377e901908df20cdb5f413ee73ede5c1a6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577814"
---
# <a name="iapplicationdebuggeruibringdocumentcontexttotop"></a>IApplicationDebuggerUI::BringDocumentContextToTop
Affiche la fenêtre contenant le contexte de document donné en haut de l’interface utilisateur du débogueur et fait défiler la fenêtre jusqu’au contexte.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT BringDocumentContextToTop(  
   IDebugDocumentContext*  pddc  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pddc`  
 dans Contexte de document à afficher dans la partie supérieure de l’interface utilisateur du débogueur.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_INVALIDARG`|Le contexte spécifié par `pddc` n’est pas connu.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode amène la fenêtre contenant le contexte de document donné au sommet de l’interface utilisateur du débogueur et fait défiler la fenêtre jusqu’au contexte.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IApplicationDebuggerUI](../../winscript/reference/iapplicationdebuggerui-interface.md)