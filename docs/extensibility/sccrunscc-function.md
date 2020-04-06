---
title: Fonction SccRunScc (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRunScc
helpviewer_keywords:
- SccRunScc function
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d012908e59be8b82e34ff68cdab1945c5bd2de8b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700407"
---
# <a name="sccrunscc-function"></a>Fonction SccRunScc
Cette fonction invoque l’outil d’administration du contrôle source.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccRunScc(
   LPVOID  pvContext,
   HWND    hWnd,
   LONG    nFiles,
   LPCSTR* lpFileNames
);
```

#### <a name="parameters"></a>Paramètres
 pvContexte

[dans] La structure de contexte de plug-in de contrôle de source.

 hWnd

[dans] Une poignée à la fenêtre IDE que le plug-in de contrôle source peut utiliser comme parent pour toutes les boîtes de dialogue qu’il fournit.

 nFiles

[dans] Nombre de fichiers `lpFileNames` spécifiés dans le tableau.

 lpFileNames

[dans] Array de noms de fichiers sélectionnés.

## <a name="return-value"></a>Valeur de retour
 La mise en œuvre plug-in de cette fonction de contrôle source devrait renvoyer l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|L’outil d’administration du contrôle source a été invoqué avec succès.|
|SCC_I_OPERATIONCANCELED|L’opération a été annulée.|
|SCC_E_INITIALIZEFAILED|N’a pas réussi à initialiser le système de contrôle source.|
|SCC_E_ACCESSFAILURE|Il y avait un problème d’accès au système de contrôle à la source, probablement en raison de problèmes de réseau ou de contention.|
|SCC_E_CONNECTIONFAILURE|N’a pas réussi à se connecter au système de contrôle source.|
|SCC_E_FILENOTCONTROLLED|Le fichier sélectionné n’est pas sous contrôle source.|
|SCC_E_NONSPECIFICERROR|Défaillance non spécifique.|

## <a name="remarks"></a>Notes
 Cette fonction permet à l’appelant d’accéder à toute la gamme des fonctionnalités du système de contrôle source grâce à un outil d’administration externe. Si le système de contrôle source n’a pas d’interface utilisateur, le plug-in de contrôle source peut implémenter une interface pour effectuer les fonctions d’administration nécessaires.

 Cette fonction est appelée avec un nombre et un tableau de noms de fichiers pour les fichiers actuellement sélectionnés. Si l’outil d’administration le prend en charge, la liste des fichiers peut être utilisée pour présélectionner les fichiers dans l’interface d’administration; autrement, la liste peut être ignorée.

 Cette fonction est généralement invoquée lorsque l’utilisateur sélectionne le **serveur de contrôle source de lancement \<>** dans le menu De contrôle des**sources** de **fichiers.** ->  Cette option de menu **de lancement** peut être toujours désactivée ou même cachée en définissant une inscription au registre. Voir [comment : Installer un plug-in de contrôle des sources](../extensibility/internals/how-to-install-a-source-control-plug-in.md) pour plus de détails. Cette fonction est appelée uniquement si [SccInitialize](../extensibility/sccinitialize-function.md) retourne le bit de capacité `SCC_CAP_RUNSCC` (voir drapeaux de [capacité](../extensibility/capability-flags.md) pour plus de détails sur ce bits et d’autres fonctionnalités).

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
- [Guide pratique pour installer un plug-in de contrôle de code source](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [Indicateurs de capacité](../extensibility/capability-flags.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
