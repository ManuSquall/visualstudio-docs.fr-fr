---
title: IDiaSymbol::get_hasSecurityChecks | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasSecurityChecks method
ms.assetid: 4bb51f62-8645-41a4-bc44-1451010623fd
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b296ad472b747b14dd2c49b52239fea3920aab9b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58951872"
---
# <a name="idiasymbolgethassecuritychecks"></a>IDiaSymbol::get_hasSecurityChecks
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère un indicateur qui spécifie si le module ou la fonction a été compilée avec les vérifications de sécurité de dépassement de mémoire tampon (par exemple, le [/GS (vérification de la sécurité de la mémoire tampon)](http://msdn.microsoft.com/library/8d8a5ea1-cd5e-42e1-bc36-66e1cd7e731e) commutateur de compilateur).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_hasSecurityChecks(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pFlag`  
 [out] Retourne `TRUE` si la fonction a des vérifications de sécurité ; sinon, retourne `FALSE`.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="requirements"></a>Configuration requise  
  
|Spécification|Description|  
|-----------------|-----------------|  
|En-tête :|dia2.h|  
|Version :|DIA SDK 8.0|  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [/GS (vérification de la sécurité des mémoires tampons)](http://msdn.microsoft.com/library/8d8a5ea1-cd5e-42e1-bc36-66e1cd7e731e)
