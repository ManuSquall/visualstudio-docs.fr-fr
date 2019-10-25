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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7dd6ab61db3e3bafd594298aa41d32bce64d4941
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744916"
---
# <a name="idiadatasourceopensession"></a>IDiaDataSource::openSession
Ouvre une session pour interroger les symboles.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT openSession ( 
   IDiaSession** ppSession
);
```

#### <a name="parameters"></a>Paramètres
ppSession

à Retourne un objet [IDiaSession](../../debugger/debug-interface-access/idiasession.md) représentant la session ouverte.

## <a name="return-value"></a>Valeur de retour
En cas de réussite, retourne `S_OK` ; Sinon, retourne un code d’erreur. Le tableau suivant indique les valeurs de retour possibles pour cette méthode.

|valeur|Description|
|-----------|-----------------|
|E_UNEXPECTED|L’objet [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) n’a pas encore été initialisé avec une source de symboles.|
|E_INVALIDARG|Paramètre `ppSession` non valide.|
|E_OUTOFMEMORY|Mémoire insuffisante pour ouvrir la session.|

## <a name="remarks"></a>Notes
Cette méthode ouvre un objet [IDiaSession](../../debugger/debug-interface-access/idiasession.md) pour une source de données.

les objets `IDiaSession` implémentent des requêtes dans la source de données. Une session gère un espace d’adressage pour chaque ensemble de symboles de débogage. Si le fichier. exe ou. dll décrit par les symboles de la source de données est actif dans plusieurs plages d’adresses (par exemple, parce que plusieurs processus ont été chargés), une session pour chaque plage d’adresses doit être utilisée.

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
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [Vue d’ensemble](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [Interrogation du fichier .Pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)
