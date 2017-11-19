---
title: IDebugDocumentTextExternalAuthor::NotifyChanged | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentTextExternalAuthor.NotifyChanged
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentTextExternalAuthor::NotifyChanged
ms.assetid: f0de7984-3a15-49e2-bd29-f768f34d2a4d
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 016eda303f5a5a74a20e42112890698a1ca28798
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenttextexternalauthornotifychanged"></a>IDebugDocumentTextExternalAuthor::NotifyChanged
Avertit l’hôte que le document source a changé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT NotifyChanged();  
```  
  
#### <a name="parameters"></a>Paramètres  
 Cette méthode ne prend aucun paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode est appelée par un éditeur externe après qu’un document basé sur le fichier de débogueur est modifié et enregistré pour notifier l’hôte que le document source a changé. L’ordinateur hôte puis actualise le document à partir du fichier source.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugDocumentTextExternalAuthor](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)