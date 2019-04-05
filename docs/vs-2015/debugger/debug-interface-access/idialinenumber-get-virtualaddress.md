---
title: IDiaLineNumber::get_virtualAddress | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_virtualAddress method
ms.assetid: 9048ef91-a59d-4ad8-90cb-4c13d0989241
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 21bd5364c8fa6d91962dd82b4cbcf8b8c0db90e1
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58938840"
---
# <a name="idialinenumbergetvirtualaddress"></a>IDiaLineNumber::get_virtualAddress
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère l’adresse virtuelle (VA) du bloc.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_virtualAddress (   
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne l’adresse virtuelle du bloc.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas pris en charge. Sinon, retourne un code d'erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
