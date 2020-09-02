---
title: IDiaSession::findChildren | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findChildren method
ms.assetid: 5d19046f-f668-4aa9-8788-95cda9a98997
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cf274bb0f572da11a9aa43248da7eaa72a2e73c3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150427"
---
# <a name="idiasessionfindchildren"></a>IDiaSession::findChildren
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère tous les enfants d’un identificateur parent spécifié qui correspondent au nom et au type de symbole.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 dans Objet [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) qui représente le parent. Si ce symbole parent est une fonction, un module ou un bloc, ses enfants lexicaux sont retournés dans `ppResult` . Si le symbole parent est un type, ses enfants de classe sont retournés. Si ce paramètre a `NULL` `symtag` la valeur, doit avoir `SymTagExe` la valeur ou `SymTagNull` , qui retourne l’étendue globale (fichier. exe).  
  
 `symtag`  
 dans Spécifie la balise de symbole des enfants à récupérer. Les valeurs sont extraites de l’énumération d' [énumération SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) . Affectez la valeur `SymTagNull` pour récupérer tous les enfants.  
  
 `name`  
 dans Spécifie le nom des enfants à récupérer. Affectez à la valeur `NULL` pour tous les enfants à récupérer.  
  
 `compareFlags`  
 dans Spécifie les options de comparaison appliquées à la correspondance de noms. Les valeurs de l’énumération d' [énumération NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md) peuvent être utilisées seules ou en combinaison.  
  
 `ppResult`  
 à Retourne un objet [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) qui contient la liste des symboles enfants récupérés.  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment rechercher les variables locales de la fonction `pFunc` qui correspondent au nom `szVarName` .  
  
```cpp#  
IDiaEnumSymbols* pEnum;  
pSession->findChildren( pFunc, SymTagData, szVarName, nsCaseSensitive, &pEnum );  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Vue](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Énumération NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)   
 [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md)
