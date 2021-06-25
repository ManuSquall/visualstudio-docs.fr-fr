---
title: QUERYCHANGESFUNC | Microsoft Docs
description: La fonction de rappel QUERYCHANGESFUNC est utilisée pour énumérer une collection de noms de fichiers et déterminer l’état de chaque fichier.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- QUERYCHANGESFUNC
helpviewer_keywords:
- QUERYCHANGESFUNC callback function
- QUERYCHANGESDATA structure
ms.assetid: 9d383e2c-eee1-4996-973a-0652d4c5951c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b061fbfb6644f77348574020c0a5cb614691ae6b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899132"
---
# <a name="querychangesfunc"></a>QUERYCHANGESFUNC
Il s’agit d’une fonction de rappel utilisée par l’opération [SccQueryChanges](../extensibility/sccquerychanges-function.md) pour énumérer une collection de noms de fichiers et déterminer l’état de chaque fichier.

 La `SccQueryChanges` fonction reçoit une liste de fichiers et un pointeur vers le `QUERYCHANGESFUNC` rappel. Le plug-in de contrôle de code source énumère la liste donnée et fournit l’État (par le biais de ce rappel) pour chaque fichier de la liste.

## <a name="signature"></a>Signature

```cpp
typedef BOOL (*QUERYCHANGESFUNC)(
   LPVOID pvCallerData,
   QUERYCHANGESDATA * pChangesData
);
```

## <a name="parameters"></a>Paramètres
 pvCallerData

dans `pvCallerData` Paramètre passé par l’appelant (l’IDE) à [SccQueryChanges](../extensibility/sccquerychanges-function.md). Le plug-in de contrôle de code source ne doit pas faire d’hypothèses concernant le contenu de cette valeur.

 pChangesData

dans Pointeur vers une structure de [structure QUERYCHANGESDATA](#LinkQUERYCHANGESDATA) décrivant les modifications apportées à un fichier.

## <a name="return-value"></a>Valeur retournée
 L’IDE retourne un code d’erreur approprié :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|Continuer le traitement.|
|SCC_I_OPERATIONCANCELED|Arrêter le traitement.|
|SCC_E_xxx|Toute erreur SCC appropriée doit arrêter le traitement.|

## <a name="querychangesdata-structure"></a><a name="LinkQUERYCHANGESDATA"></a> QUERYCHANGESDATA, structure
 La structure transmise pour chaque fichier ressemble à ce qui suit :

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

 dwSize nul taille de cette structure (en octets).

 lpFileName le nom de fichier d’origine pour cet élément.

 Code dwChangeType indiquant l’état du fichier :

|Code|Description|
|----------|-----------------|
|`SCC_CHANGE_UNKNOWN`|Impossible d’indiquer ce qui a changé.|
|`SCC_CHANGE_UNCHANGED`|Aucune modification de nom pour ce fichier.|
|`SCC_CHANGE_DIFFERENT`|Fichier avec une identité différente, mais le même nom existe dans la base de données.|
|`SCC_CHANGE_NONEXISTENT`|Le fichier n’existe pas dans la base de données ou localement.|
|`SCC_CHANGE_DATABASE_DELETED`|Fichier supprimé dans la base de données.|
|`SCC_CHANGE_LOCAL_DELETED`|Fichier supprimé localement, mais le fichier existe toujours dans la base de données. Si cela ne peut pas être déterminé, retournez `SCC_CHANGE_DATABASE_ADDED` .|
|`SCC_CHANGE_DATABASE_ADDED`|Le fichier a été ajouté à la base de données mais n’existe pas localement.|
|`SCC_CHANGE_LOCAL_ADDED`|Le fichier n’existe pas dans la base de données et est un nouveau fichier local.|
|`SCC_CHANGE_RENAMED_TO`|Fichier renommé ou déplacé dans la base de données en tant que `lpLatestName` .|
|`SCC_CHANGE_RENAMED_FROM`|Fichier renommé ou déplacé dans la base de données à partir de `lpLatestName` ; si cela est trop coûteux pour le suivi, retournez un autre indicateur, tel que `SCC_CHANGE_DATABASE_ADDED` .|

 lpLatestName le nom de fichier actuel pour cet élément.

## <a name="see-also"></a>Voir aussi
- [Fonctions de rappel implémentées par l’IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccQueryChanges](../extensibility/sccquerychanges-function.md)
- [Codes d’erreur](../extensibility/error-codes.md)
