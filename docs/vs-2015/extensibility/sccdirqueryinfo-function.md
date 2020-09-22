---
title: SccDirQueryInfo fonction) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccDirQueryInfo
helpviewer_keywords:
- SccDirQueryInfo function
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7334ddd1ce6c7f9feac63253246e55b65121e18b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839286"
---
# <a name="sccdirqueryinfo-function"></a>Fonction SccDirQueryInfo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette fonction examine une liste de répertoires complets pour leur état actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
SCCRTN SccDirQueryInfo(  
LPVOID  pContext,  
LONG    nDirs,  
LPCSTR* lpDirNames,  
LPLONG  lpStatus  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pContext  
 dans Structure de contexte du plug-in de contrôle de code source.  
  
 nDirs  
 dans Nombre de répertoires sélectionnés à interroger.  
  
 lpDirNames  
 dans Tableau de chemins d’accès qualifiés complets des répertoires à interroger.  
  
 lpStatus  
 [in, out] Structure de tableau pour que le plug-in de contrôle de code source retourne les indicateurs d’État (pour plus d’informations, consultez le [code d’État du répertoire](../extensibility/directory-status-code-enumerator.md) ).  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation du plug-in de contrôle de code source de cette fonction est supposée retourner l’une des valeurs suivantes :  
  
|Valeur|Description|  
|-----------|-----------------|  
|SCC_OK|La requête a réussi.|  
|SCC_E_OPNOTSUPPORTED|Le système de contrôle de code source ne prend pas en charge cette opération.|  
|SCC_E_ACCESSFAILURE|Un problème est survenu lors de l’accès au système de contrôle de code source, probablement en raison de problèmes de réseau ou de contention. Une nouvelle tentative est recommandée.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Échec non spécifique.|  
  
## <a name="remarks"></a>Remarques  
 La fonction remplit le tableau de retour avec un masque de bits de la `SCC_DIRSTATUS` famille (voir [code d’État du répertoire](../extensibility/directory-status-code-enumerator.md)), une entrée pour chaque répertoire donné. Le tableau d’État est alloué par l’appelant.  
  
 L’IDE utilise cette fonction avant qu’un répertoire ne soit renommé afin de vérifier si le répertoire est sous contrôle de code source en interrogeant s’il possède un projet correspondant. Si le répertoire n’est pas sous contrôle de code source, l’IDE peut fournir l’avertissement approprié à l’utilisateur.  
  
> [!NOTE]
> Si un plug-in de contrôle de code source choisit de ne pas implémenter une ou plusieurs des valeurs d’État, les bits non implémentés doivent avoir la valeur zéro.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de l’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)   
 [Code d’état de répertoire](../extensibility/directory-status-code-enumerator.md)
