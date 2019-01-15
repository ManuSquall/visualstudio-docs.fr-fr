---
title: IDiaStackWalkHelper | Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: f498ea6f34522b3eb5ca8eda78f9bb188ea1c241
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53957509"
---
# <a name="idiastackwalkhelper"></a>IDiaStackWalkHelper
Facilite le parcours de la pile utilisant le fichier de base de données (.pdb) de débogage de programme.  
  
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
|[IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)|Lit un bloc de données à partir de l’image de l’exécutable en mémoire.|  
|[IDiaStackWalkHelper::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddress.md)|Recherche dans le frame de pile spécifié pour l’adresse de retour de fonction le plus proche.|  
|[IDiaStackWalkHelper::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddressstart.md)|Recherche dans le frame de pile spécifié pour une adresse de retour à ou près de l’adresse de pile spécifié.|  
|[IDiaStackWalkHelper::frameForVA](../../debugger/debug-interface-access/idiastackwalkhelper-frameforva.md)|Récupère le frame de pile qui contient l’adresse virtuelle spécifiée.|  
|[IDiaStackWalkHelper::symbolForVA](../../debugger/debug-interface-access/idiastackwalkhelper-symbolforva.md)|Récupère le symbole qui contient l’adresse virtuelle spécifiée. **Remarque :**  Symbole doit être du type `SymTagFunctionType` (une valeur comprise entre le [SymTagEnum (énumération)](../../debugger/debug-interface-access/symtagenum.md) énumération).|  
|[IDiaStackWalkHelper::pdataForVA](../../debugger/debug-interface-access/idiastackwalkhelper-pdataforva.md)|Retourne le bloc de données PDATA associé à l’adresse virtuelle spécifiée.|  
|[IDiaStackWalkHelper::imageForVA](../../debugger/debug-interface-access/idiastackwalkhelper-imageforva.md)|Récupère l’adresse virtuelle à partir d’un fichier exécutable, une adresse virtuelle quelque part dans l’espace de mémoire de l’exécutable.|  
  
## <a name="remarks"></a>Notes  
 Cette interface est appelée par le code DIA pour obtenir des informations sur l’exécutable pour construire une liste de frames de pile pendant l’exécution du programme.  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 Une application cliente implémente cette interface pour prendre en charge le parcours de la pile pendant l’exécution du programme. Une instance de cette interface est passée à la [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) ou [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md) méthodes.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : Dia2.h  
  
 Bibliothèque : diaguids.lib  
  
 DLL : msdia80.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces (Kit SDK Debug Interface Access)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)   
 [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)