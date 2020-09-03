---
title: IDiaEnumSourceFiles::Item | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles::Item method
ms.assetid: 3c19d7ed-0232-4b0e-9b10-f33ed9e0c93b
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 62dce70d3ebf05694b453d13e1f11529dd21e8ce
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189774"
---
# <a name="idiaenumsourcefilesitem"></a>IDiaEnumSourceFiles::Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère un fichier source au moyen d’un index.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT Item (   
   DWORD            index,  
   IDiaSourceFile** sourceFile  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 index  
 dans Index de l’objet [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) à récupérer. L’index se trouve dans la plage de 0 à `count` -1, où `count` est retourné par la méthode [IDiaEnumSourceFiles :: get_Count](../../debugger/debug-interface-access/idiaenumsourcefiles-get-count.md) .  
  
 sourceFile  
 à Retourne un objet [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) représentant le fichier source souhaité.  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
