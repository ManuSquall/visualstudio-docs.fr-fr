---
title: IDebugDocumentHost::OnCreateDocumentContext | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 55598a4191d421d3aea01d27cc7991b70bd6a019
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24726719"
---
# <a name="idebugdocumenthostoncreatedocumentcontext"></a>IDebugDocumentHost::OnCreateDocumentContext
Avertit l’hôte qu’un nouveau contexte de document est créé et permet à l’hôte pour éventuellement retourner un contrôle inconnu pour le nouveau contexte.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT OnCreateDocumentContext(  
   IUnknown**  ppunkOuter  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppunkOuter`  
 [out] Objet qui contrôle le nouveau contexte.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_NOTIMPL`|L’hôte ne fournit pas un objet de contrôle.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode permet à l’hôte ajouter de nouvelles fonctionnalités pour les contextes de document fournie par l’application d’assistance. Cette méthode peut retourner **E_NOTIMPL** ou un objet externe null, auquel cas l’appelant est responsable de la création du contexte.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugDocumentHost](../../winscript/reference/idebugdocumenthost-interface.md)