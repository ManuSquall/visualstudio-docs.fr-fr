---
title: POPLISTFUNC | Microsoft Docs
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
ms.openlocfilehash: 061f7b4d1c1fb9ddeb76444f058a95fe30abe47c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49920870"
---
# <a name="poplistfunc"></a>POPLISTFUNC
Ce rappel est fourni à la [SccPopulateList](../extensibility/sccpopulatelist-function.md) par l’IDE et est utilisé par le plug-in de contrôle de code source pour mettre à jour une liste de fichiers ou répertoires (également fourni pour le `SccPopulateList` (fonction)).  
  
 Quand un utilisateur choisit le **obtenir** commande dans l’IDE, l’IDE affiche une zone de liste de tous les fichiers que l’utilisateur peut accéder. Malheureusement, l’IDE ne connaît pas la liste exacte de tous les fichiers que l’utilisateur peut obtenir ; uniquement le plug-in a cette liste. Si d’autres utilisateurs ont ajouté des fichiers au projet de contrôle de code source, ces fichiers doivent apparaître dans la liste, mais l’IDE ne sait pas à leur sujet. L’IDE génère une liste des fichiers qui il pense que l’utilisateur peut accéder. Avant d’afficher cette liste à l’utilisateur, il appelle le [SccPopulateList](../extensibility/sccpopulatelist-function.md) `,` en donnant le plug-in de contrôle de code source occasion de vous ajouter et supprimer des fichiers à partir de la liste.  
  
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
 Le `pvCallerData` paramètre passé par l’appelant (l’IDE) à la [SccPopulateList](../extensibility/sccpopulatelist-function.md). Le plug-in de contrôle de code source doit rien deviner à propos du contenu de ce paramètre.  
  
 fAddRemove  
 Si `TRUE`, `lpFileName` est un fichier qui doit être ajouté à la liste des fichiers. Si `FALSE`, `lpFileName` est un fichier qui doit être supprimé à partir de la liste des fichiers.  
  
 État  
 État de `lpFileName` (une combinaison de la `SCC_STATUS` bits ; consultez [Code d’état de fichier](../extensibility/file-status-code-enumerator.md) pour plus d’informations).  
  
 lpFileName  
 Chemin complet du répertoire du nom de fichier pour ajouter ou supprimer dans la liste.  
  
## <a name="return-value"></a>Valeur de retour  
  
|Value|Description|  
|-----------|-----------------|  
|`TRUE`|Le plug-in peut continuer d’appeler cette fonction.|  
|`FALSE`|Il a été un problème sur le côté de l’IDE (par exemple, une de situation de mémoire insuffisante). Le plug-in doit s’arrêter opération.|  
  
## <a name="remarks"></a>Notes  
 Pour chaque fichier que le plug-in de contrôle de code source souhaite ajouter ou supprimer à partir de la liste des fichiers, il appelle cette fonction, en passant le `lpFileName`. Le `fAddRemove` indicateur indique un nouveau fichier à ajouter à la liste ou un ancien fichier à supprimer. Le `nStatus` paramètre donne le statut du fichier. Une fois le plug-in de SCC Ajout et suppression de fichiers, il retourne à partir de la [SccPopulateList](../extensibility/sccpopulatelist-function.md) appeler.  
  
> [!NOTE]
>  Le `SCC_CAP_POPULATELIST` bit de fonctionnalité est requise pour Visual Studio.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de rappel implémentées par l’IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [Plug-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)   
 [Code d’état de fichier](../extensibility/file-status-code-enumerator.md)