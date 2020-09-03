---
title: IDiaDataSource::get_lastError | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::get_lastError method
ms.assetid: cf08850b-8b75-4e8c-90bd-bd0214756f99
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 231c6b082f7a641ee78d10003d544c3fb9644c1c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85468524"
---
# <a name="idiadatasourceget_lasterror"></a>IDiaDataSource::get_lastError
Récupère le nom de fichier de la dernière erreur de chargement.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_lastError (
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 pRetVal

à Retourne une chaîne qui contient le nom de fichier. pdb associé à la dernière erreur de chargement.

## <a name="return-value"></a>Valeur renvoyée
 Retourne le dernier code d’erreur provoqué par une opération de chargement. Retourne `E_INVALIDARG` si le `pRetVal` paramètre a la valeur `NULL` .

## <a name="example"></a>Exemple

```C++
BSTR    fileName;
HRESULT errorCode = pSource->get_lastError( &fileName );
```

## <a name="see-also"></a>Voir aussi
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)