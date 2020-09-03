---
title: IDiaStackFrame::get_cplusplusExceptionHandling | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_cplusplusExceptionHandling method
ms.assetid: f2631820-c986-40ca-b61e-230d7a9c426c
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f400135fab95925384947488b5582b2f3d996928
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190590"
---
# <a name="idiastackframeget_cplusplusexceptionhandling"></a>IDiaStackFrame::get_cplusplusExceptionHandling
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère un indicateur qui signale si la gestion des exceptions C++ est en vigueur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_cplusplusExceptionHandling (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 à Retourne `TRUE` si la gestion des exceptions C++ est appliquée pour ce frame ; sinon, retourne `FALSE` .  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si la propriété n’est pas prise en charge. Sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 La gestion des exceptions C++ n’est pas identique à la gestion structurée ou à la gestion des exceptions système.  
  
 Pour déterminer si la gestion structurée des exceptions est en vigueur, appelez la méthode [IDiaStackFrame :: get_systemExceptionHandling](../../debugger/debug-interface-access/idiastackframe-get-systemexceptionhandling.md) .  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [IDiaStackFrame::get_systemExceptionHandling](../../debugger/debug-interface-access/idiastackframe-get-systemexceptionhandling.md)
