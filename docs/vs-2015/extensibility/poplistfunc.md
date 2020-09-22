---
title: POPLISTFUNC | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- POPDIRLISTFUNC
helpviewer_keywords:
- POPLISTFUNC callback function
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8c3ae2ce451f076c33ea5613b71c6d262c1d7a0e
ms.sourcegitcommit: fb8babf5cd72f1fc2f97ffe4ad7b62d91f325f61
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2020
ms.locfileid: "90839813"
---
# <a name="poplistfunc"></a>POPLISTFUNC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ce rappel est fourni à l' [SccPopulateList](../extensibility/sccpopulatelist-function.md) par l’IDE et est utilisé par le plug-in de contrôle de code source pour mettre à jour une liste de fichiers ou de répertoires (également fournis à la `SccPopulateList` fonction).  
  
 Quand un utilisateur choisit la commande **obtenir** dans l’IDE, l’IDE affiche une zone de liste de tous les fichiers que l’utilisateur peut obtenir. Malheureusement, l’IDE ne connaît pas la liste exacte de tous les fichiers que l’utilisateur peut obtenir ; seul le plug-in contient cette liste. Si d’autres utilisateurs ont ajouté des fichiers au projet de contrôle de code source, ces fichiers doivent apparaître dans la liste, mais l’IDE ne les connaît pas. L’IDE génère une liste des fichiers qu’il estime que l’utilisateur peut obtenir. Avant d’afficher cette liste pour l’utilisateur, elle appelle [SccPopulateList](../extensibility/sccpopulatelist-function.md) `,` en donnant au plug-in de contrôle de code source la possibilité d’ajouter et de supprimer des fichiers dans la liste.  
  
## <a name="signature"></a>Signature  
 Le plug-in de contrôle de code source modifie la liste en appelant une fonction implémentée par l’IDE avec le prototype suivant :  
  
```cpp#  
typedef BOOL (*POPLISTFUNC) (  
   LPVOID pvCallerData,  
   BOOL fAddRemove,  
   LONG nStatus,  
   LPSTR lpFileName  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 pvCallerData  
 `pvCallerData`Paramètre passé par l’appelant (l’IDE) au [SccPopulateList](../extensibility/sccpopulatelist-function.md). Le plug-in de contrôle de code source doit supposer rien du contenu de ce paramètre.  
  
 fAddRemove  
 Si `TRUE` , `lpFileName` est un fichier qui doit être ajouté à la liste de fichiers. Si `FALSE` , `lpFileName` est un fichier qui doit être supprimé de la liste de fichiers.  
  
 nStatus  
 État de `lpFileName` (combinaison des `SCC_STATUS` bits ; pour plus d’informations, consultez le [code d’État du fichier](../extensibility/file-status-code-enumerator.md) ).  
  
 lpFileName  
 Chemin d’accès complet du répertoire du nom de fichier à ajouter ou supprimer de la liste.  
  
## <a name="return-value"></a>Valeur de retour  
  
|Valeur|Description|  
|-----------|-----------------|  
|`TRUE`|Le plug-in peut continuer à appeler cette fonction.|  
|`FALSE`|Il y a eu un problème au niveau de l’IDE (par exemple, une situation de mémoire insuffisante). Le plug-in doit arrêter l’opération.|  
  
## <a name="remarks"></a>Remarques  
 Pour chaque fichier que le plug-in de contrôle de code source souhaite ajouter ou supprimer dans la liste de fichiers, il appelle cette fonction, en passant le `lpFileName` . L' `fAddRemove` indicateur indique un nouveau fichier à ajouter à la liste ou un ancien fichier à supprimer. Le `nStatus` paramètre indique l’état du fichier. Lorsque le plug-in SCC a terminé d’ajouter et de supprimer des fichiers, il retourne à partir de l’appel [SccPopulateList](../extensibility/sccpopulatelist-function.md) .  
  
> [!NOTE]
> Le `SCC_CAP_POPULATELIST` bit de capacité est requis pour Visual Studio.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de rappel implémentées par l’IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [Plug-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)   
 [Code d’état de fichier](../extensibility/file-status-code-enumerator.md)
