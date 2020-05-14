---
title: Fonction SccGetEvents (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetEvents
helpviewer_keywords:
- SccGetEvents function
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 91b3debf0e686ceece3048cf3d92b629e3359edd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700820"
---
# <a name="sccgetevents-function"></a>Fonction SccGetEvents
Cette fonction récupère un événement de statut en file d’attente.

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
 pvContexte

[dans] La structure de contexte de plug-in de contrôle de source.

 lpFileName

[dans, dehors] Tampon où le plug-in de contrôle source met le nom de fichier retourné (jusqu’à _MAX_PATH caractères).

 lpStatus

[dans, dehors] Retourne le code d’état (voir [Code d’état du fichier](../extensibility/file-status-code-enumerator.md) pour les valeurs possibles).

 pnEventsRemaining

[dans, dehors] Renvoie le nombre d’entrées laissées dans la file d’attente après cet appel. Si ce numéro est grand, l’appelant peut décider d’appeler le [SccQueryInfo](../extensibility/sccqueryinfo-function.md) pour obtenir toutes les informations à la fois.

## <a name="return-value"></a>Valeur retournée
 La mise en œuvre plug-in de cette fonction de contrôle source devrait renvoyer l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|Obtenez des événements réussis.|
|SCC_E_OPNOTSUPPORTED|Cette fonction n'est pas prise en charge.|
|SCC_E_NONSPECIFICERROR|Défaillance non spécifique.|

## <a name="remarks"></a>Notes
 Cette fonction est appelée pendant le traitement au ralenti pour voir s’il y a eu des mises à jour de statut pour les fichiers sous contrôle source. Le plug-in de contrôle source maintient l’état de tous les fichiers qu’il connaît, et chaque fois qu’un changement de statut est noté par le plug-in, l’état et le fichier associé sont stockés dans une file d’attente. Lorsqu’on `SccGetEvents` l’appelle, l’élément supérieur de la file d’attente est récupéré et retourné. Cette fonction est contrainte de retourner seulement les informations précédemment mises en cache et doit avoir un revirement très rapide (c’est-à-dire pas de lecture du disque ou demander le système de contrôle source pour le statut); sinon, les performances de l’IDE peuvent commencer à se dégrader.

 S’il n’y a pas de mise à jour d’état à `lpFileName`signaler, le plug-in de contrôle source stocke une chaîne vide dans le tampon indiqué par . Dans le cas contraire, le plug-in stocke le nom complet du fichier pour lequel les informations de statut a changé et renvoie le code de statut approprié (l’une des valeurs détaillées dans le [code d’état du fichier](../extensibility/file-status-code-enumerator.md)).

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API plug-in de contrôle des sources](../extensibility/source-control-plug-in-api-functions.md)
- [Code d’état du fichier](../extensibility/file-status-code-enumerator.md)
