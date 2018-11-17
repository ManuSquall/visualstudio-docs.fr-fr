---
title: IDiaPropertyStorage::ReadPropertyNames | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadPropertyNames
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8523dfb795f63abdecd9be1f08ec68371355fbde
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51759567"
---
# <a name="idiapropertystoragereadpropertynames"></a>IDiaPropertyStorage::ReadPropertyNames
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère correspondant de noms de chaîne pour donné des identificateurs de propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ReadPropertyNames (  
   ULONG         cpropid,  
   PROPID const* rgpropid,  
   BSTR*         rglpwstrName  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cpropid`  
 [in] Nombre d’ID de propriété dans `rgpropid`.  
  
 `rgpropid`  
 [in] Tableau d’ID de propriété pour laquelle obtenir les noms (`PROPID` est défini dans WTypes.h comme un `ULONG`).  
  
 `rglpwstrName`  
 [in, out] Tableau des noms de propriété pour les ID de propriété spécifiée. Le tableau doit être alloué pour contenir le nombre demandé de noms de propriétés au préalable et doit être en mesure de contenir au moins `cpropid``BSTR` chaînes.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Les noms de propriété retournée doivent être libérées (en appelant le `SysFreeString` (fonction)) lorsqu’ils ne sont plus nécessaires.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)



