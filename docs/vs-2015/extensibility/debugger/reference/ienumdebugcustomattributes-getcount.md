---
title: IEnumDebugCustomAttributes::GetCount | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEnumCustomAttributes::GetCount
helpviewer_keywords:
- IEnumDebugCustomAttributes::GetCount
ms.assetid: fafe826f-4ebf-4572-b2a3-d5dd2916c12f
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e913d3092dbeee4bc7a5bfbfc2d722b3d202b4fb
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51772870"
---
# <a name="ienumdebugcustomattributesgetcount"></a>IEnumDebugCustomAttributes::GetCount
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtient le nombre d’attributs personnalisés dans un énumérateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetCount(   
   ULONG* pcelt  
);  
```  
  
```csharp  
int GetCount(  
   out uint pcelt  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pcelt`  
 [out] Retourne le nombre d’éléments dans l’énumération.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Cette méthode ne fait pas partie de l’interface d’énumération COM habituel qui spécifie que seules `Next`, `Clone`, `Skip`, et `Reset` doivent être implémentées.  
  
## <a name="see-also"></a>Voir aussi  
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)

