---
title: 'IDebugDocumentHost :: OnCreateDocumentContext | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.OnCreateDocumentContext
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::OnCreateDocumentContext
ms.assetid: 080c8604-cfd7-484e-a337-15040870e683
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3fdfa64f66288cba47dec7c498db15238e55f954
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72569109"
---
# <a name="idebugdocumenthostoncreatedocumentcontext"></a>IDebugDocumentHost::OnCreateDocumentContext
Avertit l’hôte qu’un nouveau contexte de document est en cours de création et permet à l’hôte de retourner éventuellement un contrôle inconnu pour le nouveau contexte.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT OnCreateDocumentContext(  
   IUnknown**  ppunkOuter  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppunkOuter`  
 à Objet qui contrôle le nouveau contexte.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_NOTIMPL`|L’hôte ne fournit pas d’objet de contrôle.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode permet à l’hôte d’ajouter de nouvelles fonctionnalités aux contextes de document fournis par l’assistance. Cette méthode peut retourner **E_NOTIMPL** ou un objet externe null, auquel cas l’appelant est chargé de créer le contexte.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugDocumentHost](../../winscript/reference/idebugdocumenthost-interface.md)