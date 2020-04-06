---
title: OPTNAMECHANGEPFN - France Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702248"
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
Il s’agit d’une fonction de rappel spécifiée dans `SCC_OPT_NAMECHANGEPFN`un appel à la [SccSetOption](../extensibility/sccsetoption-function.md) (en utilisant l’option ) et est utilisé pour communiquer les modifications de nom apportées par le plug-in de contrôle source vers l’IDE.

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

[dans] Valeur de l’utilisateur spécifiée dans un appel `SCC_OPT_USERDATA`précédent à la [SccSetOption](../extensibility/sccsetoption-function.md) (en utilisant l’option ).

 pszOldName (en)

[dans] Le nom original du fichier.

 pszNewName

[dans] Le nom du fichier a été rebaptisé.

## <a name="return-value"></a>Valeur retournée
 Aucun.

## <a name="remarks"></a>Notes
 Si un fichier est renommé lors d’une opération de contrôle source, le plug-in de contrôle source peut informer l’IDE sur le changement de nom par le biais de ce rappel.

 Si l’IDE ne prend pas en charge ce rappel, il n’appellera pas la [SccSetOption](../extensibility/sccsetoption-function.md) pour le spécifier. Si le plug-in ne prend pas en `SCC_E_OPNOTSUPPORTED` charge `SccSetOption` ce rappel, il reviendra de la fonction lorsque l’IDE tente de régler le rappel.

## <a name="see-also"></a>Voir aussi
- [Fonctions de rappel mises en œuvre par l’IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)
