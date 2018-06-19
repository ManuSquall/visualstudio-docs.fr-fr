---
title: QUERYCHANGESFUNC | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- QUERYCHANGESFUNC
helpviewer_keywords:
- QUERYCHANGESFUNC callback function
- QUERYCHANGESDATA structure
ms.assetid: 9d383e2c-eee1-4996-973a-0652d4c5951c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d1df5f21ffed27c45ebee6315fcc29ee1dcc8fa4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31139807"
---
# <a name="querychangesfunc"></a>QUERYCHANGESFUNC
Il s’agit d’une fonction de rappel utilisée par le [SccQueryChanges](../extensibility/sccquerychanges-function.md) opération pour énumérer une collection de noms de fichiers et de déterminer l’état de chaque fichier.  
  
 Le `SccQueryChanges` fonction reçoit une liste de fichiers et un pointeur vers le `QUERYCHANGESFUNC` rappel. Le plug-in de contrôle de source énumère la liste donnée et fournit l’état (via ce rappel) pour chaque fichier dans la liste.  
  
## <a name="signature"></a>Signature  
  
```cpp  
typedef BOOL (*QUERYCHANGESFUNC)(  
   LPVOID pvCallerData,  
   QUERYCHANGESDATA * pChangesData  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 pvCallerData  
 [in] Le `pvCallerData` paramètre passé par l’appelant (l’IDE) pour [SccQueryChanges](../extensibility/sccquerychanges-function.md). Le plug-in de contrôle de code source doit-elle pas faire d’hypothèses sur le contenu de cette valeur.  
  
 pChangesData  
 [in] Pointeur vers un [QUERYCHANGESDATA Structure](#LinkQUERYCHANGESDATA) structure qui décrit les modifications apportées à un fichier.  
  
## <a name="return-value"></a>Valeur de retour  
 L’IDE retourne un code d’erreur approprié :  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_OK|Continuer le traitement.|  
|SCC_I_OPERATIONCANCELED|Arrêter le traitement.|  
|SCC_E_xxx|Une erreur de contrôle de code source appropriée doit arrêter le traitement.|  
  
##  <a name="LinkQUERYCHANGESDATA"></a> Structure QUERYCHANGESDATA  
 La structure passée dans chaque fichier ressemble à ceci :  
  
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
  
 dwSize  
 Taille de cette structure (en octets).  
  
 lpFileName  
 Le nom de fichier d’origine pour cet élément.  
  
 dwChangeType  
 Code indiquant l’état du fichier :  
  
|Code|Description|  
|----------|-----------------|  
|`SCC_CHANGE_UNKNOWN`|Impossible d’indiquer ce qui a changé.|  
|`SCC_CHANGE_UNCHANGED`|Aucune modification de nom pour ce fichier.|  
|`SCC_CHANGE_DIFFERENT`|Fichier avec une identité différente, mais le même nom existe dans la base de données.|  
|`SCC_CHANGE_NONEXISTENT`|Fichier n’existe pas dans la base de données ou localement.|  
|`SCC_CHANGE_DATABASE_DELETED`|Fichier a été supprimé dans la base de données.|  
|`SCC_CHANGE_LOCAL_DELETED`|Fichier supprimé localement, mais le fichier existe toujours dans la base de données. Si cela ne peut pas être déterminé, retourner `SCC_CHANGE_DATABASE_ADDED`.|  
|`SCC_CHANGE_DATABASE_ADDED`|Fichier ajouté à la base de données, mais n’existe pas localement.|  
|`SCC_CHANGE_LOCAL_ADDED`|Fichier n’existe pas dans la base de données et un nouveau fichier local.|  
|`SCC_CHANGE_RENAMED_TO`|Fichiers renommés ou déplacés dans la base de données en tant que `lpLatestName`.|  
|`SCC_CHANGE_RENAMED_FROM`|Fichiers renommés ou déplacés dans la base de données à partir de `lpLatestName`; si cela est trop coûteuse pour effectuer le suivi, retourne un indicateur différent, tel que `SCC_CHANGE_DATABASE_ADDED`.|  
  
 lpLatestName  
 Le nom de fichier actuel pour cet élément.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de rappel implémentées par l’IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)   
 [Codes d’erreur](../extensibility/error-codes.md)