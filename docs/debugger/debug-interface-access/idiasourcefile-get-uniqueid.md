---
title: IDiaSourceFile::get_uniqueId | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_uniqueId method
ms.assetid: e0b8dbc0-6061-4f31-bead-2cd72be44e41
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3714ce733b0388e3ac462a9495360171971a6750
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31460558"
---
# <a name="idiasourcefilegetuniqueid"></a>IDiaSourceFile::get_uniqueId
Récupère une valeur de clé entier simple qui est unique pour cette image.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_uniqueId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne une valeur de clé entier simple qui est unique pour cette image.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Comparaison de clés plutôt que des chaînes peuvent accélérer le traitement des numéros de ligne.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)