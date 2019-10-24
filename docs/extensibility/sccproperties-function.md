---
title: SccProperties fonction) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccProperties
helpviewer_keywords:
- SccProperties function
ms.assetid: 1bed38c9-73d2-4474-9717-f9dc26a89cbe
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e269727441eebc93cd78b70f11fdb571f111ee8b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720849"
---
# <a name="sccproperties-function"></a>Fonction SccProperties
Cette fonction affiche les propriétés du contrôle de code source pour un fichier ou un projet.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccProperties (
   LPVOID pvContext,
   HWND   hWnd,
   LPCSTR lpFileName
);
```

#### <a name="parameters"></a>Paramètres
 pvContext

dans Structure de contexte du plug-in de contrôle de code source.

 hWnd

dans Handle de la fenêtre IDE que le plug-in de contrôle de code source peut utiliser comme parent pour toutes les boîtes de dialogue qu’il fournit.

 lpFileName

dans Nom de chemin d’accès qualifié complet du fichier ou du projet.

## <a name="return-value"></a>Valeur de retour
 L’implémentation du plug-in de contrôle de code source de cette fonction est supposée retourner l’une des valeurs suivantes :

|valeur|Description|
|-----------|-----------------|
|SCC_OK|Les propriétés ont été correctement affichées.|
|SCC_I_RELOADFILE|Le système de gestion de version a modifié les propriétés du fichier, de sorte que l’IDE doit recharger ce fichier.|
|SCC_E_PROJNOTOPEN|Le projet spécifié n’a pas été ouvert dans le contrôle de code source.|
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à afficher les propriétés de ce fichier ou de ce projet.|
|SCC_E_FILENOTCONTROLLED|Le fichier ou le projet spécifié n’est pas sous contrôle de code source.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Une erreur inconnue ou générale s’est produite.|

## <a name="remarks"></a>Notes
 Le plug-in de contrôle de code source affiche les propriétés dans sa propre boîte de dialogue.

 Les propriétés sont définies par le plug-in de contrôle de code source et peuvent différer d’un plug-in à un plug-in. Si le plug-in permet à l’utilisateur de modifier les propriétés du contrôle de code source d’un fichier, il doit retourner `SCC_I_RELOAD` pour signaler à l’IDE que ce fichier ou ce projet doit être rechargé.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)