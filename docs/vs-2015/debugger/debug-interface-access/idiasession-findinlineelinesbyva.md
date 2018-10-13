---
title: IDiaSession::findInlineeLinesByVA | Microsoft Docs
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
ms.assetid: dffe6594-e0d1-4ed5-aeea-8773f88d82a6
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 697a2000ced432fb477091238bc0d76029e7b0b5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49218749"
---
# <a name="idiasessionfindinlineelinesbyva"></a>IDiaSession::findInlineLinesByVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère une énumération qui permet au client d’effectuer une itération dans les informations de numéro de ligne de toutes les fonctions qui sont inline, directement ou indirectement, par le symbole parent spécifié et est contenue dans l’adresse virtuelle spécifiée (VA).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT findInlineeLinesByVA (   
   IDiaSymbol*           parent,   ULONGLONG             va,   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `parent`  
 [in] Un `IDiaSymbol` objet représentant le parent.  
  
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



