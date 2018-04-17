---
title: IDiaStackWalker | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker interface
ms.assetid: 4a61a22a-9cf8-4ea1-9e6e-b42f96872d40
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8f50eede5ce9420e610c3859e5b54e41c9b88afd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="idiastackwalker"></a>IDiaStackWalker
Fournit des méthodes pour effectuer une pile de remonter à l’aide des informations dans le fichier .pdb.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDiaStackWalker: IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDiaStackWalker`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)|Récupère un énumérateur de frame de pile pour x86 plateformes.|  
|[IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)|Récupère un énumérateur de frame de pile pour un type de plateforme spécifique.|  
  
## <a name="remarks"></a>Notes  
 Cette interface est utilisée pour obtenir une liste de frames de pile pour un module chargé. Chacune des méthodes est passé un [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) objet (implémenté par l’application cliente), qui fournit les informations nécessaires pour créer la liste de frames de pile.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Cette interface est obtenue en appelant le `CoCreateInstance` méthode avec l’identificateur de classe `CLSID_DiaStackWalker` et l’ID de l’interface de `IID_IDiaStackWalker`. L’exemple montre comment cette interface est obtenue.  
  
## <a name="example"></a>Exemple  
 Cet exemple montre comment obtenir le `IDiaStackWalker` interface.  
  
```C++  
  
      IDiaStackWalker* pStackWalker;  
HRESULT hr = CoCreateInstance(CLSID_DiaStackWalker,  
                              NULL,  
                              CLSCTX_INPROC_SERVER,  
                              IID_IDiaStackWalker,  
                              (void**) &pStackWalker);  
if (FAILED(hr))  
{  
    // Report error and exit  
}  
```  
  
## <a name="requirements"></a>Spécifications  
 En-tête : Dia2.h  
  
 Bibliothèque : diaguids.lib  
  
 DLL : msdia80.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)