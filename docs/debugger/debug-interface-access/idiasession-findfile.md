---
title: IDiaSession::findFile | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSession::findFile method
ms.assetid: a215dc21-b316-40d7-9923-55bfa014976b
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ef230d1b82992f769011e0cb1d9d4ff11145b82d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idiasessionfindfile"></a>IDiaSession::findFile
Extrait les fichiers de code source par compiland et le nom.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT findFile (   
   IDiaSymbol*           pCompiland,  
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumSourceFiles** ppResult  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pCompiland`  
 [in] Un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objet représentant le compiland à utiliser comme contexte pour la recherche. Définissez ce paramètre sur `NULL` pour rechercher les fichiers sources dans tous les modules (compilands).  
  
 `name`  
 [in] Spécifie le nom du fichier source doit être récupéré. Définissez ce paramètre sur `NULL` pour tous les fichiers source à récupérer.  
  
 `option`  
 [in] Spécifie les options de comparaison appliquées à la recherche de nom. Les valeurs à partir de la [namesearchoptions, énumération](../../debugger/debug-interface-access/namesearchoptions.md) énumération peut être utilisée seul ou combiné.  
  
 `ppResult`  
 [out] Retourne un [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md) de récupérer l’objet qui contient une liste des fichiers sources.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="example"></a>Exemple  
  
```C++  
IDiaEnumSourceFiles* pEnum;  
pSession->findFile( NULL, L"sourcefile.cpp", nsFNameExt, &pEnum );  
```  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [NameSearchOptions (énumération)](../../debugger/debug-interface-access/namesearchoptions.md)