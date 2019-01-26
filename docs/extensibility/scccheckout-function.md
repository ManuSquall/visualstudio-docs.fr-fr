---
title: Fonction SccCheckout | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCheckout
helpviewer_keywords:
- SccCheckout function
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2a01ee4e4010782570d267d5b2e35d56fedb45a1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54984975"
---
# <a name="scccheckout-function"></a>Fonction SccCheckout
Étant donné une liste de noms de fichier complet, cette fonction extrait les sur le lecteur local. Le commentaire s’applique à tous les fichiers extraits. L’argument de commentaire peut être un `null` chaîne.  
  
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
  
### <a name="parameters"></a>Paramètres  
 pvContext  
 [in] La structure de contexte de plug-in de contrôle de source.  
  
 hWnd  
 [in] Handle vers la fenêtre de l’IDE que le plug-in de contrôle de code source peut utiliser en tant que parent pour les boîtes de dialogue qu’il fournit.  
  
 nFiles  
 [in] Nombre de fichiers sélectionnés à extraire.  
  
 lpFileNames  
 [in] Tableau des noms de chemin d’accès local complet des fichiers à extraire.  
  
 lpComment  
 [in] Commentaire à appliquer à chacun des fichiers sélectionnés en cours d’extraction.  
  
 fOptions  
 [in] Indicateurs de commande (voir [indicateurs de bits utilisés par des commandes spécifiques](../extensibility/bitflags-used-by-specific-commands.md)).  
  
 pvOptions  
 [in] Options spécifiques au plug-in de contrôle source.  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_OK|Extraction a réussi.|  
|SCC_E_FILENOTCONTROLLED|Le fichier sélectionné n’est pas sous contrôle de code source.|  
|SCC_E_ACCESSFAILURE|Impossible d’accéder au système de contrôle source, probablement en raison de problèmes réseau ou de contention. Une nouvelle tentative est recommandée.|  
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer cette opération.|  
|SCC_E_NONSPECIFICERROR|Erreur non spécifique. Le fichier n’a pas été extrait.|  
|SCC_E_ALREADYCHECKEDOUT|L’utilisateur a déjà extrait le fichier.|  
|SCC_E_FILEISLOCKED|Le fichier est verrouillé, ce qui interdit la création de nouvelles versions.|  
|SCC_E_FILEOUTEXCLUSIVE|Un autre utilisateur a effectué une extraction exclusive sur ce fichier.|  
|SCC_I_OPERATIONCANCELED|L’opération a été annulée avant la fin.|  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API source contrôle plug-in](../extensibility/source-control-plug-in-api-functions.md)   
 [Indicateurs de bits utilisés par des commandes spécifiques](../extensibility/bitflags-used-by-specific-commands.md)