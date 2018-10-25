---
title: IDiaSession::findLines | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
- IDiaSession::findLines method
ms.assetid: d6e84916-fd55-457e-b057-57f97b51fe73
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 087248b4d4f25847fa8896a6896c335e2751b906
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49910743"
---
# <a name="idiasessionfindlines"></a>IDiaSession::findLines
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère les numéros de ligne au sein de compiland spécifié et les identificateurs de fichier source.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT findLines (   
   IDiaSymbol*           compiland,  
   IDiaSourceFile*       file,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `compiland`  
 [in] Un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objet représentant le compiland. Utilisez cette interface en tant qu’un contexte dans lequel rechercher les numéros de ligne.  
  
 `file`  
 [in] Un [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) objet représentant le fichier source dans laquelle rechercher les numéros de ligne.  
  
 `ppResult`  
 [out] Retourne un [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) de récupérer l’objet qui contient une liste des numéros de ligne.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



