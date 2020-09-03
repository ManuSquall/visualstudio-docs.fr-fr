---
title: OPTNAMECHANGEPFN | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- OPTNAMECHANGEPFN
helpviewer_keywords:
- OPTNAMECHANGEPFN callback function
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 603bd08c1ec3832bf732e0b33101076738d009e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80702248"
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
