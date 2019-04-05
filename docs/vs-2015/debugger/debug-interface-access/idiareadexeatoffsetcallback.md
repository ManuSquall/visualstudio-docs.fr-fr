---
title: IDiaReadExeAtOffsetCallback | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtOffsetCallback interface
ms.assetid: 3c961641-3ce3-4bc3-bd6e-a802fa3bec49
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f7e24257402ddb546df63753bed62add2d33c512
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58947765"
---
# <a name="idiareadexeatoffsetcallback"></a>IDiaReadExeAtOffsetCallback
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Permet à une application cliente fournir des octets d’un fichier exécutable, tel que spécifié par la position de fichier.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDiaReadExeAtOffsetCallback : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDiaReadExeAtOffsetCallback`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDiaReadExeAtOffsetCallback::ReadExecutableAt](../../debugger/debug-interface-access/idiareadexeatoffsetcallback-readexecutableat.md)|Lit le nombre spécifié d’octets commençant au décalage spécifié à partir d’un fichier exécutable.|  
  
## <a name="remarks"></a>Notes  
 L’application cliente implémente cette interface afin de fournir les octets de l’exécutable à l’aide d’un offset absolu dans le fichier de l’exécutable. Pour utiliser une adresse virtuelle relative, implémenter la [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) interface.  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 Cette méthode est implémentée par l’application cliente et passée à la [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) méthode comme une méthode alternative pour la lecture du fichier.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : Dia2.h  
  
 Bibliothèque : diaguids.lib  
  
 DLL : msdia80.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces (Kit SDK Debug Interface Access)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
