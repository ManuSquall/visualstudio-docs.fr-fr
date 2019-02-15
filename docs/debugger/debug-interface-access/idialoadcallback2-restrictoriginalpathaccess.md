---
title: IDiaLoadCallback2::RestrictOriginalPathAccess | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictOriginalPathAccess method
ms.assetid: 31fde3af-2824-4b0f-8d0d-cee6046596f6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 27bf39aea5b095860f9e5aebf864abb4df6bf86d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54964390"
---
# <a name="idialoadcallback2restrictoriginalpathaccess"></a>IDiaLoadCallback2::RestrictOriginalPathAccess
Détermine s’il est OK rechercher un fichier .pdb dans le répertoire de débogage d’origine.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT RestrictOriginalPathAccess ();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Un code de retour autre que `S_OK` empêche la recherche d’un fichier .pdb dans le répertoire de débogage d’origine. Le répertoire de débogage d’origine est le chemin d’accès au fichier de symboles compilé dans le fichier exécutable lorsque le débogage est activé. Ce chemin d’accès n’est pas nécessairement le même que le chemin d’accès où se trouve l’exécutable.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)