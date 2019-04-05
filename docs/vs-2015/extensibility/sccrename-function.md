---
title: Fonction SccRename | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccRename
helpviewer_keywords:
- SccRename function
ms.assetid: b467ade6-a1db-4c0b-b60f-7850ec4f79eb
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e78975acab0bf30f1f188cdd7b6454fd6e74ce6f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58951276"
---
# <a name="sccrename-function"></a>Fonction SccRename
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette fonction renomme un fichier dans le système de contrôle source.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
SCCRTN SccRename(  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPCSTR lpFileName,  
   LPCSTR lpNewName  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pvContext  
 [in] La structure de contexte de plug-in de contrôle de source.  
  
 hWnd  
 [in] Handle vers la fenêtre de l’IDE que le plug-in de contrôle de code source peut utiliser en tant que parent pour les boîtes de dialogue qu’il fournit.  
  
 lpFileName  
 [in] Le nom de fichier qualifié complet du fichier qui est renommé.  
  
 lpNewName  
 [in] Nouveau nom qualifié complet. Si le chemin du répertoire est différent, le fichier a été déplacé à partir d’un sous-répertoire à un autre.  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_OK|L’opération de changement de nom s’est terminée correctement.|  
|SCC_E_PROJNOTOPEN|Le projet n’est pas ouvert sous contrôle de code source.|  
|SCC_E_FILENOTCONTROLLED|Le fichier n’est pas sous contrôle de code source.|  
|SCC_E_ACCESSFAILURE|Impossible d’accéder au système de contrôle source, probablement en raison de problèmes réseau ou de contention.|  
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer cette opération.|  
|SCC_E_COULDNOTCREATEPROJECT|Le projet n’a pas pu être créé dans le cadre du processus de changement de nom.|  
|SCC_E_OPNOTPERFORMED|L’opération n’a pas été effectuée.|  
|SCC_E_NONSPECIFICERROR|Une erreur non spécifiée ou générale s’est produite.|  
  
## <a name="remarks"></a>Notes  
 Cette fonction peut être utilisée pour renommer un fichier ou le déplacer d’un emplacement vers un autre dans le système de contrôle de source. Le plug-in de contrôle de code source ne devez pas essayer d’accéder au fichier sur le disque. Il incombe de l’IDE pour renommer le fichier local.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
