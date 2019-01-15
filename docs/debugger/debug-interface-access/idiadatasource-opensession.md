---
title: IDiaDataSource::openSession | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::openSession method
ms.assetid: a3319ed0-3979-483b-9852-c0af96852c48
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bea16f7ff0f723979ded9962a8ff9e620227f8ea
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53843110"
---
# <a name="idiadatasourceopensession"></a>IDiaDataSource::openSession
Ouvre une session pour l’interrogation des symboles.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT openSession (   
   IDiaSession** ppSession  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 ppSession  
 [out] Retourne un [IDiaSession](../../debugger/debug-interface-access/idiasession.md) objet représentant la session ouverte.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur. Le tableau suivant montre les valeurs de retournés possibles pour cette méthode.  
  
|Value|Description|  
|-----------|-----------------|  
|E_UNEXPECTED|Le [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) objet n’a pas déjà été initialisé avec une source de symboles.|  
|E_INVALIDARG|Paramètre `ppSession` non valide.|  
|E_OUTOFMEMORY|Mémoire insuffisante pour ouvrir la session.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode ouvre un [IDiaSession](../../debugger/debug-interface-access/idiasession.md) objet pour une source de données.  
  
 `IDiaSession` objets implémentent des requêtes dans la source de données. Une session gère un espace d’adressage pour chaque ensemble de symboles de débogage. Si le fichier .exe ou .dll décrit par les symboles de source de données est actif dans la zone Adresse plusieurs plages d’adresses (par exemple, étant donné que plusieurs processus ont charger), puis une session pour chaque plage d’adresses doit être utilisée.  
  
## <a name="example"></a>Exemple  
  
```C++  
IDiaSession* pSession;  
HRESULT hr = pSource->openSession( &pSession );  
if (FAILED(hr))  
{  
   // report error  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [Vue d’ensemble](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [Interrogation du fichier .Pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)