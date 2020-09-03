---
title: SccAddFilesFromSCC fonction) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccAddFilesFromSCC
helpviewer_keywords:
- SccAddFilesFromSCC function
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d5af748c9180644cae928d1b6db3a3f880b6b286
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200911"
---
# <a name="sccaddfilesfromscc-function"></a>Fonction SccAddFilesFromSCC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette fonction ajoute une liste de fichiers du contrôle de code source au projet actuellement ouvert.  
  
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
 dans Pointeur de contexte du plug-in de contrôle de code source.  
  
 hWnd  
 dans Handle de la fenêtre IDE que le plug-in de contrôle de code source peut utiliser comme parent pour toutes les boîtes de dialogue qu’il fournit.  
  
 lpUser  
 [in, out] Nom d’utilisateur (jusqu’à SCC_USER_SIZE, y compris la marque de fin null).  
  
 lpAuxProjPath  
 [in, out] Chaîne auxiliaire identifiant le projet ( `SCC_PRJPATH_` taille maximale, y compris la marque de fin null).  
  
 cFiles  
 dans Nombre de fichiers spécifiés par `lpFilePaths` .  
  
 lpFilePaths  
 [in, out] Tableau de noms de fichiers à ajouter au projet en cours.  
  
 lpDestination  
 dans Chemin d’accès de destination où les fichiers doivent être écrits.  
  
 lpComment  
 dans Commentaire à appliquer à chacun des fichiers ajoutés.  
  
 pbResults  
 [in, out] Tableau d’indicateurs qui sont définis pour indiquer la réussite (valeur différente de zéro ou TRUE) ou l’échec (zéro ou FALSe) pour chaque fichier (la taille du tableau doit être au moins `cFiles` longue).  
  
## <a name="return-value"></a>Valeur renvoyée  
 L’implémentation du plug-in de contrôle de code source de cette fonction est supposée retourner l’une des valeurs suivantes :  
  
|Valeur|Description|  
|-----------|-----------------|  
|SCC_E_PROJNOTOPEN|Le projet n’est pas ouvert.|  
|SCC_E_OPNOTPERFORMED|La connexion n’est pas vers le même projet que celui spécifié par `lpAuxProjPath.`|  
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à mettre à jour la base de données.|  
|SCC_E_NONSPECIFICERROR|Erreur inconnue.|  
|SCC_I_RELOADFILE|Un fichier ou un projet doit être rechargé.|  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
