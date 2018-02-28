---
title: IDiaSession::findChildren | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findChildren method
ms.assetid: 5d19046f-f668-4aa9-8788-95cda9a98997
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 0cae2dd492fd11ff4a5d707ba95c571711358358
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idiasessionfindchildren"></a>IDiaSession::findChildren
Récupère tous les enfants d’un identificateur parent spécifié qui correspond au type de nom et le symbole.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT findChildren (   
   IDiaSymbol*       parent,  
   SymTagEnum        symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `parent`  
 [in] Un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objet qui représente le parent. Si ce symbole parent est une fonction, un module ou un bloc, ses enfants lexicales sont retournées dans `ppResult`. Si le symbole parent est un type, ses enfants de la classe sont retournées. Si ce paramètre est `NULL`, puis `symtag` doit avoir la valeur `SymTagExe` ou `SymTagNull`, qui retourne la portée globale (fichier .exe).  
  
 `symtag`  
 [in] Spécifie la balise symbol des enfants doit être récupéré. Les valeurs sont tirées de la [symtagenum, énumération](../../debugger/debug-interface-access/symtagenum.md) énumération. La valeur `SymTagNull` pour récupérer tous les enfants.  
  
 `name`  
 [in] Spécifie le nom de l’enfant doit être récupéré. La valeur `NULL` pour tous les enfants doivent être récupérés.  
  
 `compareFlags`  
 [in] Spécifie les options de comparaison appliquées à la correspondance de noms. Les valeurs à partir de la [namesearchoptions, énumération](../../debugger/debug-interface-access/namesearchoptions.md) énumération peut être utilisée seul ou combiné.  
  
 `ppResult`  
 [out] Retourne un [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) de récupérer l’objet qui contient la liste des symboles enfants.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment rechercher des variables locales de la fonction `pFunc` ce nom de la correspondance `szVarName`.  
  
```C++  
IDiaEnumSymbols* pEnum;  
pSession->findChildren( pFunc, SymTagData, szVarName, nsCaseSensitive, &pEnum );  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [NameSearchOptions (énumération)](../../debugger/debug-interface-access/namesearchoptions.md)   
 [SymTagEnum (énumération)](../../debugger/debug-interface-access/symtagenum.md)