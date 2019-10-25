---
title: SccRunScc fonction) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRunScc
helpviewer_keywords:
- SccRunScc function
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e577af3ce70280b81681cb72295c3511dd3ab4a4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720541"
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

dans Nombre de fichiers spécifiés dans le tableau de `lpFileNames`.

 lpFileNames

dans Tableau de noms de fichiers sélectionnés.

## <a name="return-value"></a>Valeur de retour
 L’implémentation du plug-in de contrôle de code source de cette fonction est supposée retourner l’une des valeurs suivantes :

|valeur|Description|
|-----------|-----------------|
|SCC_OK|L’outil d’administration du contrôle de code source a été appelé avec succès.|
|SCC_I_OPERATIONCANCELED|L’opération a été annulée.|
|SCC_E_INITIALIZEFAILED|Échec de l’initialisation du système de contrôle de code source.|
|SCC_E_ACCESSFAILURE|Un problème est survenu lors de l’accès au système de contrôle de code source, probablement en raison de problèmes de réseau ou de contention.|
|SCC_E_CONNECTIONFAILURE|Échec de la connexion au système de contrôle de code source.|
|SCC_E_FILENOTCONTROLLED|Le fichier sélectionné n’est pas sous contrôle de code source.|
|SCC_E_NONSPECIFICERROR|Échec non spécifique.|

## <a name="remarks"></a>Notes
 Cette fonction permet à l’appelant d’accéder à la gamme complète des fonctionnalités du système de contrôle de code source via un outil d’administration externe. Si le système de contrôle de code source n’a pas d’interface utilisateur, le plug-in de contrôle de code source peut implémenter une interface pour exécuter les fonctions d’administration nécessaires.

 Cette fonction est appelée avec un nombre et un tableau de noms de fichiers pour les fichiers actuellement sélectionnés. Si l’outil d’administration le prend en charge, la liste des fichiers peut être utilisée pour présélectionner des fichiers dans l’interface d’administration. dans le cas contraire, la liste peut être ignorée.

 Cette fonction est généralement appelée lorsque l’utilisateur sélectionne l' **> de lancement du serveur de contrôle \<Source** à partir du menu **fichier**  -> **contrôle de code source** . Cette option de menu **Launch** peut être toujours désactivée ou même masquée en définissant une entrée de registre. Pour plus d’informations, consultez [Comment : installer un plug-in de contrôle de code source](../extensibility/internals/how-to-install-a-source-control-plug-in.md) . Cette fonction est appelée uniquement si [SccInitialize](../extensibility/sccinitialize-function.md) retourne le bit de fonctionnalité `SCC_CAP_RUNSCC` (consultez les [indicateurs de fonctionnalité](../extensibility/capability-flags.md) pour plus d’informations sur ce bits de fonctionnalité et d’autres).

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
- [Guide pratique pour installer un plug-in de contrôle de code source](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [Indicateurs de capacité](../extensibility/capability-flags.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)