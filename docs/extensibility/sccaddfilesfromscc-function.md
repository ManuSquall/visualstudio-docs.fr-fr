---
title: Fonction SccAddFilesFromSCC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAddFilesFromSCC
helpviewer_keywords:
- SccAddFilesFromSCC function
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b650810ea0c3a7df32d6a058947d83fb8842b7f7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53818963"
---
# <a name="sccaddfilesfromscc-function"></a>Fonction SccAddFilesFromSCC
Cette fonction ajoute une liste de fichiers à partir du contrôle de code source au projet actuellement ouvert.  
  
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
  
### <a name="parameters"></a>Paramètres  
 pContext  
 [in] Le pointeur de contexte de plug-in de contrôle de code source.  
  
 hWnd  
 [in] Handle vers la fenêtre de l’IDE que le plug-in de contrôle de code source peut utiliser en tant que parent pour les boîtes de dialogue qu’il fournit.  
  
 lpUser  
 [in, out] Le nom d’utilisateur (jusqu'à SCC_USER_SIZE, y compris le terminateur null).  
  
 lpAuxProjPath  
 [in, out] Auxiliaire chaîne identifiant le projet (jusqu'à `SCC_PRJPATH_`taille, y compris le terminateur null).  
  
 cFiles  
 [in] Nombre de fichiers donné par `lpFilePaths`.  
  
 lpFilePaths  
 [in, out] Tableau de noms de fichiers à ajouter au projet actuel.  
  
 lpDestination  
 [in] Le chemin d’accès de destination où les fichiers doivent être écrites.  
  
 lpComment  
 [in] Le commentaire à appliquer à chacun des fichiers en cours d’ajout.  
  
 pbResults  
 [in, out] Tableau d’indicateurs qui sont le jeu pour indiquer la réussite (différente de zéro ou TRUE) ou l’échec (zéro ou FALSE) pour chaque fichier (taille du tableau doit être au moins `cFiles` long).  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_E_PROJNOTOPEN|Projet n’est pas ouvert.|  
|SCC_E_OPNOTPERFORMED|Connexion n’est pas le même projet, tel que spécifié par `lpAuxProjPath.`|  
|SCC_E_NOTAUTHORIZED|Utilisateur n’est pas autorisé à mettre à jour de la base de données.|  
|SCC_E_NONSPECIFICERROR|Erreur inconnue.|  
|SCC_I_RELOADFILE|Un fichier ou un projet doit être rechargé.|  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API source contrôle plug-in](../extensibility/source-control-plug-in-api-functions.md)