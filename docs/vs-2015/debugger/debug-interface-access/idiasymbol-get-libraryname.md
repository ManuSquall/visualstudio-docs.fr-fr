---
title: IDiaSymbol::get_libraryName | Microsoft Docs
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
- IDiaSymbol::get_libraryName method
ms.assetid: d04ddd9a-812d-46e4-bd39-28bdf3edfb70
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 23491ca9cc73a388ef4b665c7553ecee24a20647
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47508811"
---
# <a name="idiasymbolgetlibraryname"></a>IDiaSymbol::get_libraryName
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDiaSymbol::get_libraryName](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-libraryname).  
  
Récupère le nom de fichier du fichier de bibliothèque ou un objet à partir duquel l’objet a été chargé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_libraryName (   
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne le nom de fichier du fichier de bibliothèque ou un objet à partir duquel l’objet a été chargé.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



