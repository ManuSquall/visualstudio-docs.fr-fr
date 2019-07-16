---
title: IDiaSymbol::get_isAcceleratorPointerTagLiveRange | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: d195aec4-6d3c-42e0-88a5-3d463539f0b8
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5a53faf8c9395867b570909ac4d34cf329da12c6
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2019
ms.locfileid: "68149455"
---
# <a name="idiasymbolgetisacceleratorpointertagliverange"></a>IDiaSymbol::get_isAcceleratorPointerTagLiveRange
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère un indicateur qui indique si le symbole correspond à la *symbole de plage définition* pour le composant de la balise d’une variable de pointeur dans le code compilé pour un accélérateur de l’AMP C++. Le symbole de plage de définition est l’emplacement d’une variable pour une plage d’adresses.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
