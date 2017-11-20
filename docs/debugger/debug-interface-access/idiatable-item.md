---
title: IDiaTable::Item | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaTable::Item method
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e5c0c810dfd1a17f2fa63e64bf199a5882174aae
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
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
 [out] Retourne un `IUnknown` objet qui représente l’entrée de la table spécifiée.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Une table représente une collection d’objets. En fonction de ces objets, le paramètre de l’élément peut être converti à l’interface appropriée. Par exemple, si une table contient [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) des objets, puis le paramètre de l’élément peut être converti en la `IDiaSegment` interface.  
  
 Il s’agit d’une approche plus courante pour appeler le `QueryInterface` méthode dans le [IDiaTable](../../debugger/debug-interface-access/idiatable.md) interface pour l’interface de l’énumérateur approprié et utiliser des méthodes spécifiques de l’énumérateur pour accéder au contenu de la table. Consultez le [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) interface pour obtenir un exemple.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)