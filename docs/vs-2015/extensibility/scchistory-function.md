---
title: Fonction SccHistory | Microsoft Docs
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
- SccHistory
helpviewer_keywords:
- SccHistory function
ms.assetid: a636d9d3-47c1-4b48-ac6b-bcfde19d6cf9
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6b1301fd8103abe1d4f616938e1370121baf0de0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49181640"
---
# <a name="scchistory-function"></a>Fonction SccHistory
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette fonction affiche l’historique des fichiers spécifiés.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 [in] La structure de contexte de plug-in de contrôle de source.  
  
 `hWnd`  
 [in] Handle vers la fenêtre de l’IDE que le plug-in de contrôle de code source peut utiliser en tant que parent pour les boîtes de dialogue qu’il fournit.  
  
 `nFiles`  
 [in] Nombre de fichiers spécifiés dans le `lpFileName` tableau.  
  
 `lpFileName`  
 [in] Tableau des noms qualifiés complets de fichiers.  
  
 `fOptions`  
 [in] Indicateurs de commande (non utilisés actuellement).  
  
 `pvOptions`  
 [in] Options spécifiques au plug-in de contrôle source.  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_OK|Historique des versions était obtenue avec succès.|  
|SCC_I_RELOADFILE|Le système de contrôle de code source en fait modifié le fichier sur le disque lors de l’extraction de l’historique (par exemple, en obtenant d’une ancienne version de celui-ci), afin de l’IDE doit recharger ce fichier.|  
|SCC_E_FILENOTCONTROLLED|Le fichier n’est pas sous contrôle de code source.|  
|SCC_E_OPNOTSUPPORTED|Le système de contrôle de code source ne prend pas en charge cette opération.|  
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer cette opération.|  
|SCC_E_ACCESSFAILURE|Impossible d’accéder au système de contrôle source, probablement en raison de problèmes réseau ou de contention. Une nouvelle tentative est recommandée.|  
|SCC_E_PROJNOTOPEN|Le projet n’a pas été ouvert.|  
|SCC_E_NONSPECIFICERROR|Erreur non spécifique. L’historique des fichiers n’a pas pu être obtenu.|  
  
## <a name="remarks"></a>Notes  
 Le plug-in de contrôle de code source peut afficher sa propre boîte de dialogue pour afficher l’historique de chaque fichier, à l’aide de `hWnd` en tant que la fenêtre parente. Vous pouvez également le texte facultatif sortie rappel fonction fournie à la [SccOpenProject](../extensibility/sccopenproject-function.md) peut être utilisé, si elle est prise en charge.  
  
 Notez que dans certaines circonstances, le fichier en cours d’examen peut changer pendant l’exécution de cet appel. Par exemple, le [!INCLUDE[vsvss](../includes/vsvss-md.md)] commande history permet de l’utilisateur pour obtenir une ancienne version du fichier. Dans ce cas, la source de contrôler les plug-in retourne `SCC_I_RELOAD` pour avertir l’IDE qu’il faut recharger le fichier.  
  
> [!NOTE]
>  Si le plug-in de contrôle de code source ne prend pas en charge cette fonction pour un tableau de fichiers, uniquement l’historique du fichier pour le premier fichier peut être affiché.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API de plug-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)

