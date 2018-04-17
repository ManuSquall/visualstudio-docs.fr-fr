---
title: Fonction de SccDirQueryInfo | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccDirQueryInfo
helpviewer_keywords:
- SccDirQueryInfo function
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1de32b8502e40c953bd7080d64e56047e6bb5ce9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="sccdirqueryinfo-function"></a>SccDirQueryInfo (fonction)
Cette fonction examine une liste de répertoires complets pour leur état actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
SCCRTN SccDirQueryInfo(  
LPVOID  pContext,  
LONG    nDirs,  
LPCSTR* lpDirNames,  
LPLONG  lpStatus  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pContext  
 [in] La structure de contexte plug-in de contrôle de code source.  
  
 nDirs  
 [in] Le nombre de répertoires sélectionnés à interroger.  
  
 lpDirNames  
 [in] Un tableau des chemins d’accès complets des répertoires à interroger.  
  
 lpStatus  
 [dans, out] Une structure de tableau pour le plug-in pour retourner les indicateurs d’état de contrôle de code source (voir [Code d’état Active](../extensibility/directory-status-code-enumerator.md) pour plus d’informations).  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_OK|La requête a réussi.|  
|SCC_E_OPNOTSUPPORTED|Le système de contrôle de code source ne prend pas en charge cette opération.|  
|SCC_E_ACCESSFAILURE|Impossible d’accéder au système de contrôle source, probablement en raison de problèmes réseau ou de contention. Une nouvelle tentative est recommandée.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Erreur non spécifique.|  
  
## <a name="remarks"></a>Notes  
 La fonction remplit le tableau de résultats avec un masque de bits de bits à partir de la `SCC_DIRSTATUS` famille (consultez [Code d’état Active](../extensibility/directory-status-code-enumerator.md)), une entrée pour chaque répertoire donné. Le tableau de l’état est alloué par l’appelant.  
  
 L’IDE utilise cette fonction avant qu’un répertoire est renommé pour vérifier si le répertoire est sous contrôle de code source en interrogeant s’il dispose d’un projet correspondant. Si le répertoire n’est pas sous contrôle de code source, l’IDE peut fournir l’avertissement approprié à l’utilisateur.  
  
> [!NOTE]
>  Si un plug-in de contrôle de code source choisit ne pas implémenter une ou plusieurs valeurs d’état, non implémentées bits doivent être définis à zéro.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API de plug-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [Code d’état Active](../extensibility/directory-status-code-enumerator.md)