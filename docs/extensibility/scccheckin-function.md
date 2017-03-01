---
title: Fonction de SccCheckin | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccCheckin
helpviewer_keywords:
- SccCheckin function
ms.assetid: e3f26ac2-6163-42e1-a764-22cfea5a3bc6
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: e8bfa87246bc866a251951e4700b796d833dd63f
ms.lasthandoff: 02/22/2017

---
# <a name="scccheckin-function"></a>SccCheckin (fonction)
Cette fonction vérifie dans les fichiers extraits précédemment vers le système de contrôle source, stocke les modifications et la création d’une nouvelle version. Cette fonction est appelée avec un nombre et un tableau de noms de fichiers à archiver.  
  
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
 [in] La structure de contexte du plug-in de contrôle de source.  
  
 hWnd  
 [in] Handle vers la fenêtre de l’IDE SCC plug-in peut utiliser comme parent pour toutes les boîtes de dialogue qu’il fournit.  
  
 nFiles  
 [in] Nombre de fichiers sélectionnés pour être archivé.  
  
 lpFileNames  
 [in] Tableau des noms de chemin d’accès local complet des fichiers à archiver.  
  
 lpComment  
 [in] Commentaire à appliquer à chaque fichier sélectionné en cours d’archivage. Il s’agit de `NULL` si le plug-in de contrôle de code source doit demander un commentaire.  
  
 Options  
 [in] Indicateurs de commande, soit 0 ou `SCC_KEEP_CHECKEDOUT`.  
  
 pvOptions  
 [in] Options spécifiques au plug-in de contrôle de code source.  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée renvoyer une des valeurs suivantes :  
  
|Valeur|Description|  
|-----------|-----------------|  
|SCC_OK|Fichiers a réussi.|  
|SCC_E_FILENOTCONTROLLED|Le fichier sélectionné n’est pas sous contrôle de code source.|  
|SCC_E_ACCESSFAILURE|Impossible d’accéder au système de contrôle source, probablement en raison de problèmes réseau ou de contention. Une nouvelle tentative est recommandée.|  
|SCC_E_NONSPECIFICERROR|Erreur non spécifique. Fichier n’a pas été activé.|  
|SCC_E_NOTCHECKEDOUT|L’utilisateur n’a pas extrait le fichier ne peut pas archiver.|  
|SCC_E_CHECKINCONFLICT|Archivage n’a pas pu être effectuée car :<br /><br /> -Un autre utilisateur a archivé à l’avance et `bAutoReconcile` a la valeur false.<br /><br /> ou<br /><br /> -La fusion automatique ne peut pas être effectuée (par exemple, lorsque les fichiers sont binaires).|  
|SCC_E_VERIFYMERGE|Fichier a été fusionnée automatiquement, mais n’a pas été vérifiée en attente de vérification de l’utilisateur.|  
|SCC_E_FIXMERGE|Fichier a été fusionnée automatiquement, mais n’a pas été archivé en raison d’un conflit de fusion qui doit être résolu manuellement.|  
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer cette opération.|  
|SCC_I_OPERATIONCANCELED|Opération a été annulée avant la fin.|  
|SCC_I_RELOADFILE|Un fichier ou un projet doit être rechargé.|  
|SCC_E_FILENOTEXIST|Impossible de trouver le fichier local.|  
  
## <a name="remarks"></a>Remarques  
 Le commentaire s’applique à tous les fichiers en cours d’archivage. L’argument de commentaire peut être un `null` de chaîne, auquel cas le plug-in de contrôle de code source peut inviter l’utilisateur pour une chaîne de commentaire pour chaque fichier.  
  
 Le `fOptions` argument peut attribuer une valeur de la `SCC_KEEP_CHECKEDOUT` l’indicateur pour indiquer l’intention de l’utilisateur à archiver le fichier et l’extraire à nouveau.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API de plug-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)
