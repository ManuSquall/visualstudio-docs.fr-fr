---
title: IDiaEnumSectionContribs::Item | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Item method
ms.assetid: 63a28f23-0ca0-44a7-b11b-ca0206d642a0
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 06a82fbb52ccdf0f9fb9fda50a74f2cfb30e7648
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58952035"
---
# <a name="idiaenumsectioncontribsitem"></a>IDiaEnumSectionContribs::Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère les contributions de la section au moyen d’un index.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT Item (   
   DWORD                index,  
   IDiaSectionContrib** section  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 index  
 [in] Index de la [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) objet à récupérer. L’index est comprise entre 0 et `count`-1, où `count` est retourné par la [IDiaEnumSectionContribs::get_Count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md) (méthode).  
  
 section  
 [out] Retourne un [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) objet représentant la contribution de la section souhaitée.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaEnumSectionContribs::get_Count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md)   
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)
