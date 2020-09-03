---
title: IDiaDataSource::openSession | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::openSession method
ms.assetid: a3319ed0-3979-483b-9852-c0af96852c48
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4bec5507d15374e6e88afd4567d4b0fec9ca6cb7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198602"
---
# <a name="idiadatasourceopensession"></a>IDiaDataSource::openSession
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ouvre une session pour interroger les symboles.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT openSession (   
   IDiaSession** ppSession  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 ppSession  
 à Retourne un objet [IDiaSession](../../debugger/debug-interface-access/idiasession.md) représentant la session ouverte.  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur. Le tableau suivant indique les valeurs de retour possibles pour cette méthode.  
  
|Valeur|Description|  
|-----------|-----------------|  
|E_UNEXPECTED|L’objet [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) n’a pas encore été initialisé avec une source de symboles.|  
|E_INVALIDARG|Paramètre `ppSession` non valide.|  
|E_OUTOFMEMORY|Mémoire insuffisante pour ouvrir la session.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode ouvre un objet [IDiaSession](../../debugger/debug-interface-access/idiasession.md) pour une source de données.  
  
 `IDiaSession` les objets implémentent des requêtes dans la source de données. Une session gère un espace d’adressage pour chaque ensemble de symboles de débogage. Si le fichier. exe ou. dll décrit par les symboles de la source de données est actif dans plusieurs plages d’adresses (par exemple, parce que plusieurs processus ont été chargés), une session pour chaque plage d’adresses doit être utilisée.  
  
## <a name="example"></a> Exemple  
  
```cpp#  
IDiaSession* pSession;  
HRESULT hr = pSource->openSession( &pSession );  
if (FAILED(hr))  
{  
   // report error  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [Vue](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [Interrogation du fichier .Pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)
