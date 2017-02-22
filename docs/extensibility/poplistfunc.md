---
title: "POPLISTFUNC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "POPDIRLISTFUNC"
helpviewer_keywords: 
  - "Fonction de rappel POPLISTFUNC"
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# POPLISTFUNC
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ce rappel est fourni pour le [SccPopulateList](../extensibility/sccpopulatelist-function.md) par l'IDE et est utilisé par le plug\-in de contrôle de code source pour mettre à jour une liste de fichiers ou répertoires \(également fourni à la `SccPopulateList` fonction\).  
  
 Lorsqu'un utilisateur choisit le **obtenir** de commandes dans l'IDE, l'IDE affiche une zone de liste de tous les fichiers que l'utilisateur peut obtenir. Malheureusement, l'IDE ne connaît pas la liste exacte de tous les fichiers que l'utilisateur peut obtenir ; seul le plug\-in a cette liste. Si d'autres utilisateurs ont ajouté des fichiers au projet de contrôle de code source, ces fichiers doivent figurer dans la liste, mais l'IDE ne sait pas à leur sujet. L'IDE génère une liste des fichiers qui il pense que l'utilisateur peut obtenir. Avant d'afficher cette liste à l'utilisateur, il appelle le [SccPopulateList](../extensibility/sccpopulatelist-function.md)`,` donnant le plug\-in de contrôle de code source une chance pour ajouter et supprimer des fichiers à partir de la liste.  
  
## Signature  
 Le plug\-in de contrôle de code source modifie la liste en appelant une fonction IDE implémentées avec le prototype suivant :  
  
```cpp#  
typedef BOOL (*POPLISTFUNC) ( LPVOID pvCallerData, BOOL fAddRemove, LONG nStatus, LPSTR lpFileName );  
```  
  
## Paramètres  
 pvCallerData  
 Le `pvCallerData` paramètre passé par l'appelant \(l'IDE\) à le [SccPopulateList](../extensibility/sccpopulatelist-function.md). Le plug\-in de contrôle de code source doit supposer que rien dans le contenu de ce paramètre.  
  
 fAddRemove  
 Si `TRUE`, `lpFileName` est un fichier qui doit être ajouté à la liste des fichiers. Si `FALSE`, `lpFileName` est un fichier qui doit être supprimé de la liste des fichiers.  
  
 État  
 État de `lpFileName` \(une combinaison de la `SCC_STATUS` bits ; consultez [Code d'état de fichier](../extensibility/file-status-code-enumerator.md) Pour plus d'informations\).  
  
 lpFileName  
 Chemin d'accès complet du répertoire du nom de fichier pour ajouter ou supprimer de la liste.  
  
## Valeur de retour  
  
|Valeur|Description|  
|------------|-----------------|  
|`TRUE`|Le plug\-in peut continuer à appeler cette fonction.|  
|`FALSE`|Il a été un problème sur le côté de l'IDE \(par exemple, une sortie de la mémoire\). Le plug\-in doit arrêter une opération.|  
  
## Notes  
 Pour chaque fichier qui souhaite que le plug\-in de contrôle de code source pour ajouter ou supprimer de la liste des fichiers, il appelle cette fonction, en passant le `lpFileName`. Le `fAddRemove` indicateur indique un nouveau fichier à ajouter à la liste ou un ancien fichier à supprimer. Le `nStatus` paramètre indique l'état du fichier. Une fois le plug\-in de SCC Ajout et suppression de fichiers, il renvoie à partir de la [SccPopulateList](../extensibility/sccpopulatelist-function.md) appeler.  
  
> [!NOTE]
>  Le `SCC_CAP_POPULATELIST` bit de fonctionnalité est requise pour Visual Studio.  
  
## Voir aussi  
 [Fonctions de rappel implémentées par l'IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [Plug\-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)   
 [Code d'état de fichier](../extensibility/file-status-code-enumerator.md)