---
title: IDiaSymbol::get_builtInKind | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 953e6dba-582e-4b76-b736-898b92e5693e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8a53bea46c2abcffa820da132162d7efb55c3da9
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31462618"
---
# <a name="idiasymbolgetbuiltinkind"></a>IDiaSymbol::get_builtInKind
Récupère un type intégré du type HLSL.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_buildInKind(   
   DWORD* pRetVal);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Un pointeur vers un `DWORD` qui contient des types de type HLSL intégré.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)