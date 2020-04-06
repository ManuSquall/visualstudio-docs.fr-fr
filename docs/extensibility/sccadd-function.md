---
title: Fonction SccAdd (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAdd
helpviewer_keywords:
- SccAdd function
ms.assetid: 545268f3-8e83-446a-a398-1a9db9e866e8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 23a6226b0d3cc2441a509c16b2e4672a766f3329
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701311"
---
# <a name="sccadd-function"></a>Fonction SccAdd
Cette fonction ajoute de nouveaux fichiers au système de contrôle source.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccAdd(
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LPCSTR    lpComment,
   LONG*     pfOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Paramètres
 pvContexte

[dans] La structure de contexte de plug-in de contrôle de source.

 hWnd

[dans] Une poignée à la fenêtre IDE que le plug-in de contrôle source peut utiliser comme parent pour toutes les boîtes de dialogue qu’il fournit.

 nFiles

[dans] Nombre de fichiers sélectionnés pour être ajoutés `lpFileNames` au projet en cours tel qu’il est donné dans le tableau.

 lpFileNames

[dans] Array de noms locaux entièrement qualifiés de fichiers à ajouter.

 lpComment

[dans] Le commentaire à appliquer à tous les fichiers ajoutés.

 pfOptions

[dans] Array de drapeaux de commande, fournis sur une base par fichier.

 pvOptions

[dans] Options spécifiques au plug-in de contrôle des sources.

## <a name="return-value"></a>Valeur retournée
 La mise en œuvre plug-in de cette fonction de contrôle source devrait renvoyer l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|L’opération add a été couronnée de succès.|
|SCC_E_FILEALREADYEXISTS|Le fichier sélectionné est déjà sous contrôle source.|
|SCC_E_TYPENOTSUPPORTED|Le type de fichier (par exemple, binaire) n’est pas pris en charge par le système de contrôle source.|
|SCC_E_OPNOTSUPPORTED|Le système de contrôle à la source ne prend pas en charge cette opération.|
|SCC_E_ACCESSFAILURE|Il y avait un problème d’accès au système de contrôle à la source, probablement en raison de problèmes de réseau ou de contention. Une nouvelle tentative est recommandée.|
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer cette opération.|
|SCC_E_NONSPECIFICERROR|Défaillance non spécifique; ajouter non exécuté.|
|SCC_I_OPERATIONCANCELED|L’opération a été annulée avant l’achèvement.|
|SCC_I_RELOADFILE|Un fichier ou un projet doit être rechargé.|
|SCC_E_FILENOTEXIST|Le dossier local n’a pas été trouvé.|

## <a name="remarks"></a>Notes
 Les `fOptions` habituels sont remplacés `pfOptions`ici `LONG` par un tableau, , avec une spécification d’option par fichier. C’est parce que le type de fichier peut varier d’un fichier à l’autre.

> [!NOTE]
> Il est invalide `SCC_FILETYPE_TEXT` `SCC_FILETYPE_BINARY` de spécifier à la fois et des options pour le même fichier, mais il est valable de spécifier ni l’un ni l’autre. Le réglage n’est `SCC_FILETYPE_AUTO`pas non plus le même que le réglage, auquel cas le plug-in de contrôle source autodétecte le type de fichier.

 Voici la liste des drapeaux `pfOptions` utilisés dans le tableau:

|Option|Valeur|Signification|
|------------|-----------|-------------|
|SCC_FILETYPE_AUTO|0x00|Le plug-in de contrôle source doit détecter le type de fichier.|
|SCC_FILETYPE_TEXT|0x01|Indique un fichier texte ASCII.|
|SCC_FILETYPE_BINARY|0x02|Indique un type de fichier autre que le texte ASCII.|
|SCC_ADD_STORELATEST|0x04|Stocke seulement la dernière copie du fichier, pas de deltas.|
|SCC_FILETYPE_TEXT_ANSI|0x08|Traite le fichier comme un texte DE l’ANSI.|
|SCC_FILETYPE_UTF8|0x10|Traite le fichier comme texte Unicode en format UTF8.|
|SCC_FILETYPE_UTF16LE|0x20|Traite le fichier comme texte Unicode dans le format UTF16 Little Endian.|
|SCC_FILETYPE_UTF16BE|0x40|Traite le fichier comme texte Unicode dans le format BIG Endian UTF16.|

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API plug-in de contrôle des sources](../extensibility/source-control-plug-in-api-functions.md)
