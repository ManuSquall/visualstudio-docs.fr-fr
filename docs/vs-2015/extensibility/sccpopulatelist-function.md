---
title: Fonction SccPopulateList | Microsoft Docs
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
- SccPopulateList
helpviewer_keywords:
- SccPopulateList function
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: efdb79b765dc515fd1239a633a50684b2bfe9cd0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49816142"
---
# <a name="sccpopulatelist-function"></a>Fonction SccPopulateList
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette fonction met à jour une liste des fichiers pour une commande de contrôle de code source particulier et fournit l’état de contrôle de code source sur tous les fichiers donnés.  
  
## <a name="syntax"></a>Syntaxe  
  
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
  
#### <a name="parameters"></a>Paramètres  
 pvContext  
 [in] La structure de contexte de plug-in de contrôle de source.  
  
 %n%ncommande  
 [in] La commande de contrôle de code source qui est appliquée à tous les fichiers dans le `lpFileNames` tableau (consultez [Code de commande](../extensibility/command-code-enumerator.md) pour obtenir la liste des commandes possible).  
  
 nFiles  
 [in] Nombre de fichiers dans le `lpFileNames` tableau.  
  
 lpFileNames  
 [in] Un tableau de noms de fichiers connus à l’IDE.  
  
 pfnPopulate  
 [in] La fonction de rappel à appeler pour ajouter et supprimer des fichiers IDE (consultez [POPLISTFUNC](../extensibility/poplistfunc.md) pour plus d’informations).  
  
 pvCallerData  
 [in] Valeur qui doit être transmises sans modification à la fonction de rappel.  
  
 lpStatus  
 [in, out] Un tableau pour le plug-in pour retourner les indicateurs d’état pour chaque fichier de contrôle de code source.  
  
 Options  
 [in] Indicateurs de commande (consultez la section « Indicateur PopulateList » de [indicateurs de bits utilisés par les commandes spécifiques](../extensibility/bitflags-used-by-specific-commands.md) pour plus d’informations).  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_OK|Opération réussie.|  
|SCC_E_NONSPECIFICERROR|Erreur non spécifique.|  
  
## <a name="remarks"></a>Notes  
 Cette fonction examine la liste des fichiers pour son état actuel. Il utilise le `pfnPopulate` fonction de rappel pour notifier l’appelant quand un fichier ne correspond pas aux critères pour le `nCommand`. Par exemple, si la commande est `SCC_COMMAND_CHECKIN` un fichier dans la liste n’est pas extrait, puis le rappel est utilisé pour informer l’appelant. Parfois, le plug-in de contrôle de code source peut trouver les autres fichiers qui peuvent faire partie de la commande et les ajouter. Cela permet, par exemple, un utilisateur de Visual Basic extraire un fichier .bmp qui est utilisé par son projet mais n’apparaît pas dans le fichier de projet Visual Basic. Un utilisateur choisit le **obtenir** commande dans l’IDE. L’IDE affiche une liste de tous les fichiers qu’il pense que l’utilisateur peut obtenir, mais avant l’affichage de la liste, le `SccPopulateList` fonction est appelée pour vérifier que la liste à afficher est à jour.  
  
## <a name="example"></a>Exemple  
 L’IDE génère une liste de fichiers il pense que l’utilisateur peut accéder. Avant d’afficher cette liste, il appelle le `SccPopulateList` de fonction, en donnant le plug-in de contrôle de source de la possibilité d’ajouter et de supprimer des fichiers à partir de la liste. Le plug-in modifie la liste en appelant la fonction de rappel donné (consultez [POPLISTFUNC](../extensibility/poplistfunc.md) pour plus d’informations).  
  
 Le plug-in continue d’appeler le `pfnPopulate` (fonction), qui ajoute et supprime les fichiers, jusqu'à ce qu’il est terminé et le renvoie à partir de la `SccPopulateList` (fonction). L’IDE peut ensuite afficher sa liste. Le `lpStatus` tableau représente tous les fichiers dans la liste d’origine passé par l’IDE. Le plug-in renseigne le statut de tous ces fichiers en outre à rendre l’utilisation de la fonction de rappel.  
  
> [!NOTE]
>  Un plug-in de contrôle de code source a toujours la possibilité pour simplement retourner immédiatement à partir de cette fonction, en laissant la liste car il s’agit. Si un plug-in implémente cette fonction, cela peut indiquer cela en définissant le `SCC_CAP_POPULATELIST` indicateur binaire de fonctionnalité dans le premier appel à la [SccInitialize](../extensibility/sccinitialize-function.md). Par défaut, le plug-in doit toujours supposer que tous les éléments transmis dans sont des fichiers. Toutefois, si l’IDE définit le `SCC_PL_DIR` indicateur dans le `fOptions` tous les éléments en cours de passage de paramètre, sont à prendre en compte les répertoires. Le plug-in doit ajouter tous les fichiers qui appartiennent dans les répertoires. L’IDE ne passe jamais dans un mélange de fichiers et répertoires.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API de plug-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)   
 [Indicateurs de bits utilisés par des commandes spécifiques](../extensibility/bitflags-used-by-specific-commands.md)   
 [Code de commande](../extensibility/command-code-enumerator.md)

