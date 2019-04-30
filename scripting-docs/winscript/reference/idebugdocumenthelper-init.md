---
title: IDebugDocumentHelper::Init | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 3b399f51fc042aa1ed297ab30a7bf2c9bc4befca
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63000994"
---
# <a name="idebugdocumenthelperinit"></a>IDebugDocumentHelper::Init
Le `Init` méthode Initialise une assistance de document de débogage avec un nom et d’attributs initiaux.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
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
 [in] Chaîne se terminant par null qui contient le nom court du document.  
  
 `pszLongName`  
 [in] Chaîne se terminant par null qui contient le nom long du document.  
  
 `docAttr`  
 [in] Spécifie les attributs du document texte.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode Initialise une assistance de document de débogage avec un nom et d’attributs initiaux.  
  
 Ce document n’apparaît pas dans l’arborescence jusqu'à ce que `IDebugDocumentHelper::Attach` est appelée.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugDocumentHelper::Attach](../../winscript/reference/idebugdocumenthelper-attach.md)   
 [Interface IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [Constantes TEXT_DOC_ATTR](../../winscript/reference/text-doc-attr-constants.md)