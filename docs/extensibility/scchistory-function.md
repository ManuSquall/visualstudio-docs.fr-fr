---
title: Fonction SccHistory (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccHistory
helpviewer_keywords:
- SccHistory function
ms.assetid: a636d9d3-47c1-4b48-ac6b-bcfde19d6cf9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 734afefd97e61867076d487acbcf67f10f54e672
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700666"
---
# <a name="scchistory-function"></a>Fonction SccHistory
Cette fonction affiche l’historique des fichiers spécifiés.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccHistory(
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

#### <a name="parameters"></a>Paramètres
 `pvContext`

[dans] La structure de contexte de plug-in de contrôle de source.

 `hWnd`

[dans] Une poignée à la fenêtre IDE que le plug-in de contrôle source peut utiliser comme parent pour toutes les boîtes de dialogue qu’il fournit.

 `nFiles`

[dans] Nombre de fichiers `lpFileName` spécifiés dans le tableau.

 `lpFileName`

[dans] Array de noms de fichiers entièrement qualifiés.

 `fOptions`

[dans] Drapeaux de commandement (actuellement non utilisés).

 `pvOptions`

[dans] Options spécifiques au plug-in de contrôle des sources.

## <a name="return-value"></a>Valeur de retour
 La mise en œuvre plug-in de cette fonction de contrôle source devrait renvoyer l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|L’historique de la version a été obtenu avec succès.|
|SCC_I_RELOADFILE|Le système de contrôle source effectivement modifié le fichier sur le disque tout en allant chercher l’historique (par exemple, en obtenant une ancienne version de celui-ci), de sorte que l’IDE devrait recharger ce fichier.|
|SCC_E_FILENOTCONTROLLED|Le fichier n'est pas soumis au contrôle de code source.|
|SCC_E_OPNOTSUPPORTED|Le système de contrôle à la source ne prend pas en charge cette opération.|
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer cette opération.|
|SCC_E_ACCESSFAILURE|Il y avait un problème d’accès au système de contrôle à la source, probablement en raison de problèmes de réseau ou de contention. Une nouvelle tentative est recommandée.|
|SCC_E_PROJNOTOPEN|Le projet n’a pas été ouvert.|
|SCC_E_NONSPECIFICERROR|Défaillance non spécifique. L’historique des dossiers n’a pu être obtenu.|

## <a name="remarks"></a>Notes
 Le plug-in de contrôle source peut afficher sa propre boîte `hWnd` de dialogue pour afficher l’historique de chaque fichier, en utilisant comme fenêtre parente. Alternativement, la fonction de rappel de sortie de texte facultative fournie au [SccOpenProject](../extensibility/sccopenproject-function.md) peut être utilisée, si elle est prise en charge.

 Notez que, dans certaines circonstances, le dossier examiné peut changer lors de l’exécution de cet appel. Par exemple, [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] la commande d’historique donne à l’utilisateur une chance d’obtenir une ancienne version du fichier. Dans un tel cas, le plug-in de contrôle source retourne `SCC_I_RELOAD` pour avertir l’IDE qu’il doit recharger le fichier.

> [!NOTE]
> Si le plug-in de contrôle source ne prend pas en charge cette fonction pour un tableau de fichiers, seul l’historique de fichier pour le premier fichier peut être affiché.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
