---
title: Fonction SccProperties (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccProperties
helpviewer_keywords:
- SccProperties function
ms.assetid: 1bed38c9-73d2-4474-9717-f9dc26a89cbe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf2dd87efbb50346093144db6e069eea30138e37
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700506"
---
# <a name="sccproperties-function"></a>Fonction SccProperties
Cette fonction affiche les propriétés de contrôle de source pour un fichier ou un projet.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccProperties (
   LPVOID pvContext,
   HWND   hWnd,
   LPCSTR lpFileName
);
```

#### <a name="parameters"></a>Paramètres
 pvContexte

[dans] La structure de contexte de plug-in de contrôle de source.

 hWnd

[dans] Une poignée à la fenêtre IDE que le plug-in de contrôle source peut utiliser comme parent pour toutes les boîtes de dialogue qu’il fournit.

 lpFileName

[dans] Le nom de chemin entièrement qualifié du fichier ou du projet.

## <a name="return-value"></a>Valeur de retour
 La mise en œuvre plug-in de cette fonction de contrôle source devrait renvoyer l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|Les propriétés ont été affichées avec succès.|
|SCC_I_RELOADFILE|Le système de contrôle de version a modifié les propriétés du fichier, de sorte que l’IDE devrait recharger ce fichier.|
|SCC_E_PROJNOTOPEN|Le projet spécifié n’a pas été ouvert dans le contrôle des sources.|
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à afficher les propriétés de ce fichier ou de ce projet.|
|SCC_E_FILENOTCONTROLLED|Le fichier ou le projet spécifié n’est pas sous contrôle source.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Une erreur inconnue ou générale s’est produite.|

## <a name="remarks"></a>Notes
 Le plug-in de contrôle source affiche les propriétés dans sa propre boîte de dialogue.

 Les propriétés sont définies par le plug-in de contrôle source et peuvent différer du plug-in au plug-in. Si le plug-in permet à l’utilisateur de modifier les `SCC_I_RELOAD` propriétés de contrôle source d’un fichier, il doit revenir pour signaler à l’IDE que ce fichier ou projet doit être rechargé.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
