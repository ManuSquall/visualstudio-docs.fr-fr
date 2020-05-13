---
title: QUERYCHANGESFUNC - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- QUERYCHANGESFUNC
helpviewer_keywords:
- QUERYCHANGESFUNC callback function
- QUERYCHANGESDATA structure
ms.assetid: 9d383e2c-eee1-4996-973a-0652d4c5951c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30864cae95672f4026084a94c5474d165b124cba
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701630"
---
# <a name="querychangesfunc"></a>QUERYCHANGESFUNC
Il s’agit d’une fonction de rappel utilisée par l’opération [SccQueryChanges](../extensibility/sccquerychanges-function.md) pour énumérer une collection de noms de fichiers et déterminer l’état de chaque fichier.

 La `SccQueryChanges` fonction est donnée une liste de `QUERYCHANGESFUNC` fichiers et un pointeur à la rappel. Le plug-in de contrôle source énumère sur la liste donnée et fournit l’état (via ce rappel) pour chaque fichier de la liste.

## <a name="signature"></a>Signature

```cpp
typedef BOOL (*QUERYCHANGESFUNC)(
   LPVOID pvCallerData,
   QUERYCHANGESDATA * pChangesData
);
```

## <a name="parameters"></a>Paramètres
 pvCallerData

[dans] Le `pvCallerData` paramètre passé par l’appelant (l’IDE) à [SccQueryChanges](../extensibility/sccquerychanges-function.md). Le plug-in de contrôle source ne doit pas faire d’hypothèses sur le contenu de cette valeur.

 pChangesData (en)

[dans] Pointeur vers une structure [de structure QUERYCHANGESDATA](#LinkQUERYCHANGESDATA) décrivant les modifications apportées à un fichier.

## <a name="return-value"></a>Valeur retournée
 L’IDE renvoie un code d’erreur approprié :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|Continuer le traitement.|
|SCC_I_OPERATIONCANCELED|Arrêter le traitement.|
|SCC_E_xxx|Toute erreur appropriée de CSC devrait cesser le traitement.|

## <a name="querychangesdata-structure"></a><a name="LinkQUERYCHANGESDATA"></a>QUERYCHANGESDATA Structure
 La structure transmise pour chaque fichier ressemble à ce qui suit :

```cpp
struct QUERYCHANGESDATA_A
{
    DWORD  dwSize;
    LPCSTR lpFileName;
    DWORD  dwChangeType;
    LPCSTR lpLatestName;
};

typedef struct QUERYCHANGESDATA_A QUERYCHANGESDATA;

struct QUERYCHANGESDATA_W
{
    DWORD   dwSize;
    LPCWSTR lpFileName;
    DWORD   dwChangeType;
    LPCWSTR lpLatestName;
};
```

 dwSize Taille de cette structure (dans les octets).

 lpFileName Le nom de fichier original pour cet article.

 code dwChangeType indiquant l’état du fichier :

|Code|Description|
|----------|-----------------|
|`SCC_CHANGE_UNKNOWN`|Je ne peux pas dire ce qui a changé.|
|`SCC_CHANGE_UNCHANGED`|Aucun changement de nom pour ce fichier.|
|`SCC_CHANGE_DIFFERENT`|Fichier avec une identité différente, mais le même nom existe dans la base de données.|
|`SCC_CHANGE_NONEXISTENT`|Le fichier n’existe ni dans la base de données ni localement.|
|`SCC_CHANGE_DATABASE_DELETED`|Fichier supprimé dans la base de données.|
|`SCC_CHANGE_LOCAL_DELETED`|Fichier supprimé localement, mais le fichier existe toujours dans la base de données. Si cela ne peut `SCC_CHANGE_DATABASE_ADDED`pas être déterminé, retour .|
|`SCC_CHANGE_DATABASE_ADDED`|Fichier ajouté à la base de données, mais n’existe pas localement.|
|`SCC_CHANGE_LOCAL_ADDED`|Le fichier n’existe pas dans la base de données et est un nouveau fichier local.|
|`SCC_CHANGE_RENAMED_TO`|Fichier renommé ou déplacé `lpLatestName`dans la base de données comme .|
|`SCC_CHANGE_RENAMED_FROM`|Fichier renommé ou déplacé `lpLatestName`dans la base de données à partir de ; si c’est trop cher à suivre, `SCC_CHANGE_DATABASE_ADDED`retourner un drapeau différent, comme .|

 lpLatestName Le nom de fichier actuel pour cet article.

## <a name="see-also"></a>Voir aussi
- [Fonctions de rappel mises en œuvre par l’IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccQueryChanges](../extensibility/sccquerychanges-function.md)
- [Codes d’erreur](../extensibility/error-codes.md)
