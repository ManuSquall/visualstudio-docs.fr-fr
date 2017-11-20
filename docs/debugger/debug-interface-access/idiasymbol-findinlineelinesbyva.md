---
title: IDiaSymbol::findInlineeLinesByVA | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 61427d33-30d2-4ac9-9bd6-c58c6c705072
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 442dd8fce97c30cfce792f825d8212e6558bf4cb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolfindinlineelinesbyva"></a>IDiaSymbol::findInlineeLinesByVA
Récupère une énumération qui permet à un client parcourir les informations de numéro de ligne de toutes les fonctions qui sont incorporées, directement ou indirectement, de ce symbole dans l’adresse virtuelle spécifiée (VA).  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT findInlineeLinesByVA (   
   ULONGLONG             va,  
   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `va`  
 [in] Spécifie l’adresse utiliser que  
  
 `length`  
 [in] Spécifie la plage d’adresses, en octets, pour couvrir cette requête.  
  
 `ppResult`  
 [out] Contient un `IDiaEnumLineNumbers` objet qui contient la liste des numéros de ligne qui sont récupérés.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum (énumération)](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)