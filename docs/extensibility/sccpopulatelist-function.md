---
title: "SccPopulateList (fonction) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccPopulateList"
helpviewer_keywords: 
  - "SccPopulateList (fonction)"
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# SccPopulateList (fonction)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette fonction met à jour une liste de fichiers pour une commande de contrôle source particulière et fournit l'état de contrôle de code source sur tous les fichiers donnés.  
  
## Syntaxe  
  
```cpp#  
SCCRTN SccPopulateList (  
   LPVOID          pvContext,  
   enum SCCCOMMAND nCommand,  
   LONG            nFiles,  
   LPCSTR*         lpFileNames,  
   POPLISTFUNC     pfnPopulate,  
   LPVOID          pvCallerData,  
   LPLONG          lpStatus,  
   LONG            fOptions  
);  
```  
  
#### Paramètres  
 pvContext  
 \[in\] La structure de contexte du plug\-in de contrôle de source.  
  
 %n%ncommande  
 \[in\] La commande de contrôle de code source qui est appliquée à tous les fichiers du `lpFileNames` tableau \(voir [Code de commande](../extensibility/command-code-enumerator.md) pour obtenir la liste des commandes possibles\).  
  
 nFiles  
 \[in\] Nombre de fichiers dans le `lpFileNames` tableau.  
  
 lpFileNames  
 \[in\] Tableau de noms de fichiers connus à l'IDE.  
  
 pfnPopulate  
 \[in\] La fonction de rappel à appeler pour ajouter et supprimer des fichiers IDE \(voir [POPLISTFUNC](../extensibility/poplistfunc.md) Pour plus d'informations\).  
  
 pvCallerData  
 \[in\] Valeur qui doit être passé à la fonction de rappel inchangé.  
  
 lpStatus  
 \[dans, out\] Tableau pour le plug\-in pour retourner les indicateurs d'état pour chaque fichier de contrôle de code source.  
  
 Options  
 \[in\] Indicateurs de commande \(voir la section « Indicateur PopulateList » de [Indicateurs de bits utilisés par des commandes spécifiques](../extensibility/bitflags-used-by-specific-commands.md) Pour plus d'informations\).  
  
## Valeur de retour  
 L'implémentation de plug\-in de contrôle de source de cette fonction est censée renvoyer une des valeurs suivantes :  
  
|Valeur|Description|  
|------------|-----------------|  
|SCC\_OK|Opération réussie.|  
|SCC\_E\_NONSPECIFICERROR|Erreur non spécifique.|  
  
## Notes  
 Cette fonction examine la liste des fichiers concernant son état actuel. Il utilise le `pfnPopulate` fonction de rappel pour notifier l'appelant quand un fichier ne respectent pas les critères pour le `nCommand`. Par exemple, si la commande est `SCC_COMMAND_CHECKIN` un fichier dans la liste n'est pas extrait, puis le rappel est utilisé pour informer l'appelant. Parfois, les autres fichiers qui peuvent faire partie de la commande et les ajouter peuvent se trouver le plug\-in de contrôle de code source. Cela permet, par exemple, un utilisateur de Visual Basic extraire un fichier .bmp qui est utilisé par son projet mais n'apparaît pas dans le fichier de projet Visual Basic. Un utilisateur choisit le **obtenir** commande dans l'IDE. L'IDE affiche une liste de tous les fichiers qu'il pense que l'utilisateur peut obtenir, mais avant l'affichage de la liste, le `SccPopulateList` fonction est appelée pour vérifier que la liste qui s'affiche est à jour.  
  
## Exemple  
 L'IDE génère une liste des fichiers qu'il pense que l'utilisateur peut obtenir. Avant d'afficher cette liste, il appelle le `SccPopulateList` de fonction, ce qui le plug\-in de contrôle de code source permet d'ajouter et supprimer des fichiers à partir de la liste. Le plug\-in modifie la liste en appelant la fonction de rappel donnée \(voir [POPLISTFUNC](../extensibility/poplistfunc.md) Pour plus de détails\).  
  
 Le plug\-in continue d'appeler le `pfnPopulate` \(fonction\), qui ajoute et supprime des fichiers, jusqu'à ce qu'il est terminé et le renvoie à partir de la `SccPopulateList` \(fonction\). L'IDE peut ensuite afficher sa liste. Le `lpStatus` tableau représente tous les fichiers dans la liste d'origine passé par l'IDE. Le plug\-in renseigne l'état de tous ces fichiers en plus à faire d'utilisation de la fonction de rappel.  
  
> [!NOTE]
>  Un plug\-in de contrôle de code source a toujours de simplement retourner immédiatement à partir de cette fonction, en laissant la liste car il s'agit. Si un plug\-in implémente cette fonction, il peut indiquer cela en définissant le `SCC_CAP_POPULATELIST` fonctionnalité indicateur binaire dans le premier appel à la [SccInitialize](../extensibility/sccinitialize-function.md). Par défaut, le plug\-in doit toujours supposent que tous les éléments passés dans les fichiers. Toutefois, si l'IDE définit le `SCC_PL_DIR` indicateur dans le `fOptions` paramètre, tous les éléments passés doivent être considérées comme des répertoires. Le plug\-in doit ajouter tous les fichiers qui appartiennent dans les répertoires. L'IDE ne passe jamais dans un mélange de fichiers et répertoires.  
  
## Voir aussi  
 [Fonctions d'API de plug\-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)   
 [Indicateurs de bits utilisés par des commandes spécifiques](../extensibility/bitflags-used-by-specific-commands.md)   
 [Code de commande](../extensibility/command-code-enumerator.md)