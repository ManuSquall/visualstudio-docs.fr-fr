---
title: IDiaSession::findFile | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findFile method
ms.assetid: a215dc21-b316-40d7-9923-55bfa014976b
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1e791bc09ba3dd4f1811c650926eadb0f7f0462a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62431639"
---
# <a name="idiasessionfindfile"></a>IDiaSession::findFile
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère les fichiers sources par compiland et le nom.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT findFile (   
   IDiaSymbol*           pCompiland,  
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumSourceFiles** ppResult  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pCompiland`  
 [in] Un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objet représentant le compiland à être utilisé comme un contexte pour la recherche. Définissez ce paramètre sur `NULL` pour rechercher les fichiers sources dans tous les compilands.  
  
 `name`  
 [in] Spécifie le nom du fichier source à récupérer. Définissez ce paramètre sur `NULL` pour tous les fichiers doivent être extraites de sources.  
  
 `option`  
 [in] Spécifie les options de comparaison appliquées à la recherche de nom. Les valeurs de la [NameSearchOptions (énumération)](../../debugger/debug-interface-access/namesearchoptions.md) énumération peut être utilisée seul ou combiné.  
  
 `ppResult`  
 [out] Retourne un [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md) de récupérer l’objet qui contient une liste des fichiers sources.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="example"></a>Exemple  
  
```cpp#  
IDiaEnumSourceFiles* pEnum;  
pSession->findFile( NULL, L"sourcefile.cpp", nsFNameExt, &pEnum );  
```  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [NameSearchOptions, énumération](../../debugger/debug-interface-access/namesearchoptions.md)
