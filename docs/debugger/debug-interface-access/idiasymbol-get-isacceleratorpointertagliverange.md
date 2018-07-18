---
title: IDiaSymbol::get_isAcceleratorPointerTagLiveRange | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: d195aec4-6d3c-42e0-88a5-3d463539f0b8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 91fc97cafdb3037bb3cca4c93ee874ee329d794c
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31467286"
---
# <a name="idiasymbolgetisacceleratorpointertagliverange"></a>IDiaSymbol::get_isAcceleratorPointerTagLiveRange
Récupère un indicateur qui indique si le symbole correspond à la *symbole de plage définition* pour le composant de balise d’une variable de pointeur dans le code compilé pour un accélérateur AMP de C++. Le symbole de plage de définition est l’emplacement d’une variable pour une plage d’adresses.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_isAcceleratorPointerTagLiveRange(   
   BOOL* pFlag);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pFlag`  
 [out] Un pointeur vers un `BOOL` qui indique si le symbole correspond au symbole de plage de définition.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)