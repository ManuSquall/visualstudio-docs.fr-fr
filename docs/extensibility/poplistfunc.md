---
title: POPLISTFUNC | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- POPDIRLISTFUNC
helpviewer_keywords:
- POPLISTFUNC callback function
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 950807b0568a28763b369fef4041c69b264d12fc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="poplistfunc"></a>POPLISTFUNC
Ce rappel est fourni à la [SccPopulateList](../extensibility/sccpopulatelist-function.md) par l’IDE et est utilisé par le plug-in de contrôle de code source pour mettre à jour une liste des fichiers ou répertoires (également fourni à la `SccPopulateList` fonction).  
  
 Quand un utilisateur choisit le **obtenir** commande dans l’IDE, l’IDE affiche une zone de liste de tous les fichiers que l’utilisateur peut obtenir. Malheureusement, l’IDE ne connaît pas la liste exacte de tous les fichiers que l’utilisateur peut obtenir ; uniquement le plug-in a cette liste. Si d’autres utilisateurs ont ajouté des fichiers au projet de contrôle de code source, ces fichiers doivent apparaître dans la liste, mais l’IDE ne sait pas à leur sujet. L’IDE génère une liste des fichiers il pense que l’utilisateur peut obtenir. Avant d’afficher cette liste à l’utilisateur, il appelle la [SccPopulateList](../extensibility/sccpopulatelist-function.md) `,` en donnant le plug-in de contrôle de code source Obtient une occasion d’ajouter et supprimer des fichiers à partir de la liste.  
  
## <a name="signature"></a>Signature  
 Le plug-in de contrôle de code source modifie la liste en appelant une fonction implémentée par l’IDE avec le prototype suivant :  
  
```cpp  
typedef BOOL (*POPLISTFUNC) (  
   LPVOID pvCallerData,  
   BOOL fAddRemove,  
   LONG nStatus,  
   LPSTR lpFileName  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 pvCallerData  
 Le `pvCallerData` paramètre passé par l’appelant (l’IDE) pour le [SccPopulateList](../extensibility/sccpopulatelist-function.md). Le plug-in de contrôle de code source doit supposer rien sur le contenu de ce paramètre.  
  
 fAddRemove  
 Si `TRUE`, `lpFileName` est un fichier qui doit être ajouté à la liste des fichiers. Si `FALSE`, `lpFileName` est un fichier qui doit être supprimé à partir de la liste des fichiers.  
  
 État  
 État de `lpFileName` (une combinaison de la `SCC_STATUS` bits ; consultez [Code d’état de fichier](../extensibility/file-status-code-enumerator.md) pour plus d’informations).  
  
 lpFileName  
 Chemin complet du répertoire du nom de fichier pour ajouter ou supprimer de la liste.  
  
## <a name="return-value"></a>Valeur de retour  
  
|Value|Description|  
|-----------|-----------------|  
|`TRUE`|Le plug-in peut continuer d’appeler cette fonction.|  
|`FALSE`|Un problème a été sur le côté de l’IDE (par exemple, une sortie de la mémoire). Le plug-in doit arrêter une opération.|  
  
## <a name="remarks"></a>Notes  
 Pour chaque fichier du plug-in de contrôle de code source souhaite ajouter ou supprimer de la liste des fichiers, il appelle cette fonction, en passant le `lpFileName`. Le `fAddRemove` indicateur signale un nouveau fichier à ajouter à la liste ou un ancien fichier à supprimer. Le `nStatus` paramètre indique l’état du fichier. Une fois l’analyse de plug-in a ajout et suppression de fichiers, il quitte la [SccPopulateList](../extensibility/sccpopulatelist-function.md) appeler.  
  
> [!NOTE]
>  Le `SCC_CAP_POPULATELIST` bit de fonctionnalité est requise pour Visual Studio.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de rappel implémentées par l’IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [Plug-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)   
 [Code d’état de fichier](../extensibility/file-status-code-enumerator.md)