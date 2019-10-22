---
title: 'IDebugDocumentHelper :: init | Microsoft Docs'
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
ms.openlocfilehash: 13e6379052707aa44c0fa52f4cb30db2c4c4fa99
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576863"
---
# <a name="idebugdocumenthelperinit"></a>IDebugDocumentHelper::Init
La méthode `Init` Initialise une application d’assistance de document de débogage avec un nom et des attributs initiaux.  
  
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
 dans Application de débogage associée à ce document.  
  
 `pszShortName`  
 dans Chaîne terminée par le caractère null qui contient le nom abrégé du document.  
  
 `pszLongName`  
 dans Chaîne terminée par le caractère null qui contient le nom long du document.  
  
 `docAttr`  
 dans Spécifie des attributs de document texte.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode initialise une application d’assistance de document de débogage avec un nom et des attributs initiaux.  
  
 Ce document n’apparaît pas dans l’arborescence tant que `IDebugDocumentHelper::Attach` n’est pas appelé.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugDocumentHelper :: Attach](../../winscript/reference/idebugdocumenthelper-attach.md)    
 @No__t_1 de l' [interface IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)  
 [Constantes TEXT_DOC_ATTR](../../winscript/reference/text-doc-attr-constants.md)