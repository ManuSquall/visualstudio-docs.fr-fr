---
title: IDiaStackWalkHelper::symbolForVA | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper::symbolForVA method
ms.assetid: 8dd9455d-d44c-4dd6-a0aa-31131cbea2aa
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 953684a81b95bd29c6d932b4429a1ea7b079c0c3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49275754"
---
# <a name="idiastackwalkhelpersymbolforva"></a>IDiaStackWalkHelper::symbolForVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère le symbole qui contient l’adresse virtuelle spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT symbolForVA(   
   ULONGLONG     va,  
   IDiaSymbol**  ppSymbol  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `va`  
 [in] L’adresse virtuelle qui est contenue dans le symbole demandé. Le symbole doit être un `SymTagFunctionType` (une valeur comprise entre le [SymTagEnum (énumération)](../../debugger/debug-interface-access/symtagenum.md) énumération).  
  
 `ppSymbol`  
 [out] Un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objet qui représente le symbole à l’adresse spécifiée.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



