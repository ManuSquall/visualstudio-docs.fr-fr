---
title: IDispError::GetSource | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.GetSource
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetSource
ms.assetid: 20def54c-a67c-4102-babf-6f0704e5fc5c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8a84640f020a1ff255b8c7e5dd753752e0d310a7
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446884"
---
# <a name="idisperrorgetsource"></a>IDispError::GetSource
Retourne le ProgID dépendants de la langue pour la classe ou d’une application qui a généré l’erreur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetSource(  
   BSTR*  pbstrSource  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pbstrSource`  
 [out] Chaîne qui contient un identificateur programmatique, sous la forme `progname.objectname`.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode est utilisée pour déterminer la classe ou une application où l’exception s’est produite. L’identificateur programmatique peut-être être retournée dans la langue spécifiée par l’identificateur de paramètres régionaux (LCID) fourni au moment de l’appel.  
  
> [!NOTE]
> Cette méthode n’est pas implémentée.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDispError](../../winscript/reference/idisperror-interface.md)