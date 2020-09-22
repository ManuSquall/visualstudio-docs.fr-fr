---
title: IDiaSymbol::get_volatileType | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_volatileType method
ms.assetid: 19782a4d-40a8-467b-ab7d-58bc4d812309
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d36d688c29894bd65eae29e033ef1d94869e04fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840042"
---
# <a name="idiasymbolget_volatiletype"></a>IDiaSymbol::get_volatileType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère un indicateur qui spécifie si le type de données défini par l’utilisateur (UDT) est volatile.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_volatileType (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 à Retourne `TRUE` si le type défini par l’utilisateur est volatile ; sinon, retourne `FALSE` .  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
> [!NOTE]
> Une valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="remarks"></a>Remarques  
 En C++, un UDT peut être marqué avec le `volatile` mot clé, ce qui indique que son contenu ne peut pas être supposé exister d’un accès à l’autre.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
