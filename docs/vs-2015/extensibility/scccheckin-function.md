---
title: SccCheckin fonction) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccCheckin
helpviewer_keywords:
- SccCheckin function
ms.assetid: e3f26ac2-6163-42e1-a764-22cfea5a3bc6
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d8a5a91a0300f256b66970403a3431edf0fe757e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189534"
---
# <a name="scccheckin-function"></a>Fonction SccCheckin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette fonction Archive les fichiers précédemment extraits dans le système de contrôle de code source, en stockant les modifications et en créant une nouvelle version. Cette fonction est appelée avec un nombre et un tableau de noms des fichiers à archiver.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
SCCRTN SccCheckin (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPSTR*    lpFileNames,  
   LPCSTR    lpComment,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pvContext  
 dans Structure de contexte du plug-in de contrôle de code source.  
  
 hWnd  
 dans Handle de la fenêtre IDE que le plug-in SCC peut utiliser comme parent pour toutes les boîtes de dialogue qu’il fournit.  
  
 Nfichiers  
 dans Nombre de fichiers sélectionnés pour l’archivage.  
  
 lpFileNames  
 dans Tableau de noms de chemins d’accès locaux complets des fichiers à archiver.  
  
 lpComment  
 dans Commentaire à appliquer à chacun des fichiers sélectionnés en cours d’archivage. C’est `NULL` le cas si le plug-in de contrôle de code source doit demander un commentaire.  
  
 fOptions  
 dans Indicateurs de commande, 0 ou `SCC_KEEP_CHECKEDOUT` .  
  
 pvOptions  
 dans Options spécifiques au plug-in SCC.  
  
## <a name="return-value"></a>Valeur renvoyée  
 L’implémentation du plug-in de contrôle de code source de cette fonction est supposée retourner l’une des valeurs suivantes :  
  
|Valeur|Description|  
|-----------|-----------------|  
|SCC_OK|Les fichiers ont été archivés avec succès.|  
|SCC_E_FILENOTCONTROLLED|Le fichier sélectionné n’est pas sous le contrôle de code source.|  
|SCC_E_ACCESSFAILURE|Un problème est survenu lors de l’accès au système de contrôle de code source, probablement en raison de problèmes de réseau ou de contention. Une nouvelle tentative est recommandée.|  
|SCC_E_NONSPECIFICERROR|Échec non spécifique. Le fichier n’a pas été archivé.|  
|SCC_E_NOTCHECKEDOUT|L’utilisateur n’a pas extrait le fichier et ne peut donc pas l’archiver.|  
|SCC_E_CHECKINCONFLICT|L’archivage n’a pas pu être effectué, car :<br /><br /> -Un autre utilisateur a été vérifié et `bAutoReconcile` a été faux.<br /><br /> - ou -<br /><br /> -La fusion automatique ne peut pas être effectuée (par exemple, lorsque les fichiers sont binaires).|  
|SCC_E_VERIFYMERGE|Le fichier a été fusionné automatiquement mais n’a pas été vérifié dans la vérification de l’utilisateur en attente.|  
|SCC_E_FIXMERGE|Le fichier a été fusionné automatiquement mais n’a pas été archivé en raison d’un conflit de fusion qui doit être résolu manuellement.|  
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer cette opération.|  
|SCC_I_OPERATIONCANCELED|L’opération a été annulée avant la fin.|  
|SCC_I_RELOADFILE|Un fichier ou un projet doit être rechargé.|  
|SCC_E_FILENOTEXIST|Fichier local introuvable.|  
  
## <a name="remarks"></a>Notes  
 Le commentaire s’applique à tous les fichiers en cours d’archivage. L’argument de commentaire peut être une `null` chaîne, auquel cas le plug-in de contrôle de code source peut inviter l’utilisateur à entrer une chaîne de commentaire pour chaque fichier.  
  
 L' `fOptions` argument peut recevoir une valeur de l' `SCC_KEEP_CHECKEDOUT` indicateur pour indiquer l’intention de l’utilisateur de vérifier le fichier et de le récupérer.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
