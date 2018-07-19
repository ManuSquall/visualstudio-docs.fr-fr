---
title: IDiaPropertyStorage::Enum | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::Enum
ms.assetid: 00e462da-980a-40b3-a2d6-75a25ee809e5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f0fe51224a4b4a5abc73a3edb7a2caf239d32efb
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31459088"
---
# <a name="idiapropertystorageenum"></a>IDiaPropertyStorage::Enum
Obtient un énumérateur pour les propriétés dans cet ensemble.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT Enum (   
   IEnumSTATPROPSTG** ppenum  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppenum`  
 [out] Retourne un `IEnumSTATPROPSTG` objet (dans l’espace de noms d’assemblys Microsoft.VisualStudio.OLE.Interop) qui représente une énumération des propriétés.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)