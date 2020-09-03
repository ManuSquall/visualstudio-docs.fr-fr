---
title: IDiaEnumSymbolsByAddr::Next | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::Next method
ms.assetid: a1320587-7ce7-401f-9548-2f8bcece5cc3
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fc58c8da54380b8a835d64fcc5dc079bb8d8023e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189647"
---
# <a name="idiaenumsymbolsbyaddrnext"></a>IDiaEnumSymbolsByAddr::Next
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère les symboles suivants dans l’ordre par adresse.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT Next (   
   ULONG        celt,   
   IDiaSymbol** rgelt,  
   ULONG*       pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 celt  
 dans Nombre de symboles dans l’énumérateur à récupérer.  
  
 rgelt  
 à Tableau à remplir avec l’objet [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) qui représente les symboles souhaités.  
  
 pceltFetched  
 à Retourne le nombre de symboles dans l’énumérateur extrait.  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` s’il n’y a plus de symboles. Sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 Cette méthode met à jour la position de l’énumérateur en fonction du nombre d’éléments extraits.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
