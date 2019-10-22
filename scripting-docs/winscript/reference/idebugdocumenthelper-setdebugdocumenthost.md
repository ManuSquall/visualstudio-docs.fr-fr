---
title: 'IDebugDocumentHelper :: SetDebugDocumentHost | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.SetDebugDocumentHost
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::SetDebugDocumentHost
ms.assetid: b26a03c3-8a3f-47b0-b916-4c65d5500f10
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b32d14f3a7d65bee7bdb587a35dfe05bb06f5e1e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574658"
---
# <a name="idebugdocumenthelpersetdebugdocumenthost"></a>IDebugDocumentHelper::SetDebugDocumentHost
Définit la `IDebugDocumentHost` pour ce document.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SetDebugDocumentHost(  
   IDebugDocumentHost*  pddh  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pddh`  
 dans Hôte de document de débogage.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 L’interface `IDebugDocumentHost` est utilisée pour la coloration de la syntaxe de l’hôte intelligent, l’extraction de texte différé et le renvoi d’objets de contrôle pour les contextes de document nouvellement créés.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)  
 [Interface IDebugDocumentHost](../../winscript/reference/idebugdocumenthost-interface.md)