---
title: IDiaSymbol::get_targetSection | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_targetSection method
ms.assetid: 95382395-da41-4aa8-87f1-5b03da128565
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f4d96e30d443adb6d790c1645c218fb212ce0699
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54987724"
---
# <a name="idiasymbolgettargetsection"></a>IDiaSymbol::get_targetSection
Récupère la section de l’adresse d’une cible de conversion de code.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_targetSection (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Partie de la section d’une adresse de cible de conversion de code.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)