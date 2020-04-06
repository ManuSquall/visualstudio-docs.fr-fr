---
title: Fonction SccCheckin (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCheckin
helpviewer_keywords:
- SccCheckin function
ms.assetid: e3f26ac2-6163-42e1-a764-22cfea5a3bc6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a5ba512642e1a63d9d39856f96194d717583d44f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701181"
---
# <a name="scccheckin-function"></a>Fonction SccCheckin
Cette fonction vérifie les fichiers précédemment vérifiés au système de contrôle source, en stockant les modifications et en créant une nouvelle version. Cette fonction est appelée avec un compte et un tableau de noms des fichiers à vérifier.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccCheckin (
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPSTR*    lpFileNames,
   LPCSTR    lpComment,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Paramètres
 pvContexte

[dans] La structure de contexte de plug-in de contrôle de source.

 hWnd

[dans] Une poignée à la fenêtre IDE que le plug-in SCC peut utiliser comme parent pour toutes les boîtes de dialogue qu’il fournit.

 nFiles

[dans] Nombre de fichiers sélectionnés pour être enregistrés.

 lpFileNames

[dans] Array de noms de chemin local entièrement qualifiés des fichiers à vérifier.

 lpComment

[dans] Commentaire à appliquer à chacun des fichiers sélectionnés enregistrés. Ce paramètre est `NULL` si le plug-in de contrôle source devrait inciter à un commentaire.

 fOptions

[dans] Drapeaux de commandement, `SCC_KEEP_CHECKEDOUT`soit 0 ou .

 pvOptions

[dans] Options spécifiques au plug-in du SCC.

## <a name="return-value"></a>Valeur retournée
 La mise en œuvre plug-in de cette fonction de contrôle source devrait renvoyer l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|Le fichier a été enregistré avec succès.|
|SCC_E_FILENOTCONTROLLED|Le fichier sélectionné n’est pas sous contrôle de code source.|
|SCC_E_ACCESSFAILURE|Il y avait un problème d’accès au système de contrôle à la source, probablement en raison de problèmes de réseau ou de contention. Une nouvelle tentative est recommandée.|
|SCC_E_NONSPECIFICERROR|Défaillance non spécifique. Le fichier n’a pas été enregistré.|
|SCC_E_NOTCHECKEDOUT|L’utilisateur n’a pas vérifié le fichier, donc ne peut pas l’enregistrer.|
|SCC_E_CHECKINCONFLICT|Checkin n’a pas pu être effectué parce que:<br /><br /> - Un autre utilisateur `bAutoReconcile` s’est enregistré à l’avance et était faux.<br /><br /> -ou-<br /><br /> - L’auto-fusion ne peut pas être faite (par exemple, lorsque les fichiers sont binaires).|
|SCC_E_VERIFYMERGE|Le fichier a été auto-fusionné mais n’a pas été vérifié en attendant la vérification de l’utilisateur.|
|SCC_E_FIXMERGE|Le fichier a été auto-fusionné mais n’a pas été enregistré en raison d’un conflit de fusion qui doit être résolu manuellement.|
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer cette opération.|
|SCC_I_OPERATIONCANCELED|L’opération a été annulée avant l’achèvement.|
|SCC_I_RELOADFILE|Un fichier ou un projet doit être rechargé.|
|SCC_E_FILENOTEXIST|Le dossier local n’a pas été trouvé.|

## <a name="remarks"></a>Notes
 Le commentaire s’applique à tous les fichiers enregistrés. L’argument de `null` commentaire peut être une chaîne, auquel cas le plug-in de contrôle source peut inciter l’utilisateur pour une chaîne de commentaire pour chaque fichier.

 L’argument `fOptions` peut être donné `SCC_KEEP_CHECKEDOUT` une valeur du drapeau pour indiquer l’intention de l’utilisateur de vérifier le fichier et le vérifier à nouveau.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API plug-in de contrôle des sources](../extensibility/source-control-plug-in-api-functions.md)
