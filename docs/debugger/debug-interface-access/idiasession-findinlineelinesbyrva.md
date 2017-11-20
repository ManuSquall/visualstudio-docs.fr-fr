---
title: IDiaSession::findInlineeLinesByRVA | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 7a74d5ee-0dbf-47c0-92b4-47ec03b13ce9
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5210616573d2d1e0248c189095c8f10e192eab80
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idiasessionfindinlineelinesbyrva"></a>IDiaSession::findInlineeLinesByRVA
Récupère une énumération qui permet à un client parcourir les informations de numéro de ligne de toutes les fonctions qui sont incorporées, directement ou indirectement, par le symbole parent spécifié et est contenue dans l’adresse virtuelle relative (RVA) spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT findInlineeLinesByRVA (   
   IDiaSymbol*           parent,  
   DWORD                 rva,  
   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `parent`  
 [in] Un `IDiaSymbol` objet qui représente le parent.  
  
 `rva`  
 [in] Spécifie l’adresse en tant qu’une adresse RVA.  
  
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