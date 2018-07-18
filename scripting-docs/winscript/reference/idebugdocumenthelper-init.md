---
title: IDebugDocumentHelper::Init | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.Init
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::Init
ms.assetid: 1dd5a01f-0779-4109-8c6c-f16f5a3835bf
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 45cd57e4ba9e86bf84f927f487c637d61aa5339b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24726319"
---
# <a name="idebugdocumenthelperinit"></a>IDebugDocumentHelper::Init
Le `Init` méthode initialise un programme d’assistance du document de débogage avec un nom et les attributs initiaux.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Init(  
   IDebugApplication*  pda,  
   LPCOLESTR           pszShortName,  
   LPCOLESTR           pszLongName,  
   TEXT_DOC_ATTR       docAttr  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pda`  
 [in] L’application de débogage associée à ce document.  
  
 `pszShortName`  
 [in] Chaîne terminée par le caractère null qui contient le nom court du document.  
  
 `pszLongName`  
 [in] Chaîne terminée par le caractère null qui contient le nom long du document.  
  
 `docAttr`  
 [in] Spécifie les attributs du document texte.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode initialise un programme d’assistance du document de débogage avec un nom et les attributs initiaux.  
  
 Ce document n’apparaît pas dans l’arborescence jusqu'à ce que `IDebugDocumentHelper::Attach` est appelée.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugDocumentHelper::Attach](../../winscript/reference/idebugdocumenthelper-attach.md)   
 [IDebugDocumentHelper (Interface)](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [Constantes TEXT_DOC_ATTR](../../winscript/reference/text-doc-attr-constants.md)