---
title: IDiaStackWalkHelper::imageForVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper::imageForVA method
ms.assetid: 8d4edabf-3c01-4fef-8b61-4779f3371067
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a65c93bbac1cd49c52f6e93e2f009aba22581bb4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53854631"
---
# <a name="idiastackwalkhelperimageforva"></a>IDiaStackWalkHelper::imageForVA
Retourne le début de l’image d’un exécutable dans la mémoire affectée d’une adresse virtuelle quelque part dans l’espace de mémoire de l’exécutable.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT imageForVA(  
   ULONGLONG  vaContext,  
   ULONGLONG *pvaImageStart  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `vaContext`  
 [in] L’adresse virtuelle se trouve quelque part dans l’espace de l’exécutable.  
  
 `pvaImageStart`  
 [out] Retourne l’adresse virtuelle à partir de l’image de l’exécutable.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)