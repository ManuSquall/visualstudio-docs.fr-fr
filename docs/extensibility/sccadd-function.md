---
description: Cette fonction ajoute de nouveaux fichiers au système de contrôle de code source.
title: SccAdd fonction) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccAdd
helpviewer_keywords:
- SccAdd function
ms.assetid: 545268f3-8e83-446a-a398-1a9db9e866e8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7f73a91f7f801ca89a633f1722e0c4d1183fb3dc
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904849"
---
# <a name="sccadd-function"></a>SccAdd fonction)
Cette fonction ajoute de nouveaux fichiers au système de contrôle de code source.

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
 pvContext

dans Structure de contexte du plug-in de contrôle de code source.

 hWnd

dans Handle de la fenêtre IDE que le plug-in de contrôle de code source peut utiliser comme parent pour toutes les boîtes de dialogue qu’il fournit.

 Nfichiers

dans Nombre de fichiers sélectionnés à ajouter au projet actif, comme indiqué dans le `lpFileNames` tableau.

 lpFileNames

dans Tableau de noms locaux complets des fichiers à ajouter.

 lpComment

dans Commentaire à appliquer à tous les fichiers en cours d’ajout.

 pfOptions

dans Tableau d’indicateurs de commande, fourni pour chaque fichier.

 pvOptions

dans Options spécifiques au plug-in de contrôle de code source.

## <a name="return-value"></a>Valeur retournée
 L’implémentation du plug-in de contrôle de code source de cette fonction est supposée retourner l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|L’opération d’ajout a réussi.|
|SCC_E_FILEALREADYEXISTS|Le fichier sélectionné est déjà sous contrôle de code source.|
|SCC_E_TYPENOTSUPPORTED|Le type du fichier (par exemple, binaire) n’est pas pris en charge par le système de contrôle de code source.|
|SCC_E_OPNOTSUPPORTED|Le système de contrôle de code source ne prend pas en charge cette opération.|
|SCC_E_ACCESSFAILURE|Un problème est survenu lors de l’accès au système de contrôle de code source, probablement en raison de problèmes de réseau ou de contention. Une nouvelle tentative est recommandée.|
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer cette opération.|
|SCC_E_NONSPECIFICERROR|Échec non spécifique ; ajout non effectué.|
|SCC_I_OPERATIONCANCELED|L’opération a été annulée avant la fin.|
|SCC_I_RELOADFILE|Un fichier ou un projet doit être rechargé.|
|SCC_E_FILENOTEXIST|Fichier local introuvable.|

## <a name="remarks"></a>Remarques
 Les options habituelles `fOptions` sont remplacées ici par un tableau, `pfOptions` , avec une `LONG` spécification d’option par fichier. Cela est dû au fait que le type de fichier peut varier d’un fichier à un fichier.

> [!NOTE]
> Il n’est pas possible de spécifier les deux `SCC_FILETYPE_TEXT` `SCC_FILETYPE_BINARY` options et pour le même fichier, mais il est possible de spécifier l’un ni l’autre. Le fait de ne pas être le même que le paramètre `SCC_FILETYPE_AUTO` , auquel cas le plug-in de contrôle de code source détecte automatiquement le type de fichier.

 Voici la liste des indicateurs utilisés dans le `pfOptions` tableau :

|Option|Valeur|Signification|
|------------|-----------|-------------|
|SCC_FILETYPE_AUTO|0x00|Le plug-in de contrôle de code source doit détecter le type de fichier.|
|SCC_FILETYPE_TEXT|0x01|Indique un fichier texte ASCII.|
|SCC_FILETYPE_BINARY|0x02|Indique un type de fichier autre qu’un texte ASCII.|
|SCC_ADD_STORELATEST|0x04|Stocke uniquement la copie la plus récente du fichier, pas de Delta.|
|SCC_FILETYPE_TEXT_ANSI|0x08|Traite le fichier comme du texte ANSI.|
|SCC_FILETYPE_UTF8|0x10|Traite le fichier en tant que texte Unicode au format UTF8.|
|SCC_FILETYPE_UTF16LE|0x20|Traite le fichier en tant que texte Unicode au format Little endian UTF16.|
|SCC_FILETYPE_UTF16BE|0x40|Traite le fichier en tant que texte Unicode au format Big endian UTF16.|

## <a name="see-also"></a>Voir aussi
- [Fonctions de l’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
