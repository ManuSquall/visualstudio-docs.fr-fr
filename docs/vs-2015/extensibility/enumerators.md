---
title: Énumérateurs | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, enumerators
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6dcbd3dea8ad932aec5890bc085873ce3d20a8f0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47507208"
---
# <a name="enumerators"></a>Énumérateurs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [énumérateurs](https://docs.microsoft.com/visualstudio/extensibility/enumerators).  
  
Cette section répertorie les types de données d’énumérateur dans l’API de plug-in de contrôle de Source que le plug-in de contrôle de code source doit connaître.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Code de commande](../extensibility/command-code-enumerator.md)  
 Énumère les options pour le [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) et [SccPopulateList](../extensibility/sccpopulatelist-function.md) fonctions.  
  
 [Message](../extensibility/message-enumerator.md)  
 Énumère les indicateurs utilisés pour le rappel d’impression, [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).  
  
 [Code d’état de fichier](../extensibility/file-status-code-enumerator.md)  
 Contient des valeurs de constantes nommées qui spécifient l’état d’un fichier sous contrôle de code source.  
  
 [Code d’état de répertoire](../extensibility/directory-status-code-enumerator.md)  
 Contient des valeurs de constantes nommées qui spécifient l’état d’un répertoire sous contrôle de code source.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Création d’un plug-in de contrôle de code source](../extensibility/internals/creating-a-source-control-plug-in.md)  
 Définit le SDK de plug-in de contrôle de Source et décrit les ressources incluses.  
  
 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)  
 Invite l’utilisateur pour les options avancées pour la commande donnée.  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 Examine la liste des fichiers pour leur état actuel. En outre, utilise le `pfnPopulate` fonction permettant de notifier l’appelant quand un fichier ne correspond pas aux critères pour le `nCommand`.  
  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 Décrit la fonction de rappel qui est utilisée par [SccOpenProject](../extensibility/sccopenproject-function.md) pour afficher les messages de contrôle de source de plug-in via l’IDE.  
  
 [Plug-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)  
 Fournit une liste complète de tous les éléments dans l’API de plug-in de contrôle de Source.

