---
title: IDiaTable::Item | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable::Item method
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6112a4580a68a98407723afab1ec3310d0f1cca9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62574799"
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
 dans Index de l’entrée de table dans la plage de 0 à `count` -1, où `count` est retourné par la méthode [IDiaTable :: get_Count](../../debugger/debug-interface-access/idiatable-get-count.md).  
  
 `element`  
 à Retourne un `IUnknown` objet qui représente l’entrée de table spécifiée.  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 Une table représente une collection d’objets. En fonction de ces objets, le paramètre d’élément peut être casté en interface appropriée. Par exemple, si une table contient des objets [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) , le paramètre d’élément peut être casté en `IDiaSegment` interface.  
  
 Une approche plus courante consiste à appeler la `QueryInterface` méthode dans l’interface [IDiaTable](../../debugger/debug-interface-access/idiatable.md) pour l’interface d’énumérateur appropriée et à utiliser les méthodes spécifiques de l’énumérateur pour accéder au contenu de la table. Pour obtenir un exemple, consultez l’interface [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) .  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaTable :: get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
