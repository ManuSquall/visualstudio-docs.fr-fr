---
title: IDiaSession::findFileById | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findFileById method
ms.assetid: 710efe04-78b5-4f3e-a1d8-f9b069063503
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1893a361ab4043ad5969a7fa899c07fe18253b9a
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85465831"
---
# <a name="idiasessionfindfilebyid"></a>IDiaSession::findFileById
Récupère un fichier source par identificateur de fichier source.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT findFileById ( 
   DWORD            uniqueId,
   IDiaSourceFile** ppResult
);
```

#### <a name="parameters"></a>Paramètres
 `uniqueId`

dans Spécifie l’identificateur du fichier source.

 `ppResult`

à Retourne un objet [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) qui représente le fichier source récupéré.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Remarques
 L’identificateur du fichier source est une valeur unique utilisée en interne par le kit de développement logiciel (SDK) DIA pour rendre tous les fichiers sources uniques. Cette méthode est généralement utilisée en interne dans le kit de développement logiciel (SDK) DIA.

## <a name="see-also"></a>Voir aussi
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)