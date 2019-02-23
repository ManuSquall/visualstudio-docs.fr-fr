---
title: Fonction SccGetExtendedCapabilities | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetExtendedCapabilities
helpviewer_keywords:
- SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9ed27c996a94c4e81a946efbfa2684dc4169005a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56720469"
---
# <a name="sccgetextendedcapabilities-function"></a>Fonction SccGetExtendedCapabilities
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

[in] Le pointeur de contexte de plug-in de contrôle de code source.

 lSccExCaps

[in] Un indicateur qui spécifie une fonctionnalité étendue pour laquelle effectuer un test (voir le tableau de Code de fonctionnalité étendue dans [indicateurs de capacité](../extensibility/capability-flags.md) pour les indicateurs possibles).

 pbSupported

[out] Retourne zéro (`TRUE`) si la fonctionnalité spécifiée est prise en charge ; sinon, retourne la valeur zéro (`FALSE`).

## <a name="return-value"></a>Valeur de retour
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :

|Value|Description|
|-----------|-----------------|
|SCC_OK|Opération de fonctionnalité de récupération s’est terminée correctement.|
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|Erreur inconnue ou non spécifiée s’est produite.|

## <a name="remarks"></a>Notes
 Cette méthode est appelée à la demande ; Autrement dit, quand une fonctionnalité doit être testée, cette méthode est appelée pour déterminer si la prise en charge de fonctionnalité. Seul l’indicateur à la fois est spécifié.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API source contrôle plug-in](../extensibility/source-control-plug-in-api-functions.md)
- [Codes d’erreur](../extensibility/error-codes.md)
- [Indicateurs de capacité](../extensibility/capability-flags.md)