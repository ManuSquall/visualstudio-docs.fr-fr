---
title: IDiaSymbol::get_types | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_types method
ms.assetid: 5f056e0c-e15b-4e00-8f78-aadc8574f7ea
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6521d2a7ffdf5bb285f571e0d3975626f34d84d1
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31470034"
---
# <a name="idiasymbolgettypes"></a>IDiaSymbol::get_types
Récupère un tableau de types spécifiques au compilateur pour ce symbole.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_types (   
   DWORD       cTypes,  
   DWORD*      pcTypes,  
   IDiaSymbol* types[]  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cTypes`  
 [in] Taille de la mémoire tampon pour stocker les données.  
  
 `pcTypes`  
 [out] Retourne le nombre de types écrits, ou, si le `types` paramètre est `NULL`, puis le nombre total de types disponibles.  
  
 `types[]`  
 [out] Un tableau qui doit être remplie avec les [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objets qui représentent tous les types de ce symbole.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)