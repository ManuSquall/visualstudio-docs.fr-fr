---
title: IDiaSession::findFileById | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: aafdd2270606ba6e56713e9166dbae2b8c635b41
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742274"
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

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 L’identificateur du fichier source est une valeur unique utilisée en interne par le kit de développement logiciel (SDK) DIA pour rendre tous les fichiers sources uniques. Cette méthode est généralement utilisée en interne dans le kit de développement logiciel (SDK) DIA.

## <a name="see-also"></a>Voir aussi
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)