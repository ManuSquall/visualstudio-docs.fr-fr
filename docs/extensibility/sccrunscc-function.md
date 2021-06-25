---
description: Cette fonction appelle l’outil d’administration du contrôle de code source.
title: SccRunScc fonction) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccRunScc
helpviewer_keywords:
- SccRunScc function
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c865931ed52601761f0bd519bf360d584d49ec04
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904111"
---
# <a name="sccrunscc-function"></a>Fonction SccRunScc
Cette fonction appelle l’outil d’administration du contrôle de code source.

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
 pvContext

dans Structure de contexte du plug-in de contrôle de code source.

 hWnd

dans Handle de la fenêtre IDE que le plug-in de contrôle de code source peut utiliser comme parent pour toutes les boîtes de dialogue qu’il fournit.

 Nfichiers

dans Nombre de fichiers spécifiés dans le `lpFileNames` tableau.

 lpFileNames

dans Tableau de noms de fichiers sélectionnés.

## <a name="return-value"></a>Valeur renvoyée
 L’implémentation du plug-in de contrôle de code source de cette fonction est supposée retourner l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|L’outil d’administration du contrôle de code source a été appelé avec succès.|
|SCC_I_OPERATIONCANCELED|L’opération a été annulée.|
|SCC_E_INITIALIZEFAILED|Échec de l’initialisation du système de contrôle de code source.|
|SCC_E_ACCESSFAILURE|Un problème est survenu lors de l’accès au système de contrôle de code source, probablement en raison de problèmes de réseau ou de contention.|
|SCC_E_CONNECTIONFAILURE|Échec de la connexion au système de contrôle de code source.|
|SCC_E_FILENOTCONTROLLED|Le fichier sélectionné n’est pas sous contrôle de code source.|
|SCC_E_NONSPECIFICERROR|Échec non spécifique.|

## <a name="remarks"></a>Remarques
 Cette fonction permet à l’appelant d’accéder à la gamme complète des fonctionnalités du système de contrôle de code source via un outil d’administration externe. Si le système de contrôle de code source n’a pas d’interface utilisateur, le plug-in de contrôle de code source peut implémenter une interface pour exécuter les fonctions d’administration nécessaires.

 Cette fonction est appelée avec un nombre et un tableau de noms de fichiers pour les fichiers actuellement sélectionnés. Si l’outil d’administration le prend en charge, la liste des fichiers peut être utilisée pour présélectionner des fichiers dans l’interface d’administration. dans le cas contraire, la liste peut être ignorée.

 Cette fonction est généralement appelée lorsque l’utilisateur sélectionne le **lancement \<Source Control Server>** dans le menu du contrôle de source de **fichier**  ->   . Cette option de menu **Launch** peut être toujours désactivée ou même masquée en définissant une entrée de registre. Pour plus d’informations, consultez [Comment : installer un plug-in de contrôle de code source](../extensibility/internals/how-to-install-a-source-control-plug-in.md) . Cette fonction est appelée uniquement si [SccInitialize](../extensibility/sccinitialize-function.md) retourne le `SCC_CAP_RUNSCC` bit de fonctionnalité (consultez [indicateurs de fonctionnalité](../extensibility/capability-flags.md) pour plus d’informations sur ce bits de fonctionnalité et d’autres).

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
- [Guide pratique pour installer un plug-in de contrôle de code source](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [Indicateurs de capacité](../extensibility/capability-flags.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
