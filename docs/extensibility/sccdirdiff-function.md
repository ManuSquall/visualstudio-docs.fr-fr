---
title: Fonction SccDirDiff (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDirDiff
helpviewer_keywords:
- SccDirDiff function
ms.assetid: 26c9ba92-e3b9-4dd2-bd5e-76b17745e308
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1bb592a1174a91480ed76ef818733c288c5273c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701015"
---
# <a name="sccdirdiff-function"></a>Fonction SccDirDiff
Cette fonction affiche les différences entre l’annuaire local actuel sur le disque client et le projet correspondant sous contrôle source.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccDirDiff(
   LPVOID    pContext,
   HWND      hWnd,
   LPCSTR    lpDirName,
   LONG      dwFlags,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Paramètres
 pContext

[dans] La structure de contexte de plug-in de contrôle de source.

 hWnd

[dans] Une poignée à la fenêtre IDE que le plug-in de contrôle source peut utiliser comme parent pour toutes les boîtes de dialogue qu’il fournit.

 lpDirName

[dans] Chemin entièrement qualifié vers l’annuaire local pour lequel montrer une différence visuelle.

 dwFlags

[dans] Drapeaux de commandement (voir Section Remarques).

 pvOptions

[dans] Options spécifiques au plug-in de contrôle des sources.

## <a name="return-value"></a>Valeur retournée
 La mise en œuvre plug-in de cette fonction de contrôle source devrait renvoyer l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|L’annuaire sur disque est le même que le projet dans le contrôle du code source.|
|SCC_I_FILESDIFFER|L’annuaire sur disque est différent du projet dans le contrôle du code source.|
|SCC_I_RELOADFILE|Un fichier ou un projet doit être rechargé.|
|SCC_E_FILENOTCONTROLLED|L’annuaire n’est pas sous contrôle de code source.|
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer cette opération.|
|SCC_E_ACCESSFAILURE|Il y avait un problème d’accès au système de contrôle à la source, probablement en raison de problèmes de réseau ou de contention. Une nouvelle tentative est recommandée.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Défaillance non spécifique.|
|SCC_E_FILENOTEXIST|Le répertoire local n’a pas pu être trouvé.|

## <a name="remarks"></a>Notes
 Cette fonction est utilisée pour instruire le plug-in de contrôle source pour afficher à l’utilisateur une liste de modifications à un répertoire spécifié. Le plug-in ouvre sa propre fenêtre, dans un format de son choix, pour afficher les différences entre l’annuaire de l’utilisateur sur disque et le projet correspondant sous contrôle de version.

 Si un plug-in prend en charge la comparaison des répertoires, il doit soutenir la comparaison des répertoires sur une base de nom de fichier, même si les options de «quick-diff» ne sont pas prises en charge.

|`dwFlags`|Interprétation|
|---------------|--------------------|
|SCC_DIFF_IGNORECASE|Comparaison insensible aux cas (peut être utilisée pour le diff rapide ou visuelle).|
|SCC_DIFF_IGNORESPACE|Ignore l’espace blanc (peut être utilisé pour le rapide-diff ou visuel).|
|SCC_DIFF_QD_CONTENTS|Si pris en charge par le plug-in de contrôle source, compare silencieusement l’annuaire, byte byte by byte.|
|SCC_DIFF_QD_CHECKSUM|Si pris en charge par plug-in, compare silencieusement l’annuaire via un checksum, ou, si elle n’est pas pris en charge, retombe à SCC_DIFF_QD_CONTENTS.|
|SCC_DIFF_QD_TIME|Si pris en charge par plug-in, compare silencieusement l’annuaire via son horaire, ou, si elle n’est pas pris en charge, retombe sur SCC_DIFF_QD_CHECKSUM ou SCC_DIFF_QD_CONTENTS.|

> [!NOTE]
> Cette fonction utilise les mêmes drapeaux de commande que le [SccDiff](../extensibility/sccdiff-function.md). Cependant, un plug-in de contrôle source peut choisir de ne pas soutenir l’opération « quick-diff » pour les répertoires.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API plug-in de contrôle des sources](../extensibility/source-control-plug-in-api-functions.md)
