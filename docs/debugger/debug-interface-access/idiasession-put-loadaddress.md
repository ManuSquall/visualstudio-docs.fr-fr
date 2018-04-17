---
title: IDiaSession::put_loadAddress | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::put_loadAddress method
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fa8f7c12e07f68d8c3fdd85f0d33d964847abf22
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="idiasessionputloadaddress"></a>IDiaSession::put_loadAddress
Définit l’adresse de chargement du fichier exécutable qui correspond aux symboles dans ce magasin de symboles.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT put_loadAddress (   
   ULONGLONG NewVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `NewVal`  
 [in] Charge l’adresse pour le fichier exécutable.  
  
## <a name="remarks"></a>Notes  
 Propriétés d’adresse virtuelle (VA) de symbole sont calculées à l’aide de la valeur de cette méthode. Adresses virtuelles ne sont pas calculés, sauf si cette propriété est définie zéro.  
  
> [!NOTE]
>  Vous devez appeler cette méthode lorsque vous obtenez le [IDiaSession](../../debugger/debug-interface-access/idiasession.md) de l’objet et avant de commencer à l’aide de l’objet si vous avez besoin d’utiliser toutes les propriétés virtuelles sur les symboles.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)