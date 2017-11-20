---
title: IDiaSession::put_loadAddress | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSession::put_loadAddress method
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3b12ef6fa6da9338346aa997ba16cb023548f138
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
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
  
## <a name="remarks"></a>Remarques  
 Propriétés d’adresse virtuelle (VA) de symbole sont calculées à l’aide de la valeur de cette méthode. Adresses virtuelles ne sont pas calculés, sauf si cette propriété est définie zéro.  
  
> [!NOTE]
>  Vous devez appeler cette méthode lorsque vous obtenez le [IDiaSession](../../debugger/debug-interface-access/idiasession.md) de l’objet et avant de commencer à l’aide de l’objet si vous avez besoin d’utiliser toutes les propriétés virtuelles sur les symboles.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)