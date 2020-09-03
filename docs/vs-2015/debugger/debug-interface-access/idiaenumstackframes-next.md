---
title: IDiaEnumStackFrames::Next | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumStackFrames::Next method
ms.assetid: 09378a21-d5e3-4213-b7e2-10f04d85295f
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1c66e8b281f27e13a1176dd32f21856367e5f1ac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189741"
---
# <a name="idiaenumstackframesnext"></a>IDiaEnumStackFrames::Next
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère un nombre spécifié d’éléments de frame de pile à partir de la séquence d’énumération.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT Next(   
   ULONG             celt,  
   IDiaStackFrame**  rgelt,  
   ULONG*            pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 celt  
 dans Nombre d’éléments StackFrame dans l’énumérateur à récupérer.  
  
 rgelt  
 à Tableau à remplir avec les objets [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) demandés.  
  
 pceltFetched  
 à Retourne le nombre d’éléments de frame de pile dans l’énumérateur extrait.  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` s’il n’y a plus de frames de pile. Sinon, retourne un code d'erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)   
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
