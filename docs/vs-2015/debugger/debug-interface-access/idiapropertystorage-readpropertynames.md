---
title: IDiaPropertyStorage::ReadPropertyNames | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadPropertyNames
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f3f6d3ac520a396b5207767a3fec0913c801c287
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62537353"
---
# <a name="idiapropertystoragereadpropertynames"></a>IDiaPropertyStorage::ReadPropertyNames
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère les noms de chaîne correspondants pour les identificateurs de propriété donnés.  
  
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
 dans Nombre d’ID de propriété dans `rgpropid` .  
  
 `rgpropid`  
 dans Tableau d’ID de propriété pour lequel obtenir les noms ( `PROPID` est défini dans WTypes. h en tant que `ULONG` ).  
  
 `rglpwstrName`  
 [in, out] Tableau de noms de propriété pour les ID de propriété spécifiés. Le tableau doit être pré-alloué pour contenir le nombre demandé de noms de propriétés et doit pouvoir contenir au moins `cpropid``BSTR` chaînes.  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne `S_OK` ; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Les noms de propriété retournés doivent être libérés (en appelant la `SysFreeString` fonction) lorsqu’ils ne sont plus nécessaires.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
