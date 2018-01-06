---
title: IDebugObject2::IsEncOutdated | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugObject2::IsEncOutdated
helpviewer_keywords: IDebugObject2::IsEncOutdated method
ms.assetid: d3a8c02d-895b-478c-9957-d663130f308e
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 757e533f855ab1bc276e484d46d6866b0dd6ca40
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugobject2isencoutdated"></a>IDebugObject2::IsEncOutdated
Cette méthode détermine si l’état de modifier & Continuer de cet objet ou du conteneur parent est obsolète. Un évaluateur d’expression personnalisée n’implémente pas cette méthode et retourne toujours `E_NOTIMPL`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT IsEncOutdated(  
   BOOL* pfEncOutdated  
);  
```  
  
```csharp  
int IsEncOutdated(  
   out int pfEncOutdated  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pfEncOutdated`  
 [out] Différent de zéro (`TRUE`) si l’état de modifier & Continuer est périmé, zéro (`FALSE`) si elle n’est pas.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
> [!NOTE]
>  Un évaluateur d’expression personnalisées doit toujours retourner `E_NOTIMPL`.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)