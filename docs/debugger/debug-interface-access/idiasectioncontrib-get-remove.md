---
title: IDiaSectionContrib::get_remove | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_remove method
ms.assetid: fd30ab7b-022b-4402-a42a-2d38e274c1b1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4d44143994a0516c08e4738749b65bca54ba7a66
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49854063"
---
# <a name="idiasectioncontribgetremove"></a>IDiaSectionContrib::get_remove
Récupère un indicateur qui indique si la section est supprimée avant qu’il est fait partie de l’image en mémoire.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_remove (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne `TRUE` si la section n’est ne pas à ajouter à l’image en mémoire ; sinon, retourne `FALSE`.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas pris en charge. Sinon, retourne un code d'erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)