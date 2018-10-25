---
title: IDiaSession::findInlineFramesByRVA | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: ddb3ff0e-cb3d-4fa0-af56-f064b218b264
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0ebb32b9b22de8d4092c53f56accf1d953bbc94a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49876878"
---
# <a name="idiasessionfindinlineframesbyrva"></a>IDiaSession::findInlineFramesByRVA
Récupère une énumération qui permet au client d’effectuer une itération dans tous les cadres inline sur une adresse virtuelle relative (RVA) spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT findInlineFramesByRVA (   
   IDiaSymbol*       parent,   DWORD             rva,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `parent`  
 [in] Un `IDiaSymbol` objet représentant le parent.  
  
 `rva`  
 [in] Spécifie l’adresse comme une RVA.  
  
 `ppResult`  
 [out] Contient un `IDiaEnumSymbols` objet qui contient la liste d’images qui sont récupérés.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum (énumération)](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)