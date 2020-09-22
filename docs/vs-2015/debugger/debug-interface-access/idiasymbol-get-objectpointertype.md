---
title: IDiaSymbol::get_objectPointerType | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_objectPointerType method
ms.assetid: bce193b9-67b0-4c35-96e5-6a664937322e
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1d8f5251f61b8c513c58f5165fbaecbb9d5f00f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839842"
---
# <a name="idiasymbolget_objectpointertype"></a>IDiaSymbol::get_objectPointerType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère le type du pointeur d’objet pour une méthode de classe.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_objectPointerType (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 à Retourne un objet [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) qui représente le pointeur d’objet pour une méthode de classe.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
> [!NOTE]
> Une valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="remarks"></a>Remarques  
 Cette propriété s’applique uniquement aux symboles dont le type d' [énumération SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) est `SymTagFunctionType` .  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md)
