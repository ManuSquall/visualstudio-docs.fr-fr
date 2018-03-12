---
title: Fonction de SccDirQueryInfo | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccDirQueryInfo
helpviewer_keywords:
- SccDirQueryInfo function
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: c7a930c0fcdffbc76bba431012d76dd6d13686d0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
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