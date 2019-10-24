---
title: SccQueryInfo fonction) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryInfo
helpviewer_keywords:
- SccQueryInfo function
ms.assetid: 3973d336-a9b7-41a2-a4e6-bb8184a96aaf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5807eb6b695e140350696436a8bba351687f4a24
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720827"
---
# <a name="sccqueryinfo-function"></a>Fonction SccQueryInfo
Cette fonction obtient les informations d’état d’un ensemble de fichiers sélectionnés sous contrôle de code source.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccQueryInfo(
   LPVOID  pvContext,
   LONG    nFiles,
   LPCSTR* lpFileNames,
   LPLONG  lpStatus
);
```

#### <a name="parameters"></a>Paramètres
 pvContext

dans Structure de contexte du plug-in de contrôle de code source.

 Nfichiers

dans Nombre de fichiers spécifiés dans le tableau `lpFileNames` et longueur du tableau `lpStatus`.

 lpFileNames

dans Tableau de noms des fichiers à interroger.

 lpStatus

[in, out] Tableau dans lequel le plug-in de contrôle de code source retourne les indicateurs d’état de chaque fichier. Pour plus d’informations, consultez [code d’État du fichier](../extensibility/file-status-code-enumerator.md).

## <a name="return-value"></a>Valeur de retour
 L’implémentation du plug-in de contrôle de code source de cette fonction est supposée retourner l’une des valeurs suivantes :

|valeur|Description|
|-----------|-----------------|
|SCC_OK|La requête a réussi.|
|SCC_E_ACCESSFAILURE|Un problème est survenu lors de l’accès au système de contrôle de code source, probablement en raison de problèmes de réseau ou de contention. Une nouvelle tentative est recommandée.|
|SCC_E_PROJNOTOPEN|Le projet n’est pas ouvert sous le contrôle de code source.|
|SCC_E_NONSPECIFICERROR|Échec non spécifique.|

## <a name="remarks"></a>Notes
 Si `lpFileName` est une chaîne vide, il n’existe actuellement aucune information d’État à mettre à jour. Dans le cas contraire, il s’agit du nom de chemin d’accès complet du fichier pour lequel les informations d’État ont peut-être changé.

 Le tableau de retour peut être un masque de bits de `SCC_STATUS_xxxx` bits. Pour plus d’informations, consultez [code d’État du fichier](../extensibility/file-status-code-enumerator.md). Un système de contrôle de code source ne prend peut-être pas en charge tous les types de bits. Par exemple, si `SCC_STATUS_OUTOFDATE` n’est pas disponible, le bit n’est pas défini.

 Lorsque vous utilisez cette fonction pour extraire des fichiers, notez les conditions d’État `MSSCCI` suivantes :

- `SCC_STATUS_OUTBYUSER` est définie lorsque l’utilisateur actuel a extrait le fichier.

- `SCC_STATUS_CHECKEDOUT` ne peut pas être défini si `SCC_STATUS_OUTBYUSER` n’est pas défini.

- `SCC_STATUS_CHECKEDOUT` est défini uniquement lorsque le fichier est extrait dans le répertoire de travail désigné.

- Si le fichier est extrait par l’utilisateur actuel dans un répertoire autre que le répertoire de travail, `SCC_STATUS_OUTBYUSER` est défini, mais pas `SCC_STATUS_CHECKEDOUT`.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
- [Code d’état de fichier](../extensibility/file-status-code-enumerator.md)