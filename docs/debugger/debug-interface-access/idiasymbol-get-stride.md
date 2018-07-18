---
title: IDiaSymbol::get_stride | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 4264742a-3d91-44b9-9d14-87adbc77f0f0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 30f32bd7f69d303ec6050534f54e389cd2f69873
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31469696"
---
# <a name="idiasymbolgetstride"></a>IDiaSymbol::get_stride
Récupère la longueur de la matrice ou un tableau a parcouru le.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_stride(   
   DWORD* pRetVal);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Un pointeur vers un `DWORD` qui contient la largeur de numérisation.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)