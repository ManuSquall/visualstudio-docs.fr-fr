---
description: Cette fonction récupère un événement d’État mis en file d’attente.
title: SccGetEvents fonction) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGetEvents
helpviewer_keywords:
- SccGetEvents function
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9438ac10301e2da43b26a88575e44a8ad2c0bf82
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901056"
---
# <a name="sccgetevents-function"></a>SccGetEvents fonction)
Cette fonction récupère un événement d’État mis en file d’attente.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccGetEvents (
   LPVOID pvContext,
   LPSTR  lpFileName,
   LPLONG lpStatus,
   LPLONG pnEventsRemaining
);
```

### <a name="parameters"></a>Paramètres
 pvContext

dans Structure de contexte du plug-in de contrôle de code source.

 lpFileName

[in, out] Mémoire tampon dans laquelle le plug-in de contrôle de code source place le nom de fichier retourné (jusqu’à _MAX_PATH caractères).

 lpStatus

[in, out] Retourne le code d’État (consultez le [code d’État du fichier](../extensibility/file-status-code-enumerator.md) pour connaître les valeurs possibles).

 pnEventsRemaining

[in, out] Retourne le nombre d’entrées restantes dans la file d’attente après cet appel. Si ce nombre est élevé, l’appelant peut décider d’appeler le [SccQueryInfo](../extensibility/sccqueryinfo-function.md) pour récupérer toutes les informations en même temps.

## <a name="return-value"></a>Valeur retournée
 L’implémentation du plug-in de contrôle de code source de cette fonction est supposée retourner l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|Événements d’extraction réussis.|
|SCC_E_OPNOTSUPPORTED|Cette fonction n'est pas prise en charge.|
|SCC_E_NONSPECIFICERROR|Échec non spécifique.|

## <a name="remarks"></a>Remarques
 Cette fonction est appelée pendant un traitement inactif pour voir si des mises à jour d’État ont été effectuées pour des fichiers sous contrôle de code source. Le plug-in de contrôle de code source conserve l’état de tous les fichiers qu’il connaît, et chaque fois qu’un changement d’État est signalé par le plug-in, l’État et le fichier associé sont stockés dans une file d’attente. Lorsque `SccGetEvents` est appelé, l’élément supérieur de la file d’attente est récupéré et retourné. Cette fonction est contournée pour retourner uniquement les informations précédemment mises en cache et doit avoir un délai très court (autrement dit, aucune lecture du disque ou demander l’État au système de contrôle de code source). Sinon, les performances de l’IDE peuvent commencer à se dégrader.

 S’il n’existe aucune mise à jour d’État pour le rapport, le plug-in de contrôle de code source stocke une chaîne vide dans la mémoire tampon vers laquelle pointe `lpFileName` . Dans le cas contraire, le plug-in stocke le nom de chemin d’accès complet du fichier pour lequel les informations d’État ont été modifiées et retourne le code d’état approprié (l’une des valeurs détaillées dans le [code d’État du fichier](../extensibility/file-status-code-enumerator.md)).

## <a name="see-also"></a>Voir aussi
- [Fonctions de l’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
- [Code d’État du fichier](../extensibility/file-status-code-enumerator.md)
