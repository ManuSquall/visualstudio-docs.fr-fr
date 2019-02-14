---
title: IDiaTable::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable::Item method
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9bf9ad425b703cbaa15378200260061304223607
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55040175"
---
# <a name="idiatableitem"></a>IDiaTable::Item
Récupère une référence à l’entrée spécifiée dans la table.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
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
  
## <a name="remarks"></a>Remarques  
 Une table représente une collection d’objets. En fonction de ces objets, le paramètre de l’élément peut être casté vers l’interface appropriée. Par exemple, si une table contient [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) objets, puis le paramètre de l’élément peut être casté en le `IDiaSegment` interface.  
  
 Il est une approche plus courante pour appeler le `QueryInterface` méthode dans le [IDiaTable](../../debugger/debug-interface-access/idiatable.md) interface pour l’interface de l’énumérateur approprié et utiliser des méthodes spécifiques de l’énumérateur pour accéder au contenu de la table. Consultez le [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) interface pour obtenir un exemple.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)