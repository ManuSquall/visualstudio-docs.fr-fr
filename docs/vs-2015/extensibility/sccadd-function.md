---
title: Fonction SccAdd | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccAdd
helpviewer_keywords:
- SccAdd function
ms.assetid: 545268f3-8e83-446a-a398-1a9db9e866e8
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7d0ac6ba5ef5e4950030d80efb030742a121e876
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49879009"
---
# <a name="sccadd-function"></a>Fonction SccAdd
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette fonction ajoute de nouveaux fichiers au système de contrôle source.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
SCCRTN SccAdd(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LPCSTR    lpComment,  
   LONG*     pfOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pvContext  
 [in] La structure de contexte de plug-in de contrôle de source.  
  
 hWnd  
 [in] Handle vers la fenêtre de l’IDE que le plug-in de contrôle de code source peut utiliser en tant que parent pour les boîtes de dialogue qu’il fournit.  
  
 nFiles  
 [in] Nombre de fichiers sélectionnés à ajouter au projet actuel en tant que donnée dans le `lpFileNames` tableau.  
  
 lpFileNames  
 [in] Tableau de noms locales qualifiés complets de fichiers à ajouter.  
  
 lpComment  
 [in] Le commentaire à appliquer à tous les fichiers en cours d’ajout.  
  
 pfOptions  
 [in] Tableau d’indicateurs de commande, fourni sur une base par fichier.  
  
 pvOptions  
 [in] Options spécifiques au plug-in de contrôle source.  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_OK|L’opération d’ajout a réussi.|  
|SCC_E_FILEALREADYEXISTS|Le fichier sélectionné est déjà sous contrôle de code source.|  
|SCC_E_TYPENOTSUPPORTED|Le type du fichier (par exemple, binaire) n’est pas pris en charge par le système de contrôle de code source.|  
|SCC_E_OPNOTSUPPORTED|Le système de contrôle de code source ne prend pas en charge cette opération.|  
|SCC_E_ACCESSFAILURE|Impossible d’accéder au système de contrôle source, probablement en raison de problèmes réseau ou de contention. Une nouvelle tentative est recommandée.|  
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer cette opération.|  
|SCC_E_NONSPECIFICERROR|Échec non spécifique ; Ajoutez ne pas effectuée.|  
|SCC_I_OPERATIONCANCELED|L’opération a été annulée avant la fin.|  
|SCC_I_RELOADFILE|Un fichier ou un projet doit être rechargé.|  
|SCC_E_FILENOTEXIST|Fichier local est introuvable.|  
  
## <a name="remarks"></a>Notes  
 Habituelles `fOptions` sont remplacés ici par un tableau, `pfOptions`, avec une `LONG` option spécification par fichier. Il s’agit, car le type de fichier peut varier d’un fichier.  
  
> [!NOTE]
>  Il n’est pas valide pour spécifier les deux `SCC_FILETYPE_TEXT` et `SCC_FILETYPE_BINARY` options pour le même fichier, mais il est possible de spécifier aucune des deux. Aucun paramètre est équivalent au paramètre `SCC_FILETYPE_AUTO`, auquel cas la source de contrôler les plug-in détecte automatiquement le type de fichier.  
  
 Voici la liste des indicateurs utilisés dans le `pfOptions` tableau :  
  
|Option|Value|Signification|  
|------------|-----------|-------------|  
|SCC_FILETYPE_AUTO|0 x 00|Le plug-in de contrôle de code source doit détecter le type de fichier.|  
|SCC_FILETYPE_TEXT|0 x 01|Indique un fichier texte ASCII.|  
|SCC_FILETYPE_BINARY|0 x 02|Indique un type de fichier autre que texte ASCII.|  
|SCC_ADD_STORELATEST|0 x 04|Stocke uniquement la dernière copie du fichier, aucun deltas.|  
|SCC_FILETYPE_TEXT_ANSI|0 x 08|Traite le fichier comme texte ANSI.|  
|SCC_FILETYPE_UTF8|0x10|Traite le fichier en tant que texte Unicode au format UTF8.|  
|SCC_FILETYPE_UTF16LE|0 x 20|Traite le fichier en tant que texte Unicode dans UTF16 format Little Endian.|  
|SCC_FILETYPE_UTF16BE|0 x 40|Mettre en forme traite le fichier en tant que texte Unicode Big Endian UTF16.|  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)

