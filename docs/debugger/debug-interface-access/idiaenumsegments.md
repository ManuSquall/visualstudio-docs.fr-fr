---
title: IDiaEnumSegments | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments interface
ms.assetid: 0c9edd5e-b9ce-43e1-a791-cd4c5d16d923
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 30e359192ea6d19d6bc6e31de3c91943bda2deee
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37056868"
---
# <a name="idiaenumsegments"></a>IDiaEnumSegments
Énumère les différents segments contenus dans la source de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDiaEnumSegments : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDiaEnumSegments`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDiaEnumSegments::get__NewEnum](../../debugger/debug-interface-access/idiaenumsegments-get-newenum.md)|Récupère le [IEnumVARIANT Interface](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant) version de cet énumérateur.|  
|[IDiaEnumSegments::get_Count](../../debugger/debug-interface-access/idiaenumsegments-get-count.md)|Récupère le nombre de segments.|  
|[IDiaEnumSegments::Item](../../debugger/debug-interface-access/idiaenumsegments-item.md)|Récupère un segment au moyen d’un index.|  
|[IDiaEnumSegments::Next](../../debugger/debug-interface-access/idiaenumsegments-next.md)|Récupère un nombre spécifié de segments dans la séquence d’énumération.|  
|[IDiaEnumSegments::Skip](../../debugger/debug-interface-access/idiaenumsegments-skip.md)|Ignore un nombre spécifié de segments dans une séquence d’énumération.|  
|[IDiaEnumSegments::Reset](../../debugger/debug-interface-access/idiaenumsegments-reset.md)|Réinitialise une séquence d’énumération au début.|  
|[IDiaEnumSegments::Clone](../../debugger/debug-interface-access/idiaenumsegments-clone.md)|Crée un énumérateur qui contient le même état d’énumération que l’énumérateur en cours.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 Obtenez cette interface en appelant le `QueryInterface` méthode sur un [IDiaTable](../../debugger/debug-interface-access/idiatable.md) objet. Consultez l’exemple pour plus d’informations.  
  
## <a name="example"></a>Exemple  
 Cet exemple montre comment obtenir le `IDiaEnumSections` interface à partir d’une table. Pour obtenir un exemple plus complet de l’utilisation de segments, consultez le [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) interface.  
  
```C++  
void ShowSegments(IDiaTable *pTable, IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumSegments> pSegments;  
    if ( SUCCEEDED( pTable->QueryInterface(  
                                __uuidof( IDiaEnumSegments ),  
                                (void**)&pSegments )  
                  )  
       )  
    {  
        // Do something with this enumeration  
    }  
}  
```  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : Dia2.h  
  
 Bibliothèque : diaguids.lib  
  
 DLL : msdia80.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces (SDK Debug Interface Access)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)