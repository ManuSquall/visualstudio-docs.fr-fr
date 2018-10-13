---
title: Fonction SccDirDiff | Microsoft Docs
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
- SccDirDiff
helpviewer_keywords:
- SccDirDiff function
ms.assetid: 26c9ba92-e3b9-4dd2-bd5e-76b17745e308
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2700bd452ec20aa8bf05bf5ec6bde51922356cca
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49218333"
---
# <a name="sccdirdiff-function"></a>Fonction SccDirDiff
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette fonction affiche les différences entre le répertoire local actuel sur le disque du client et le projet sous contrôle de code source correspondant.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 [in] La structure de contexte de plug-in de contrôle de source.  
  
 hWnd  
 [in] Handle vers la fenêtre de l’IDE que le plug-in de contrôle de code source peut utiliser en tant que parent pour les boîtes de dialogue qu’il fournit.  
  
 lpDirName  
 [in] Chemin d’accès complet au répertoire local pour lesquels vous voulez afficher une différence visuelle.  
  
 dwFlags  
 [in] Indicateurs de commande (consultez la section Notes section).  
  
 pvOptions  
 [in] Options spécifiques au plug-in de contrôle source.  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_OK|Le répertoire sur le disque est le même que le projet dans le contrôle de code source.|  
|SCC_I_FILESDIFFER|Le répertoire sur le disque est différent du projet dans le contrôle de code source.|  
|SCC_I_RELOADFILE|Un fichier ou un projet doit être rechargé.|  
|SCC_E_FILENOTCONTROLLED|Le répertoire n’est pas sous contrôle de code source.|  
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer cette opération.|  
|SCC_E_ACCESSFAILURE|Impossible d’accéder au système de contrôle source, probablement en raison de problèmes réseau ou de contention. Une nouvelle tentative est recommandée.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Erreur non spécifique.|  
|SCC_E_FILENOTEXIST|Répertoire local est introuvable.|  
  
## <a name="remarks"></a>Notes  
 Cette fonction est utilisée pour indiquer le plug-in pour afficher la liste des modifications apportées à un répertoire spécifié à l’utilisateur de contrôle de code source. Le plug-in s’ouvre sa propre fenêtre, dans un format de son choix, pour afficher les différences entre le répertoire de l’utilisateur sur le disque et le projet sous contrôle de version correspondant.  
  
 Si une comparaison de plug-in prend en charge des répertoires du tout, il doit prendre en charge la comparaison des répertoires sur une base de nom de fichier même si les options « rapide-diff » ne sont pas pris en charge.  
  
|`dwFlags`|Interprétation|  
|---------------|--------------------|  
|SCC_DIFF_IGNORECASE|Comparaison respectant la casse (peut être utilisé pour comparaison rapide ou visuel).|  
|SCC_DIFF_IGNORESPACE|Ignore les espaces blancs (peut être utilisé pour rapide-diff ou visuel).|  
|SCC_DIFF_QD_CONTENTS|Si la prise en charge par le plug-in de contrôle de code source, en mode silencieux compare le répertoire, octet par octet.|  
|SCC_DIFF_QD_CHECKSUM|Si pris en charge par le plug-in, en mode silencieux compare le répertoire via une somme de contrôle ou, si ne pas pris en charge, revient à SCC_DIFF_QD_CONTENTS.|  
|SCC_DIFF_QD_TIME|Si pris en charge par le plug-in, en mode silencieux compare le répertoire par le biais de son horodatage ou, si ne pas pris en charge, revient sur SCC_DIFF_QD_CHECKSUM ou SCC_DIFF_QD_CONTENTS.|  
  
> [!NOTE]
>  Cette fonction utilise les mêmes indicateurs de commande en tant que le [SccDiff](../extensibility/sccdiff-function.md). Toutefois, un plug-in de contrôle de code source peut choisir de ne prend ne pas en charge l’opération de « rapide-diff » pour les répertoires.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)

