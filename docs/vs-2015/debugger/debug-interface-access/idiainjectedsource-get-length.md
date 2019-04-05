---
title: IDiaInjectedSource::get_length | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_length method
ms.assetid: 38b88b8b-c2e0-4b2d-8b8b-9ff373733e78
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7ce9a927f8e2e732bd5b74d0f58afa40a7cf8efa
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58952476"
---
# <a name="idiainjectedsourcegetlength"></a>IDiaInjectedSource::get_length
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère le nombre d’octets de code.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_length (   
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne le nombre d’octets de code.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas pris en charge. Sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 La valeur retournée par cette méthode est la longueur du code source et est la même valeur que celles retournées par la [IDiaInjectedSource::get_source](../../debugger/debug-interface-access/idiainjectedsource-get-source.md) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)   
 [IDiaInjectedSource::get_source](../../debugger/debug-interface-access/idiainjectedsource-get-source.md)
