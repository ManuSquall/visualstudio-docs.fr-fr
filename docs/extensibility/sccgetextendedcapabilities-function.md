---
title: SccGetExtendedCapabilities fonction) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80700720"
---
# <a name="sccgetextendedcapabilities-function"></a>SccGetExtendedCapabilities fonction)
Cette fonction retourne des fonctionnalités supplémentaires prises en charge par le plug-in de contrôle de code source.

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

dans Pointeur de contexte du plug-in de contrôle de code source.

 lSccExCaps

dans Indicateur spécifiant une fonctionnalité étendue pour laquelle effectuer un test (consultez la table des codes de capacité étendus dans les [indicateurs de capacité](../extensibility/capability-flags.md) pour les indicateurs possibles).

 pbSupported

à Retourne une valeur différente de zéro ( `TRUE` ) si la fonction spécifiée est prise en charge ; sinon, retourne zéro ( `FALSE` ).

## <a name="return-value"></a>Valeur retournée
 L’implémentation du plug-in de contrôle de code source de cette fonction est supposée retourner l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|L’opération d’extraction de la capacité s’est terminée avec succès.|
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|Une erreur inconnue ou non spécifiée s’est produite.|

## <a name="remarks"></a>Notes
 Cette méthode est appelée à la demande ; autrement dit, lorsqu’une fonctionnalité doit être testée, cette méthode est appelée pour déterminer si cette fonctionnalité est prise en charge. Un seul indicateur à la fois est spécifié.

## <a name="see-also"></a>Voir aussi
- [Fonctions de l’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
- [Codes d’erreur](../extensibility/error-codes.md)
- [Indicateurs de capacité](../extensibility/capability-flags.md)
