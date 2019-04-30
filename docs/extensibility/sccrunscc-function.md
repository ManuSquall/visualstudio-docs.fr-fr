---
title: Fonction SccRunScc | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRunScc
helpviewer_keywords:
- SccRunScc function
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e7400fc2b635c036f4bf9b2ff3632a20e628b50d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62800343"
---
# <a name="sccrunscc-function"></a>Fonction SccRunScc
Cette fonction appelle l’outil d’administration de contrôle source.

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

[in] La structure de contexte de plug-in de contrôle de source.

 hWnd

[in] Handle vers la fenêtre de l’IDE que le plug-in de contrôle de code source peut utiliser en tant que parent pour les boîtes de dialogue qu’il fournit.

 nFiles

[in] Nombre de fichiers spécifiés dans le `lpFileNames` tableau.

 lpFileNames

[in] Tableau des noms de fichier sélectionné.

## <a name="return-value"></a>Valeur de retour
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :

|Value|Description|
|-----------|-----------------|
|SCC_OK|L’outil d’administration de contrôle source a été appelé.|
|SCC_I_OPERATIONCANCELED|L’opération a été annulée.|
|SCC_E_INITIALIZEFAILED|Impossible d’initialiser le système de contrôle de code source.|
|SCC_E_ACCESSFAILURE|Impossible d’accéder au système de contrôle source, probablement en raison de problèmes réseau ou de contention.|
|SCC_E_CONNECTIONFAILURE|Impossible de se connecter au système de contrôle source.|
|SCC_E_FILENOTCONTROLLED|Le fichier sélectionné n’est pas sous contrôle de code source.|
|SCC_E_NONSPECIFICERROR|Erreur non spécifique.|

## <a name="remarks"></a>Notes
 Cette fonction permet à l’appelant pour accéder à la gamme complète des fonctionnalités du système de contrôle de source via un outil d’administration externe. Si le système de contrôle de code source n’a aucun interface utilisateur, le plug-in de contrôle de code source peut implémenter une interface pour effectuer des fonctions d’administration nécessaires.

 Cette fonction est appelée avec un nombre et un tableau de noms de fichiers pour les fichiers actuellement sélectionnés. Si l’outil d’administration prend en charge, la liste des fichiers peut servir à présélectionner des fichiers dans l’interface d’administration ; Sinon, la liste peut être ignorée.

 Cette fonction est généralement appelée lorsque l’utilisateur sélectionne le **lancer \<Source Control Server >** à partir de la **fichier** -> **contrôle de code Source** menu. Cela **lancer** option de menu peut être toujours désactivée ou masquée en définissant une entrée de Registre. Voir [Guide pratique pour Installer un plug-in de contrôle de Source](../extensibility/internals/how-to-install-a-source-control-plug-in.md) pour plus d’informations. Cette fonction est appelée uniquement si [SccInitialize](../extensibility/sccinitialize-function.md) retourne le `SCC_CAP_RUNSCC` bit de fonctionnalité (voir [indicateurs de capacité](../extensibility/capability-flags.md) pour plus d’informations sur cette offre et autres bits de capacité).

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
- [Guide pratique pour installer un plug-in de contrôle de code source](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [Indicateurs de capacité](../extensibility/capability-flags.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)