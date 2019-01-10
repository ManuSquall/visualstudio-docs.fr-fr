---
title: IScriptEntry::GetBody | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetBody
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetBody
ms.assetid: 419c8c11-a1f8-4b97-ab00-e8af2b2f9bfc
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3b5eb878bccaa8ed415fd813095e31064bc7e245
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094812"
---
# <a name="iscriptentrygetbody"></a>IScriptEntry::GetBody
Retourne le texte qui correspond au corps d’un `IScriptEntry` bloc de script, un bloc de fonction ou scriptlet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetBody(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pbstr`  
 [out] Le texte qui se trouve dans le corps de l’une des opérations suivantes :  
  
-   Un `IScriptEntry` bloc de script  
  
-   Un `IScriptEntry` dans un bloc de fonction (fonction)  
  
-   Un `IScriptEntry` scriptlet Gestionnaire d’événements  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IScriptEntry](../../winscript/reference/iscriptentry-interface.md)