---
title: Fonction de SccPopulateList | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccPopulateList
helpviewer_keywords:
- SccPopulateList function
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 26e7bbb4a99c3cd649eedb7638feb5b6170b3b59
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31140289"
---
# <a name="sccpopulatelist-function"></a>SccPopulateList (fonction)
Cette fonction met à jour une liste de fichiers pour une commande de contrôle source particulière et fournit l’état du contrôle source sur tous les fichiers donnés.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
  
#### <a name="parameters"></a>Paramètres  
 pvContext  
 [in] La structure de contexte plug-in de contrôle de code source.  
  
 %n%ncommande  
 [in] La commande de contrôle de code source qui est appliquée à tous les fichiers dans le `lpFileNames` tableau (consultez [le Code de commande](../extensibility/command-code-enumerator.md) pour obtenir la liste des commandes possible).  
  
 nFiles  
 [in] Nombre de fichiers dans le `lpFileNames` tableau.  
  
 lpFileNames  
 [in] Tableau des noms de fichiers connu à l’IDE.  
  
 pfnPopulate  
 [in] La fonction de rappel à appeler pour ajouter et supprimer des fichiers IDE (consultez [POPLISTFUNC](../extensibility/poplistfunc.md) pour plus d’informations).  
  
 pvCallerData  
 [in] Valeur qui doit être transmis sans modification à la fonction de rappel.  
  
 lpStatus  
 [dans, out] Tableau pour le plug-in pour retourner les indicateurs d’état pour chaque fichier de contrôle de code source.  
  
 fOptions  
 [in] Indicateurs de commandes (consultez la section « Indicateur PopulateList » de [indicateurs de bits utilisés par des commandes spécifiques](../extensibility/bitflags-used-by-specific-commands.md) pour plus d’informations).  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_OK|Opération réussie.|  
|SCC_E_NONSPECIFICERROR|Erreur non spécifique.|  
  
## <a name="remarks"></a>Notes  
 Cette fonction examine la liste des fichiers pour son état actuel. Elle utilise le `pfnPopulate` fonction de rappel pour notifier l’appelant quand un fichier ne correspond pas aux critères pour le `nCommand`. Par exemple, si la commande est `SCC_COMMAND_CHECKIN` un fichier dans la liste n’est pas extrait, puis le rappel est utilisé pour informer l’appelant. Parfois, le plug-in de contrôle de code source peut trouver des autres fichiers qui peuvent faire partie de la commande et les ajouter. Cela permet, par exemple, un utilisateur de Visual Basic extraire un fichier .bmp qui est utilisé par son projet mais n’apparaît pas dans le fichier de projet Visual Basic. Un utilisateur choisit le **obtenir** dans l’IDE. L’IDE affiche une liste de tous les fichiers qu’il pense que l’utilisateur peut obtenir, mais avant que la liste s’affiche, le `SccPopulateList` est appelée pour vous assurer que la liste à afficher est à jour.  
  
## <a name="example"></a>Exemple  
 L’IDE génère une liste de fichiers il pense que l’utilisateur peut obtenir. Avant d’afficher cette liste, il appelle le `SccPopulateList` de fonction, en donnant le plug-in de contrôle de source de la possibilité d’ajouter et de supprimer des fichiers à partir de la liste. Le plug-in modifie la liste en appelant la fonction de rappel donnée (consultez [POPLISTFUNC](../extensibility/poplistfunc.md) pour plus d’informations).  
  
 Continue le plug-in appeler le `pfnPopulate` (fonction), qui ajoute et supprime les fichiers, jusqu'à ce qu’il est terminé et le renvoie à partir de la `SccPopulateList` (fonction). L’IDE peut ensuite afficher sa liste. Le `lpStatus` tableau représente tous les fichiers dans la liste d’origine passé par l’IDE. Le plug-in renseigne l’état de tous les fichiers de plus à faire l’utilisation de la fonction de rappel.  
  
> [!NOTE]
>  Un plug-in de contrôle de code source a toujours la possibilité pour simplement retourner immédiatement à partir de cette fonction, en laissant la liste car il s’agit. Si un plug-in implémente cette fonction, il peut indiquer cela en définissant le `SCC_CAP_POPULATELIST` capacité des indicateurs de bits dans le premier appel à la [SccInitialize](../extensibility/sccinitialize-function.md). Par défaut, le plug-in doit toujours supposer que tous les éléments passés sont des fichiers. Toutefois, si l’IDE définit le `SCC_PL_DIR` indicateur dans le `fOptions` tous les éléments en cours de passage de paramètre, sont à prendre en compte les répertoires. Le plug-in doit ajouter tous les fichiers qui appartiennent dans les répertoires. L’IDE ne passe jamais dans un mélange de fichiers et répertoires.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API de plug-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)   
 [Indicateurs de bits utilisés par des commandes spécifiques](../extensibility/bitflags-used-by-specific-commands.md)   
 [Code de commande](../extensibility/command-code-enumerator.md)