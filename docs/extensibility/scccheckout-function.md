---
title: Fonction de SccCheckout | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccCheckout
helpviewer_keywords:
- SccCheckout function
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 671e4ecebb44f0910eba3bb835a6da6f9a7f3903
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="scccheckout-function"></a>SccCheckout (fonction)
Étant donné une liste de noms de fichier qualifié complet, cette fonction extrait les sur le lecteur local. Le commentaire s’applique à tous les fichiers extraits. L’argument de commentaire peut être un `null` chaîne.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
SCCRTN SccCheckout (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LPCSTR    lpComment,  
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
 [in] Nombre de fichiers sélectionnés pour être récupéré.  
  
 lpFileNames  
 [in] Tableau des noms de chemin qualifié complet des fichiers à extraire.  
  
 lpComment  
 [in] Commentaire à appliquer à chaque fichier sélectionné en cours d’extraction.  
  
 fOptions  
 [in] Indicateurs de commande (voir [indicateurs de bits utilisés par des commandes spécifiques](../extensibility/bitflags-used-by-specific-commands.md)).  
  
 pvOptions  
 [in] Options spécifiques au plug-in du contrôle source.  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_OK|Extraction réussie.|  
|SCC_E_FILENOTCONTROLLED|Le fichier sélectionné n’est pas sous contrôle de code source.|  
|SCC_E_ACCESSFAILURE|Impossible d’accéder au système de contrôle source, probablement en raison de problèmes réseau ou de contention. Une nouvelle tentative est recommandée.|  
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer cette opération.|  
|SCC_E_NONSPECIFICERROR|Erreur non spécifique. Le fichier n’a pas été extrait.|  
|SCC_E_ALREADYCHECKEDOUT|L’utilisateur a déjà extrait le fichier.|  
|SCC_E_FILEISLOCKED|Le fichier est verrouillé, ce qui empêche la création de nouvelles versions.|  
|SCC_E_FILEOUTEXCLUSIVE|Un autre utilisateur a effectué une extraction exclusive sur ce fichier.|  
|SCC_I_OPERATIONCANCELED|L’opération a été annulée avant la fin.|  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API de plug-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [Indicateurs de bits utilisés par des commandes spécifiques](../extensibility/bitflags-used-by-specific-commands.md)