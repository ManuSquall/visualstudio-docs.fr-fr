---
title: IDiaEnumSourceFiles::Item | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles::Item method
ms.assetid: 3c19d7ed-0232-4b0e-9b10-f33ed9e0c93b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 12fa454b0d91c0656e6f6792e0c77158f304af00
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49925549"
---
# <a name="idiaenumsourcefilesitem"></a>IDiaEnumSourceFiles::Item
Récupère un fichier source au moyen d’un index.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT Item (   
   DWORD            index,  
   IDiaSourceFile** sourceFile  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 index  
 [in] Index de la [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) objet à récupérer. L’index est comprise entre 0 et `count`-1, où `count` est retourné par la [IDiaEnumSourceFiles::get_Count](../../debugger/debug-interface-access/idiaenumsourcefiles-get-count.md) (méthode).  
  
 sourceFile  
 [out] Retourne un [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) objet représentant le fichier source souhaitée.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)