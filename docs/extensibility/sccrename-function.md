---
title: "SccRename (fonction) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccRename"
helpviewer_keywords: 
  - "SccRename (fonction)"
ms.assetid: b467ade6-a1db-4c0b-b60f-7850ec4f79eb
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# SccRename (fonction)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette fonction renomme un fichier dans le système de contrôle de code source.  
  
## Syntaxe  
  
```cpp#  
SCCRTN SccRename(  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPCSTR lpFileName,  
   LPCSTR lpNewName  
);  
```  
  
#### Paramètres  
 pvContext  
 \[in\] La structure de contexte du plug\-in de contrôle de source.  
  
 hWnd  
 \[in\] Handle vers la fenêtre de l'IDE que le plug\-in de contrôle de code source peut utiliser en tant que parent pour toutes les boîtes de dialogue qu'il fournit.  
  
 lpFileName  
 \[in\] Le nom de fichier complet du fichier qui est renommé.  
  
 lpNewName  
 \[in\] Le nouveau nom complet. Si le chemin d'accès est différente, le fichier a été déplacé d'un sous\-répertoire à un autre.  
  
## Valeur de retour  
 L'implémentation de plug\-in de contrôle de source de cette fonction est censée renvoyer une des valeurs suivantes :  
  
|Valeur|Description|  
|------------|-----------------|  
|SCC\_OK|L'opération de changement de nom s'est terminée correctement.|  
|SCC\_E\_PROJNOTOPEN|Le projet n'est pas ouvert sous contrôle de code source.|  
|SCC\_E\_FILENOTCONTROLLED|Le fichier n'est pas sous contrôle de code source.|  
|SCC\_E\_ACCESSFAILURE|Impossible d'accéder au système de contrôle source, probablement en raison de problèmes réseau ou de contention.|  
|SCC\_E\_NOTAUTHORIZED|L'utilisateur n'est pas autorisé à effectuer cette opération.|  
|SCC\_E\_COULDNOTCREATEPROJECT|Le projet ne peut pas créé dans le cadre du processus de changement de nom.|  
|SCC\_E\_OPNOTPERFORMED|L'opération n'a pas été effectuée.|  
|SCC\_E\_NONSPECIFICERROR|Une erreur non spécifiée ou générale s'est produite.|  
  
## Notes  
 Cette fonction peut être utilisée pour renommer un fichier ou déplacez\-le à partir d'un emplacement à un autre dans le système de contrôle de code source. Le plug\-in de contrôle de code source ne devez pas essayer d'accéder au fichier sur le disque. Il est responsable de l'IDE pour renommer le fichier local.  
  
## Voir aussi  
 [Fonctions d'API de plug\-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)