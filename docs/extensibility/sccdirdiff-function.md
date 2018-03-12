---
title: Fonction de SccDirDiff | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccDirDiff
helpviewer_keywords:
- SccDirDiff function
ms.assetid: 26c9ba92-e3b9-4dd2-bd5e-76b17745e308
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: c1f6f990bb33ddbc1d7591fa3ab9837f472f8418
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="sccdirdiff-function"></a>SccDirDiff (fonction)
Cette fonction affiche les différences entre le répertoire local actuel sur le disque du client et le projet correspondant sous contrôle de code source.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
SCCRTN SccDirDiff(  
   LPVOID    pContext,  
   HWND      hWnd,  
   LPCSTR    lpDirName,  
   LONG      dwFlags,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pContext  
 [in] La structure de contexte plug-in de contrôle de code source.  
  
 hWnd  
 [in] Handle vers la fenêtre de l’IDE que le plug-in de contrôle de code source peut utiliser en tant que parent pour toutes les boîtes de dialogue qu’il fournit.  
  
 lpDirName  
 [in] Chemin d’accès complet vers le répertoire local pour lesquels vous voulez afficher une différence visual.  
  
 dwFlags  
 [in] Indicateurs de commandes (consultez la section Notes section).  
  
 pvOptions  
 [in] Options spécifiques au plug-in du contrôle source.  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_OK|Le répertoire sur le disque est le même que le projet de contrôle de code source.|  
|SCC_I_FILESDIFFER|Le répertoire sur le disque est différent du projet dans le contrôle de code source.|  
|SCC_I_RELOADFILE|Un fichier ou un projet doit être rechargé.|  
|SCC_E_FILENOTCONTROLLED|Le répertoire n’est pas sous contrôle de code source.|  
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer cette opération.|  
|SCC_E_ACCESSFAILURE|Impossible d’accéder au système de contrôle source, probablement en raison de problèmes réseau ou de contention. Une nouvelle tentative est recommandée.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Erreur non spécifique.|  
|SCC_E_FILENOTEXIST|Répertoire local est introuvable.|  
  
## <a name="remarks"></a>Notes  
 Cette fonction est utilisée pour demander le contrôle de source de plug-in pour afficher la liste des modifications apportées à un répertoire spécifié à l’utilisateur. Le plug-in s’ouvre sa propre fenêtre, dans un format de son choix, pour afficher les différences entre le répertoire de l’utilisateur sur le disque et le projet correspondant sous contrôle de version.  
  
 Si une comparaison prend en charge de plug-in de répertoires du tout, il doit prendre en charge la comparaison des répertoires selon le nom de fichier même si les options « rapide-diff » ne sont pas pris en charge.  
  
|`dwFlags`|Interprétation|  
|---------------|--------------------|  
|SCC_DIFF_IGNORECASE|Comparaison respectant la casse (peut être utilisé pour une comparaison rapide ou visuel).|  
|SCC_DIFF_IGNORESPACE|Ignore l’espace blanc (peut être utilisé pour rapide-diff ou visuel).|  
|SCC_DIFF_QD_CONTENTS|Si la prise en charge par le plug-in de contrôle de code source, en mode silencieux compare le répertoire, octet par octet.|  
|SCC_DIFF_QD_CHECKSUM|Si pris en charge par le plug-in, en mode silencieux compare l’annuaire via une somme de contrôle ou, si non pris en charge, revient à SCC_DIFF_QD_CONTENTS.|  
|SCC_DIFF_QD_TIME|Si pris en charge par le plug-in, en mode silencieux compare l’annuaire via son horodatage ou, si non pris en charge, se replie sur SCC_DIFF_QD_CHECKSUM ou SCC_DIFF_QD_CONTENTS.|  
  
> [!NOTE]
>  Cette fonction utilise les mêmes indicateurs de commande en tant que le [SccDiff](../extensibility/sccdiff-function.md). Toutefois, un plug-in de contrôle de code source peut choisir de ne prend ne pas en charge l’opération « rapide-diff » pour les répertoires.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)