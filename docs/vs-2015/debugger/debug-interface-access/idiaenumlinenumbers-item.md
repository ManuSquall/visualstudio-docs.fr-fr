---
title: IDiaEnumLineNumbers::Item | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumLineNumbers::Item method
ms.assetid: 08efbeaf-22f7-49e9-96a8-bb906dfe4fd8
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 630c86e463cdc6ff838fad00d5d02e6f67c729d7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58950158"
---
# <a name="idiaenumlinenumbersitem"></a>IDiaEnumLineNumbers::Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère un numéro de ligne au moyen d’un index.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT Item (   
   DWORD            index,  
   IDiaLineNumber** lineNumber  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 index  
 [in] Index de la [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) objet à récupérer. L’index est comprise entre 0 et `count`-1, où `count` est retourné par la [IDiaEnumLineNumbers::get_Count](../../debugger/debug-interface-access/idiaenumlinenumbers-get-count.md) (méthode).  
  
 lineNumber  
 [out] Retourne un [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) objet représentant le numéro de ligne souhaité.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
