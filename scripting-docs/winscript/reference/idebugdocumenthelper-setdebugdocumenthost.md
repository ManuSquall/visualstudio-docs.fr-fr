---
title: IDebugDocumentHelper::SetDebugDocumentHost | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentHelper.SetDebugDocumentHost
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentHelper::SetDebugDocumentHost
ms.assetid: b26a03c3-8a3f-47b0-b916-4c65d5500f10
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5d1377edaa5b10a7ebb06713e512010be010a9d3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthelpersetdebugdocumenthost"></a>IDebugDocumentHelper::SetDebugDocumentHost
Définit le `IDebugDocumentHost` pour ce document.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetDebugDocumentHost(  
   IDebugDocumentHost*  pddh  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pddh`  
 [in] L’hôte de document de débogage.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Le `IDebugDocumentHost` interface est utilisée pour la coloration de syntaxe de l’hôte à puce, l’extraction de texte différée et retourner des objets de commande qui vient d’être créé des contextes de document.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugDocumentHelper (Interface)](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [Interface IDebugDocumentHost](../../winscript/reference/idebugdocumenthost-interface.md)