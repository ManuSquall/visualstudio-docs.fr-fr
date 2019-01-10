---
title: IDebugDocumentHost::OnCreateDocumentContext | Microsoft Docs
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
ms.openlocfilehash: c0f8ce73e05fa8dd163564184361254fd58163ee
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096332"
---
# <a name="idebugdocumenthostoncreatedocumentcontext"></a>IDebugDocumentHost::OnCreateDocumentContext
Avertit l’hôte qu’un nouveau contexte de document est créé et permet à l’hôte pour éventuellement retourner un contrôle inconnu pour le nouveau contexte.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT OnCreateDocumentContext(  
   IUnknown**  ppunkOuter  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppunkOuter`  
 [out] Objet qui contrôle le nouveau contexte.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_NOTIMPL`|L’hôte ne fournit pas un objet de contrôle.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode permet à l’hôte à ajouter de nouvelles fonctionnalités pour les contextes de document d’assistance fournies. Cette méthode peut retourner **E_NOTIMPL** ou un objet externe null, auquel cas l’appelant est responsable de la création du contexte.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugDocumentHost](../../winscript/reference/idebugdocumenthost-interface.md)