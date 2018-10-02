---
title: IDiaLineNumber::get_statement | Microsoft Docs
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
- IDiaLineNumber::get_statement method
ms.assetid: 22b8ee29-79ef-427f-bd05-00d255ab836b
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e1329cfe00bd6af4e93bc4b45c4328232b9c22df
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47507442"
---
# <a name="idialinenumbergetstatement"></a>IDiaLineNumber::get_statement
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDiaLineNumber::get_statement](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idialinenumber-get-statement).  
  
Récupère un indicateur qui spécifie que les informations de ligne décrivent le début d’une instruction, plutôt que d’une expression, dans la source du programme.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_statement (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne `TRUE` si ces informations de ligne décrivent le début d’une instruction dans la source du programme.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas pris en charge. Sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 Instructions peuvent s’étendre sur plusieurs lignes. Cette méthode indique si le numéro de ligne associé marque le début d’une telle instruction multiligne.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)



