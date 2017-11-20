---
title: Fonction de SccAddFilesFromSCC | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccAddFilesFromSCC
helpviewer_keywords: SccAddFilesFromSCC function
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1764bfc503e25860326b1910c432edcf95c8f21c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="sccaddfilesfromscc-function"></a>SccAddFilesFromSCC (fonction)
Cette fonction ajoute une liste de fichiers à partir du contrôle de code source pour le projet actuellement ouvert.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
SCCRTN SccAddFilesFromSCC(  
   LPVOID  pContext,  
   HWND    hWnd,  
   LPSTR   lpUser,  
   LPSTR   lpAuxProjPath,  
   LONG    cFiles,  
   LPCSTR* lpFilePaths,  
   LPCSTR  lpDestination,  
   LPCSTR  lpComment,  
   LPBOOL  pbResults  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pContext  
 [in] Le pointeur de contexte plug-in de contrôle de code source.  
  
 hWnd  
 [in] Handle vers la fenêtre de l’IDE que le plug-in de contrôle de code source peut utiliser en tant que parent pour toutes les boîtes de dialogue qu’il fournit.  
  
 lpUser  
 [dans, out] Le nom d’utilisateur (jusqu'à SCC_USER_SIZE, y compris la marque de fin null).  
  
 lpAuxProjPath  
 [dans, out] Auxiliaire chaîne identifiant le projet (jusqu'à `SCC_PRJPATH_`taille, y compris la marque de fin null).  
  
 cFiles  
 [in] Nombre de fichiers donné par `lpFilePaths`.  
  
 lpFilePaths  
 [dans, out] Tableau des noms de fichiers à ajouter au projet actuel.  
  
 lpDestination  
 [in] Le chemin d’accès de destination où les fichiers doivent être écrites.  
  
 lpComment  
 [in] Le commentaire à appliquer à chacun des fichiers à ajouter.  
  
 pbResults  
 [dans, out] Tableau d’indicateurs ensemble pour indiquer une réussite (différente de zéro ou TRUE) ou l’échec (zéro ou FALSE) pour chaque fichier (taille du tableau doit contenir au moins `cFiles` long).  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :  
  
|Valeur|Description|  
|-----------|-----------------|  
|SCC_E_PROJNOTOPEN|Projet n’est pas ouvert.|  
|SCC_E_OPNOTPERFORMED|La connexion n’est pas le même projet, tel que spécifié par`lpAuxProjPath.`|  
|SCC_E_NOTAUTHORIZED|Utilisateur n’est pas autorisé à mettre à jour la base de données.|  
|SCC_E_NONSPECIFICERROR|Erreur inconnue.|  
|SCC_I_RELOADFILE|Un fichier ou un projet doit être rechargé.|  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)