---
title: IDiaSession::put_loadAddress | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::put_loadAddress method
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f697384874726904960fc5ba04733c3acfe1cd06
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839265"
---
# <a name="idiasessionput_loadaddress"></a>IDiaSession::put_loadAddress
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Définit l’adresse de chargement du fichier exécutable qui correspond aux symboles dans ce magasin de symboles.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT put_loadAddress (   
   ULONGLONG NewVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `NewVal`  
 dans Adresse de chargement du fichier exécutable.  
  
## <a name="remarks"></a>Remarques  
 Les propriétés d’adresse virtuelle de symbole (VA) sont calculées à l’aide de la valeur de cette méthode. Les adresses virtuelles ne sont pas calculées, sauf si cette propriété est définie sur une valeur différente de zéro.  
  
> [!NOTE]
> Vous devez appeler cette méthode lorsque vous récupérez l’objet [IDiaSession](../../debugger/debug-interface-access/idiasession.md) et avant de commencer à utiliser l’objet si vous devez utiliser des propriétés virtuelles sur les symboles.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
