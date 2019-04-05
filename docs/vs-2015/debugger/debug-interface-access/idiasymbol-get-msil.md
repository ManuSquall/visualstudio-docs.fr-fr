---
title: IDiaSymbol::get_msil | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_msil method
ms.assetid: 43a8e003-6856-4726-aa16-c0d4dae7299b
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0474c200f6ef3a5be282aa42b32935d490f2035c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58938803"
---
# <a name="idiasymbolgetmsil"></a>IDiaSymbol::get_msil
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère un indicateur qui spécifie si le symbole fait référence au code de langage MSIL (Microsoft Intermediate Language).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_msil (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne `TRUE` si le symbole fait référence au code MSIL ; sinon, retourne `FALSE`.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
