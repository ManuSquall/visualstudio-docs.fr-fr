---
title: IDiaStackWalkHelper | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2 interface
ms.assetid: d66e5c84-565d-494e-8486-f91db9a34548
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1dac563f99697a8e43b5f7db9831e075c0ed7087
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
---
# <a name="idiastackwalkhelper"></a>IDiaStackWalkHelper
Facilite le parcours de la pile à l’aide du fichier de base de données (.pdb) de débogage de programme.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
IDiaStackWalkHelper: IUnknown  
  
```  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre VTable  
 Le tableau ci-dessous présente les méthodes de `IDiaStackWalkHelper`:  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDiaStackWalkHelper::get_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-get-registervalue.md)|Récupère la valeur d’un Registre.|  
|[IDiaStackWalkHelper::put_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-put-registervalue.md)|Définit la valeur d’un Registre.|  
|[IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)|Lit un bloc de données à partir de l’image de l’exécutable dans la mémoire.|  
|[IDiaStackWalkHelper::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddress.md)|Recherche dans le frame de pile spécifié pour l’adresse de retour de fonction le plus proche.|  
|[IDiaStackWalkHelper::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddressstart.md)|Recherche dans le frame de pile spécifié pour une adresse d’expéditeur à ou près de l’adresse de la pile spécifiée.|  
|[IDiaStackWalkHelper::frameForVA](../../debugger/debug-interface-access/idiastackwalkhelper-frameforva.md)|Récupère le frame de pile qui contient l’adresse virtuelle spécifiée.|  
|[IDiaStackWalkHelper::symbolForVA](../../debugger/debug-interface-access/idiastackwalkhelper-symbolforva.md)|Récupère le symbole qui contient l’adresse virtuelle spécifiée. **Remarque :** symbole doit avoir le type `SymTagFunctionType` (une valeur à partir de la [symtagenum, énumération](../../debugger/debug-interface-access/symtagenum.md) énumération).|  
|[IDiaStackWalkHelper::pdataForVA](../../debugger/debug-interface-access/idiastackwalkhelper-pdataforva.md)|Retourne le bloc de données PDATA associé à l’adresse virtuelle spécifiée.|  
|[IDiaStackWalkHelper::imageForVA](../../debugger/debug-interface-access/idiastackwalkhelper-imageforva.md)|Récupère l’adresse virtuelle initiale d’un fichier exécutable, une adresse virtuelle quelque part dans l’espace de mémoire de l’exécutable donnée.|  
  
## <a name="remarks"></a>Notes  
 Cette interface est appelée par le code DIA pour obtenir des informations sur le fichier exécutable pour construire une liste de frames de pile pendant l’exécution du programme.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Une application cliente implémente cette interface pour prendre en charge le parcours de la pile lors de l’exécution du programme. Une instance de cette interface est passée à la [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) ou [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md) méthodes.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : Dia2.h  
  
 Bibliothèque : diaguids.lib  
  
 DLL : msdia80.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [SymTagEnum (énumération)](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)   
 [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)