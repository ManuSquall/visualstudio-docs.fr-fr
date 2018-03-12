---
title: IDiaAddressMap | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap interface
ms.assetid: e6467529-508c-4328-85d7-89444ae4d1c1
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 6cdd8c9d2e581df3e7b0ebeba092a212fb7a89f5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idiaaddressmap"></a>IDiaAddressMap
Permet de contrôler comment le SDK DIA calcule virtuels et relatifs des adresses virtuelles pour les objets de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDiaAddressMap : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDiaAddressMap`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)|Indique si une table d’adresses a été établie pour une session particulière.|  
|[IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)|Spécifie si le mappage d’adresse doit être utilisé pour traduire les adresses de symbole.|  
|[IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)|Indique si le calcul et l’utilisation des adresses virtuelles relatives est activée.|  
|[IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)|Permet au client activer ou désactiver le calcul d’adresses virtuelles relatives.|  
|[IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)|Récupère l’alignement d’image actuelle.|  
|[IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)|Définit l’alignement d’image.|  
|[IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)|Définit l’image en-têtes pour la traduction d’adresses virtuelles relatives.|  
|[IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)|Fournit un mappage d’adresse pour prendre en charge les traductions de disposition d’image.|  
  
## <a name="remarks"></a>Notes  
 Le contrôle fourni par cette interface est encapsulé dans deux jeux de données que vous fournissez : en-têtes de l’image et de mappages d’adresses. La plupart des clients utilisent le [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) méthode pour rechercher les informations de débogage approprié pour une image et la méthode peuvent découvrir généralement toutes les données nécessaires en-têtes et des cartes de lui-même. Toutefois, certains clients implémentent spécialisées de traitement et de recherche de données. Ces clients utilisent les méthodes de la `IDiaAddressMap` interface afin de fournir la DIA SDK avec les résultats de recherche.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Cette interface est disponible à partir de l’objet de session DIA. Le client appelle le `QueryInterface` méthode sur DIA objet interface de session, généralement [IDiaSession](../../debugger/debug-interface-access/idiasession.md), pour récupérer le `IDiaAddressMap` interface.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : Dia2.h  
  
 Bibliothèque : diaguids.lib  
  
 DLL : msdia80.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)