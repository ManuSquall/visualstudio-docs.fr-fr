---
title: IDiaSymbol::findChildren | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildren method
ms.assetid: 5fe7573a-e48b-428d-9c17-7421b7209246
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a09a62a2e6b94dbccda3afce4bdd286270149c15
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150036"
---
# <a name="idiasymbolfindchildren"></a>IDiaSymbol::findChildren
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère les enfants du symbole.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT findChildren (   
   enum SymTagEnum   symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `symtag`  
 dans Spécifie les balises de symboles des enfants à récupérer, comme défini dans l' [énumération SymTagEnum](../../debugger/debug-interface-access/symtagenum.md). Affectez à la valeur `SymTagNull` pour tous les enfants à récupérer.  
  
 `name`  
 dans Spécifie le nom des enfants à récupérer. Affectez à la valeur `NULL` pour tous les enfants à récupérer.  
  
 `compareFlags`  
 dans Spécifie les options de comparaison appliquées à la correspondance de noms. Les valeurs de l’énumération d' [énumération NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md) peuvent être utilisées seules ou en combinaison.  
  
 `ppResult`  
 à Retourne un objet [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) qui contient une liste des symboles enfants récupérés.  
  
## <a name="return-value"></a>Valeur renvoyée  
 Retourne `S_OK` si au moins un enfant du symbole a été trouvé, ou retourne `S_FALSE` si aucun enfant n’a été trouvé ; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Cette méthode est identique à l’appel de la méthode [IDiaSession :: findchildren (](../../debugger/debug-interface-access/idiasession-findchildren.md) avec ce symbole comme premier paramètre.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Énumération SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession :: Findchildren (](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [NameSearchOptions, énumération](../../debugger/debug-interface-access/namesearchoptions.md)
