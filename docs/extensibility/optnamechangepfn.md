---
title: OPTNAMECHANGEPFN | Microsoft Docs
description: En savoir plus sur la fonction de rappel OPTNAMECHANGEPFN, qui communique les modifications de nom du plug-in de contrôle de code source à l’IDE de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- OPTNAMECHANGEPFN
helpviewer_keywords:
- OPTNAMECHANGEPFN callback function
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e583c7e19fb6123da06d0ee525abe9c573d8d788
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922885"
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
Il s’agit d’une fonction de rappel spécifiée dans un appel à [SccSetOption](../extensibility/sccsetoption-function.md) (option using `SCC_OPT_NAMECHANGEPFN` ) et est utilisée pour communiquer les modifications de nom apportées par le plug-in de contrôle de code source à l’IDE.

## <a name="signature"></a>Signature

```cpp
typedef void (*OPTNAMECHANGEPFN)(
   LPVOID pvCallerData,
   LPCSTR pszOldName,
   LPCSTR pszNewName
);
```

## <a name="parameters"></a>Paramètres
 pvCallerData

dans Valeur utilisateur spécifiée dans un appel précédent à [SccSetOption](../extensibility/sccsetoption-function.md) (option using `SCC_OPT_USERDATA` ).

 pszOldName

dans Nom d’origine du fichier.

 pszNewName

dans Nom du fichier dans lequel le fichier a été renommé.

## <a name="return-value"></a>Valeur retournée
 Aucun.

## <a name="remarks"></a>Notes
 Si un fichier est renommé pendant une opération de contrôle de code source, le plug-in de contrôle de code source peut notifier l’IDE du changement de nom par le biais de ce rappel.

 Si l’IDE ne prend pas en charge ce rappel, il n’appellera pas le [SccSetOption](../extensibility/sccsetoption-function.md) pour le spécifier. Si le plug-in ne prend pas en charge ce rappel, il retourne `SCC_E_OPNOTSUPPORTED` la `SccSetOption` fonction lorsque l’IDE tente de définir le rappel.

## <a name="see-also"></a>Voir aussi
- [Fonctions de rappel implémentées par l’IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)
