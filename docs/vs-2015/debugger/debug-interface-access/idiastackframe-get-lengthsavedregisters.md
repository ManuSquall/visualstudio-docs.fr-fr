---
title: IDiaStackFrame::get_lengthSavedRegisters | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
- IDiaStackFrame::get_lengthSavedRegisters method
ms.assetid: b75fad6e-1ef4-44e6-89e3-c31c6fba10b3
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 931ecb5224f3a404d1be31c313b78dd1bb4c15d7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47506474"
---
# <a name="idiastackframegetlengthsavedregisters"></a>IDiaStackFrame::get_lengthSavedRegisters
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDiaStackFrame::get_lengthSavedRegisters](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiastackframe-get-lengthsavedregisters).  
  
Récupère le nombre d’octets de l’objet d’un push sur la pile de registres enregistrés.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_lengthSavedRegisters (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne le nombre d’octets de registres enregistrés.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si la propriété n’est pas pris en charge. Sinon, retourne un code d'erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)



