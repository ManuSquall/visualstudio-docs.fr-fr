---
title: IDiaSymbol::get_language | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_language method
ms.assetid: c759ad3c-1c21-4234-869b-86aa3a608a38
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cd9adeba1b3ac84fa6a09d6c6f25b77e35cd429f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839949"
---
# <a name="idiasymbolget_language"></a>IDiaSymbol::get_language
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère la langue de la source.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_language (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 à Retourne une valeur de l’énumération d' [énumération CV_CFL_LANG](../../debugger/debug-interface-access/cv-cfl-lang.md) qui spécifie le langage de la source.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` ou code d’erreur.  
  
> [!NOTE]
> Une valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [CV_CFL_LANG, énumération](../../debugger/debug-interface-access/cv-cfl-lang.md)
