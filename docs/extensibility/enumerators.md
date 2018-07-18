---
title: Les énumérateurs | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, enumerators
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 84102435092096b7154a46100e9d857a31537482
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31127233"
---
# <a name="enumerators"></a>Énumérateurs
Cette section répertorie les types de données d’énumérateur dans l’API de plug-in de contrôle Source qui doit reconnaître le plug-in de contrôle de code source.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Code de commande](../extensibility/command-code-enumerator.md)  
 Énumère les options pour le [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) et [SccPopulateList](../extensibility/sccpopulatelist-function.md) fonctions.  
  
 [Message](../extensibility/message-enumerator.md)  
 Énumère les indicateurs utilisés pour le rappel d’impression, [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).  
  
 [Code d’état de fichier](../extensibility/file-status-code-enumerator.md)  
 Contient des valeurs de constantes nommées qui spécifient l’état d’un fichier sous contrôle de code source.  
  
 [Code d’état Active](../extensibility/directory-status-code-enumerator.md)  
 Contient des valeurs de constantes nommées qui spécifient l’état d’un répertoire sous contrôle de code source.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Création d’un plug-in de contrôle de code source](../extensibility/internals/creating-a-source-control-plug-in.md)  
 Définit le SDK de plug-in de contrôle de Source et décrit les ressources incluses.  
  
 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)  
 Invite l’utilisateur pour les options avancées pour la commande donnée.  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 Examine la liste des fichiers pour leur état actuel. Utilise en outre, le `pfnPopulate` fonction pour notifier l’appelant quand un fichier ne correspond pas les critères pour le `nCommand`.  
  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 Décrit la fonction de rappel qui est utilisée par [SccOpenProject](../extensibility/sccopenproject-function.md) pour afficher les messages de contrôle de source de plug-in via l’IDE.  
  
 [Plug-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)  
 Fournit une liste complète de tous les éléments dans l’API de plug-in de contrôle de Source.