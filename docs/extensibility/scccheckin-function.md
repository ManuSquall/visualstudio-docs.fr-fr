---
title: Fonction de SccCheckin | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccCheckin
helpviewer_keywords:
- SccCheckin function
ms.assetid: e3f26ac2-6163-42e1-a764-22cfea5a3bc6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bf8c8d23a89e55b272657dde0c2374c78e63bfaf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138852"
---
# <a name="scccheckin-function"></a>SccCheckin (fonction)
Cette fonction vérifie dans les fichiers extraits précédemment pour le système de contrôle de code source, stocke les modifications et la création d’une nouvelle version. Cette fonction est appelée avec un nombre et un tableau de noms de fichiers à archiver.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
 [in] La structure de contexte plug-in de contrôle de code source.  
  
 hWnd  
 [in] Un handle de fenêtre IDE qui permet l’analyse de plug-in en tant que parent pour toutes les boîtes de dialogue qu’il fournit.  
  
 nFiles  
 [in] Nombre de fichiers sélectionnés à être archivé.  
  
 lpFileNames  
 [in] Tableau des noms de chemin qualifié complet des fichiers à archiver.  
  
 lpComment  
 [in] Commentaire à appliquer à chaque fichier sélectionné en cours d’archivage. Il s’agit de `NULL` si le plug-in de contrôle de code source doit inviter à entrer un commentaire.  
  
 fOptions  
 [in] Indicateurs de commande, soit 0 ou `SCC_KEEP_CHECKEDOUT`.  
  
 pvOptions  
 [in] Options spécifiques au plug-in de contrôle de code source.  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_OK|Fichiers a réussi.|  
|SCC_E_FILENOTCONTROLLED|Le fichier sélectionné n’est pas sous contrôle de code source.|  
|SCC_E_ACCESSFAILURE|Impossible d’accéder au système de contrôle source, probablement en raison de problèmes réseau ou de contention. Une nouvelle tentative est recommandée.|  
|SCC_E_NONSPECIFICERROR|Erreur non spécifique. Fichier n’a pas été activé.|  
|SCC_E_NOTCHECKEDOUT|L’utilisateur n’a pas extrait le fichier ne peut pas archiver.|  
|SCC_E_CHECKINCONFLICT|Archivage n’a pas pu être effectuée car :<br /><br /> -Un autre utilisateur a archivé avance et `bAutoReconcile` a la valeur false.<br /><br /> - ou -<br /><br /> -La fusion automatique ne peut pas être effectuée (par exemple, lorsque les fichiers sont binaires).|  
|SCC_E_VERIFYMERGE|Fichier a été fusionnée automatiquement, mais n’a pas été vérifiée en attente de vérification de l’utilisateur.|  
|SCC_E_FIXMERGE|Fichier a été fusionnée automatiquement, mais n’a pas été archivé en raison d’un conflit de fusion qui doit être résolu manuellement.|  
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer cette opération.|  
|SCC_I_OPERATIONCANCELED|Opération a été annulée avant la fin.|  
|SCC_I_RELOADFILE|Un fichier ou un projet doit être rechargé.|  
|SCC_E_FILENOTEXIST|Impossible de trouver le fichier local.|  
  
## <a name="remarks"></a>Notes  
 Le commentaire s’applique à tous les fichiers en cours d’archivage. L’argument de commentaire peut être un `null` de chaîne, auquel cas le plug-in de contrôle de code source peut demander à l’utilisateur pour une chaîne de commentaire pour chaque fichier.  
  
 Le `fOptions` argument peut être donné à une valeur de la `SCC_KEEP_CHECKEDOUT` indicateur pour indiquer l’intention de l’utilisateur à archiver le fichier et l’extraire à nouveau.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)