---
title: Fonction de SccUncheckout | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccUncheckout
helpviewer_keywords: SccUncheckout function
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1e210f239c543da84a1e80833f03b684099155ef
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="sccuncheckout-function"></a>SccUncheckout (fonction)
Cette fonction annule une opération d’extraction précédente, restaurant ainsi le contenu de l’ou les fichiers sélectionnés à l’état précédant l’extraction. Toutes les modifications apportées au fichier depuis l’extraction sont perdues.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
SCCRTN SccUncheckout (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pvContext  
 [in] La structure de contexte plug-in de contrôle de code source.  
  
 hWnd  
 [in] Handle vers la fenêtre de l’IDE que le plug-in de contrôle de code source peut utiliser en tant que parent pour toutes les boîtes de dialogue qu’il fournit.  
  
 nFiles  
 [in] Nombre de fichiers spécifiés dans le `lpFileNames` tableau.  
  
 lpFileNames  
 [in] Tableau des noms de chemin qualifié complet de fichiers pour lequel annuler une extraction.  
  
 fOptions  
 [in] Indicateurs de commande (non utilisés).  
  
 pvOptions  
 [in] Options spécifiques au plug-in du contrôle source.  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :  
  
|Valeur|Description|  
|-----------|-----------------|  
|SCC_OK|Annuler l’extraction a réussi.|  
|SCC_E_FILENOTCONTROLLED|Le fichier sélectionné n’est pas sous contrôle de code source.|  
|SCC_E_ACCESSFAILURE|Impossible d’accéder au système de contrôle source, probablement en raison de problèmes réseau ou de contention. Une nouvelle tentative est recommandée.|  
|SCC_E_NONSPECIFICERROR|Erreur non spécifique. Annuler l’extraction n’a pas réussi.|  
|SCC_E_NOTCHECKEDOUT|L’utilisateur n’a pas extrait le fichier.|  
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer cette opération.|  
|SCC_E_PROJNOTOPEN|Le projet n’a pas été ouvert à partir du contrôle de code source.|  
|SCC_I_OPERATIONCANCELED|L’opération a été annulée avant la fin.|  
  
## <a name="remarks"></a>Remarques  
 Après cette opération, le `SCC_STATUS_CHECKEDOUT` et `SCC_STATUS_MODIFIED` indicateurs seront désactivées pour les fichiers sur lequel l’extraction a été effectuée.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)