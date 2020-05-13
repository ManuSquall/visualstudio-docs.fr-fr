---
title: Fonction SccDiff (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDiff
helpviewer_keywords:
- SccDiff function
ms.assetid: d49bc8c5-f631-4153-9d3c-feb3564da305
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9b68df68ce7fa4ad5cbc98db256204ddf8623d2c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701019"
---
# <a name="sccdiff-function"></a>Fonction SccDiff
Cette fonction affiche (ou il suffit de vérifier) les différences entre le fichier actuel (sur le disque local) et sa dernière version enregistrée dans le système de contrôle source.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccDiff(
   LPVOID    pvContext,
   HWND      hWnd,
   LPCSTR    lpFileName,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Paramètres
 pvContexte

[dans] La structure de contexte de plug-in de contrôle de source.

 hWnd

[dans] Une poignée à la fenêtre IDE que le plug-in de contrôle source peut utiliser comme parent pour toutes les boîtes de dialogue qu’il fournit.

 lpFileName

[dans] Nom de fichier pour lequel la différence est demandée.

 fOptions

[dans] Drapeaux de commandement. Pour plus de détails, consultez la section Notes.

 pvOptions

[dans] Options spécifiques au plug-in de contrôle des sources.

## <a name="return-value"></a>Valeur retournée
 La mise en œuvre plug-in de cette fonction de contrôle source devrait renvoyer l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|La copie de travail et la version serveur sont identiques.|
|SCC_I_FILESDIFFERS|La copie de travail diffère de la version sous contrôle source.|
|SCC_I_RELOADFILE|Un fichier ou un projet doit être rechargé.|
|SCC_E_FILENOTCONTROLLED|Le fichier n'est pas soumis au contrôle de code source.|
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer cette opération.|
|SCC_E_ACCESSFAILURE|Il y avait un problème d’accès au système de contrôle à la source, probablement en raison de problèmes de réseau ou de contention. Une nouvelle tentative est recommandée.|
|SCC_E_NONSPECIFICERROR|Défaillance non spécifique; différence de dossier n’a pas été obtenue.|
|SCC_E_FILENOTEXIST|Le dossier local n’a pas été trouvé.|

## <a name="remarks"></a>Notes
 Cette fonction a deux buts différents. Par défaut, il affiche une liste de modifications à un fichier. Le plug-in de contrôle source ouvre sa propre fenêtre, quel que soit le format qu’il choisit, pour afficher les différences entre le fichier de l’utilisateur sur disque et la dernière version du fichier sous contrôle source.

 Alternativement, l’IDE peut simplement avoir besoin de déterminer si un fichier a changé. Par exemple, l’IDE peut avoir besoin de déterminer s’il est sûr de vérifier un fichier sans en informer l’utilisateur. Dans ce cas, l’IDE passe dans le `SCC_DIFF_CONTENTS` drapeau. Le plug-in de contrôle source doit vérifier le fichier sur disque, byte byte, contre le fichier contrôlé par la source et retourner une valeur indiquant si les deux fichiers sont différents sans rien afficher à l’utilisateur.

 En optimisant les performances, le plug-in de contrôle source peut utiliser une alternative basée sur un checksum `SCC_DIFF_CONTENTS`ou un temps au lieu de la comparaison byte-byte demandée par : ces formes de comparaison sont évidemment plus rapides mais moins fiables. Tous les systèmes de contrôle des sources ne peuvent pas prendre en charge ces méthodes de comparaison alternatives, et le plug-in peut devoir retomber à une comparaison de contenu. Tous les plug-ins de contrôle des sources doivent, au minimum, prendre en charge une comparaison de contenu.

> [!NOTE]
> Les drapeaux de différence rapide sont mutuellement exclusifs. Il est valable de ne pas passer de drapeaux, mais il n’est pas valable de passer simultanément plus d’un. `SCC_DIFF_QUICK_DIFF`, qui est un masque qui combine tous les drapeaux, peut être utilisé pour tester, mais il ne doit jamais être passé comme un paramètre.

|`fOption`|Signification|
|---------------|-------------|
|SCC_DIFF_IGNORECASE|Comparaison insensible aux cas (peut être utilisée pour une différence rapide ou visuelle).|
|SCC_DIFF_IGNORESPACE|Ignore l’espace blanc (peut être utilisé pour une différence rapide ou visuelle).|
|SCC_DIFF_QD_CONTENTS|Compare silencieusement le fichier, byte byte byte.|
|SCC_DIFF_QD_CHECKSUM|Compare silencieusement le fichier via un checksum lorsqu’il est pris en charge. S’il n’est pas pris en charge, retombe à une comparaison du contenu.|
|SCC_DIFF_QD_TIME|Compare silencieusement le fichier via son chrono lorsque pris en charge. S’il n’est pas pris en charge, retombe à une comparaison du contenu.|

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API plug-in de contrôle des sources](../extensibility/source-control-plug-in-api-functions.md)
