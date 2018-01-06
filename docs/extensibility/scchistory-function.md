---
title: Fonction de SccHistory | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccHistory
helpviewer_keywords: SccHistory function
ms.assetid: a636d9d3-47c1-4b48-ac6b-bcfde19d6cf9
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: cf621b3050382d79fcf44df2ac5d50d9885e03d2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="scchistory-function"></a>SccHistory (fonction)
Cette fonction affiche l’historique des fichiers spécifiés.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
SCCRTN SccHistory(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pvContext`  
 [in] La structure de contexte plug-in de contrôle de code source.  
  
 `hWnd`  
 [in] Handle vers la fenêtre de l’IDE que le plug-in de contrôle de code source peut utiliser en tant que parent pour toutes les boîtes de dialogue qu’il fournit.  
  
 `nFiles`  
 [in] Nombre de fichiers spécifiés dans le `lpFileName` tableau.  
  
 `lpFileName`  
 [in] Tableau des noms complets des fichiers.  
  
 `fOptions`  
 [in] Indicateurs de commande (actuellement non utilisés).  
  
 `pvOptions`  
 [in] Options spécifiques au plug-in du contrôle source.  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_OK|Historique de version a été obtenue avec succès.|  
|SCC_I_RELOADFILE|Le système de contrôle de code source modifié réellement le fichier sur le disque lors de l’extraction de l’historique (par exemple, en l’obtention d’une ancienne version de celui-ci), afin de l’IDE doit recharger ce fichier.|  
|SCC_E_FILENOTCONTROLLED|Le fichier n’est pas sous contrôle de code source.|  
|SCC_E_OPNOTSUPPORTED|Le système de contrôle de code source ne prend pas en charge cette opération.|  
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer cette opération.|  
|SCC_E_ACCESSFAILURE|Impossible d’accéder au système de contrôle source, probablement en raison de problèmes réseau ou de contention. Une nouvelle tentative est recommandée.|  
|SCC_E_PROJNOTOPEN|Le projet n’a pas été ouvert.|  
|SCC_E_NONSPECIFICERROR|Erreur non spécifique. L’historique des fichiers n’a pas pu être obtenu.|  
  
## <a name="remarks"></a>Notes  
 Le plug-in de contrôle de code source peut afficher une boîte de dialogue pour afficher l’historique de chaque fichier, à l’aide de `hWnd` en tant que la fenêtre parente. Vous pouvez également le texte facultatif sortie rappel fonction fourni à la [SccOpenProject](../extensibility/sccopenproject-function.md) peut être utilisé, si elle est prise en charge.  
  
 Notez que dans certaines circonstances, le fichier en cours d’examen peut changer pendant l’exécution de cet appel. Par exemple, le [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] commande history permet de l’utilisateur pour obtenir une version ancienne du fichier. Dans ce cas, la contrôle de code source retourne plug-in `SCC_I_RELOAD` pour avertir l’IDE qu’il doit recharger le fichier.  
  
> [!NOTE]
>  Si le plug-in de contrôle de code source ne prend pas en charge cette fonction pour un tableau de fichiers, il est possible d’afficher uniquement l’historique des fichiers pour le premier fichier.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API de plug-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)