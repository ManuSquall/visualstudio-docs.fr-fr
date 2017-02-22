---
title: "SccRunScc (fonction) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccRunScc"
helpviewer_keywords: 
  - "SccRunScc (fonction)"
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# SccRunScc (fonction)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette fonction appelle l'outil d'administration de contrôle source.  
  
## Syntaxe  
  
```cpp#  
SCCRTN SccRunScc(  
   LPVOID  pvContext,  
   HWND    hWnd,  
   LONG    nFiles,  
   LPCSTR* lpFileNames  
);  
```  
  
#### Paramètres  
 pvContext  
 \[in\] La structure de contexte du plug\-in de contrôle de source.  
  
 hWnd  
 \[in\] Handle vers la fenêtre de l'IDE que le plug\-in de contrôle de code source peut utiliser en tant que parent pour toutes les boîtes de dialogue qu'il fournit.  
  
 nFiles  
 \[in\] Nombre de fichiers spécifié dans le `lpFileNames` tableau.  
  
 lpFileNames  
 \[in\] Tableau des noms de fichier sélectionné.  
  
## Valeur de retour  
 L'implémentation de plug\-in de contrôle de source de cette fonction est censée renvoyer une des valeurs suivantes :  
  
|Valeur|Description|  
|------------|-----------------|  
|SCC\_OK|L'outil d'administration de contrôle source a été appelé.|  
|SCC\_I\_OPERATIONCANCELED|L'opération a été annulée.|  
|SCC\_E\_INITIALIZEFAILED|Impossible d'initialiser le système de contrôle de code source.|  
|SCC\_E\_ACCESSFAILURE|Impossible d'accéder au système de contrôle source, probablement en raison de problèmes réseau ou de contention.|  
|SCC\_E\_CONNECTIONFAILURE|Impossible de se connecter au système de contrôle source.|  
|SCC\_E\_FILENOTCONTROLLED|Le fichier sélectionné n'est pas sous contrôle de code source.|  
|SCC\_E\_NONSPECIFICERROR|Erreur non spécifique.|  
  
## Notes  
 Cette fonction permet à l'appelant d'accéder à la gamme complète des fonctionnalités du système de contrôle de code source via un outil d'administration externe. Si le système de contrôle source n'a aucune interface utilisateur, le plug\-in de contrôle de code source peut implémenter une interface pour effectuer des fonctions d'administration nécessaires.  
  
 Cette fonction est appelée avec un nombre et un tableau de noms de fichiers pour les fichiers actuellement sélectionnés. Si l'outil d'administration prend en charge, la liste des fichiers peut être utilisée pour présélectionner des fichiers dans l'interface d'administration ; dans le cas contraire, la liste peut être ignorée.  
  
 Cette fonction est généralement appelée lorsque l'utilisateur sélectionne le **lancement \< serveur de contrôle de code Source \>** à partir de la **fichier** \-\> **contrôle de code Source** menu. Cela **lancer** option de menu peut être toujours désactivée ou même masquée en définissant une entrée de Registre. Pour plus d'informations, consultez [Comment : installer un plug\-in de contrôle de code Source](../extensibility/internals/how-to-install-a-source-control-plug-in.md). Cette fonction est appelée uniquement si [SccInitialize](../extensibility/sccinitialize-function.md) renvoie le `SCC_CAP_RUNSCC` bit de fonctionnalité \(voir [Indicateurs de capacité](../extensibility/capability-flags.md) Pour plus d'informations sur ce périphérique et autres bits de capacité\).  
  
## Voir aussi  
 [Fonctions d'API de plug\-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [Comment : installer un plug\-in de contrôle de code Source](../extensibility/internals/how-to-install-a-source-control-plug-in.md)   
 [Indicateurs de capacité](../extensibility/capability-flags.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)