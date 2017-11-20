---
title: IDiaSession::findInjectedSource | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSession::findInjectedSource method
ms.assetid: 907531b6-1ef8-4153-986d-b72611a1632d
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2dbac48aef894272d1edd9c4881c9f916255459b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idiasessionfindinjectedsource"></a>IDiaSession::findInjectedSource
Récupère une liste de sources qui a été placée dans le magasin de symboles par les fournisseurs d’attribut ou d’autres composants du processus de compilation.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT findInjectedSource (   
   LPCOLESTR                 srcFile,  
   IDiaEnumInjectedSources** ppResult  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 srcFile  
 [in] Nom du fichier source à rechercher.  
  
 ppResult  
 [out] Retourne un [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) objet qui contient une liste de toutes les sources injectées.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)