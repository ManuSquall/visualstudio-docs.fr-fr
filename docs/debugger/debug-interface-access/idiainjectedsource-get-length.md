---
title: IDiaInjectedSource::get_length | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_length method
ms.assetid: 38b88b8b-c2e0-4b2d-8b8b-9ff373733e78
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9d6cd689989cb622e0e2c70c89d26f47238fcc58
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49917440"
---
# <a name="idiainjectedsourcegetlength"></a>IDiaInjectedSource::get_length
Récupère le nombre d’octets de code.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
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