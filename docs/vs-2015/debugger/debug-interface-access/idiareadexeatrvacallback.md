---
title: IDiaReadExeAtRVACallback | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
- IDiaReadExeAtRVACallback interface
ms.assetid: b2892513-3952-4f99-9b98-60cb9b1fdc91
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 75bdd6e2e8c5ee8144b68253fa691792a267a5d5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47508134"
---
# <a name="idiareadexeatrvacallback"></a>IDiaReadExeAtRVACallback
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDiaReadExeAtRVACallback](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiareadexeatrvacallback).  
  
Permet à une application cliente fournir des octets d’un fichier exécutable comme spécifié par une adresse virtuelle relative.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDiaReadExeAtRVACallback : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDiaReadExeAtRVACallback`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDiaReadExeAtRVACallback::ReadExecutableAtRVA](../../debugger/debug-interface-access/idiareadexeatrvacallback-readexecutableatrva.md)|Lit le nombre spécifié d’octets à partir du spécifié adresse virtuelle relative (RVA) à partir du fichier exécutable.|  
  
## <a name="remarks"></a>Notes  
 L’application cliente implémente cette interface afin de fournir les octets de l’exécutable à l’aide d’une adresse virtuelle relative dans le fichier de l’exécutable. Pour utiliser un décalage de fichier absolu, implémenter la [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) interface.  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 Cette méthode est implémentée par l’application cliente et passée à la [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) méthode comme une méthode alternative pour la lecture du fichier.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : Dia2.h  
  
 Bibliothèque : diaguids.lib  
  
 DLL : msdia80.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces (SDK Debug Interface Access)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)



