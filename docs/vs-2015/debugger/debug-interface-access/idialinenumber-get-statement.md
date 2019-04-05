---
title: IDiaLineNumber::get_statement | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_statement method
ms.assetid: 22b8ee29-79ef-427f-bd05-00d255ab836b
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b5ad480a3b5d3ed892fc56fec2c882638f986810
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58939215"
---
# <a name="idialinenumbergetstatement"></a>IDiaLineNumber::get_statement
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
