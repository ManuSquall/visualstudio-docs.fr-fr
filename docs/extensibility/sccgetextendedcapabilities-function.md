---
title: Fonction SccGetExtendedCapabilitiess (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetExtendedCapabilities
helpviewer_keywords:
- SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5247f2de7ffc63db7235f915c72b3274b8fee5f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700720"
---
# <a name="sccgetextendedcapabilities-function"></a>Fonction SccGetExtendedCapabilities
Cette fonction renvoie des capacités supplémentaires prises en charge par le plug-in de contrôle source.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccGetExtendedCapabilities(
   LPVOID pContext,
   LONG lSccExCaps,
   LPBOOL pbSupported
);
```

### <a name="parameters"></a>Paramètres
 pContext

[dans] Le pointeur de contexte de plug-in de contrôle de source.

 lSccExCaps

[dans] Un drapeau précisant une capacité étendue pour laquelle le test (voir la table du Code de capacité étendue dans [les drapeaux de capacité](../extensibility/capability-flags.md) pour les drapeaux possibles).

 pbSupported

[out] Retourne non zéro`TRUE`( ) si la capacité spécifiée est prise en charge; autrement, retourne`FALSE`zéro ( ).

## <a name="return-value"></a>Valeur retournée
 La mise en œuvre plug-in de cette fonction de contrôle source devrait renvoyer l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|L’opération de capacité de se terminer avec succès.|
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|Une erreur inconnue ou non spécifiée s’est produite.|

## <a name="remarks"></a>Notes
 Cette méthode est appelée à la demande; c’est-à-dire qu’une capacité doit être testée, cette méthode est appelée pour déterminer si cette capacité est prise en charge. Un seul drapeau à la fois est spécifié.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API plug-in de contrôle des sources](../extensibility/source-control-plug-in-api-functions.md)
- [Codes d’erreur](../extensibility/error-codes.md)
- [Drapeaux de capacité](../extensibility/capability-flags.md)
