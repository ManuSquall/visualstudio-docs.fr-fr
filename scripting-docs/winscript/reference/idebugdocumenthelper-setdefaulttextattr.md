---
title: 'IDebugDocumentHelper :: SetDefaultTextAttr | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.SetDefaultTextAttr
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::SetDefaultTextAttr
ms.assetid: 019a4191-0019-4376-bf70-89b33e7369de
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ea63f028497f1eb90803f59423f608d0a42960cf
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574636"
---
# <a name="idebugdocumenthelpersetdefaulttextattr"></a>IDebugDocumentHelper::SetDefaultTextAttr
Définit les attributs par défaut à utiliser pour le texte qui n’est pas dans un bloc de script.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SetDefaultTextAttr(  
   SOURCE_TEXT_ATTR  staTextAttr  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `staTextAttr`  
 Attributs de texte source par défaut.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 À moins que les attributs par défaut ne soient modifiés par cette méthode, les attributs par défaut du texte en dehors d’un bloc de script sont SOURCETEXT_ATTR_NONSOURCE. L’interface utilisateur peut utiliser ces informations pour marquer le texte en dehors des blocs de script comme étant en lecture seule.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)  
 [Énumération SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)