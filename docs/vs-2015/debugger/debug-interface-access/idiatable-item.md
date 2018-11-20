---
title: IDiaTable::Item | Microsoft Docs
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
- IDiaTable::Item method
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2d1ebea7d657683d4174784a92ca2213851dcae9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51816734"
---
# <a name="idiatableitem"></a>IDiaTable::Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère une référence à l’entrée spécifiée dans la table.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT Item (   
   DWORD      index,  
   IUnknown** element  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `index`  
 [in] L’index de l’entrée de table dans la plage 0 à `count`-1, où `count` est retourné par la [IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)(méthode).  
  
 `element`  
 [out] Retourne un `IUnknown` objet qui représente l’entrée de table spécifié.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Une table représente une collection d’objets. En fonction de ces objets, le paramètre de l’élément peut être casté vers l’interface appropriée. Par exemple, si une table contient [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) objets, puis le paramètre de l’élément peut être casté en le `IDiaSegment` interface.  
  
 Il est une approche plus courante pour appeler le `QueryInterface` méthode dans le [IDiaTable](../../debugger/debug-interface-access/idiatable.md) interface pour l’interface de l’énumérateur approprié et utiliser des méthodes spécifiques de l’énumérateur pour accéder au contenu de la table. Consultez le [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) interface pour obtenir un exemple.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)



