---
title: IDiaEnumLineNumbers::Next | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumLineNumbers::Next method
ms.assetid: 363d5b40-1316-4ab8-836f-63637f619e0a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f06a7a8e72e6d882acdad5876aae7e43e1242338
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="idiaenumlinenumbersnext"></a>IDiaEnumLineNumbers::Next
Récupère un nombre spécifié de numéros de ligne dans la séquence d’énumération.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT Next (   
   ULONG            celt,  
   IDiaLineNumber** rgelt,  
   ULONG*           pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 celt  
 [in] Le nombre de numéros de ligne dans l’énumérateur doit être récupéré.  
  
 rgelt  
 [out] Retourne un tableau de [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) les objets qui représentent les numéros de ligne de votre choix.  
  
 pceltFetched  
 [out] Retourne le nombre de numéros de ligne dans l’énumérateur d’extraction.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` s’il n’y aucun numéro de ligne plus. Sinon, retourne un code d'erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)   
 [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)