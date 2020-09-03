---
title: Énumérateurs | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, enumerators
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 65a03a8dc741ec86aca3137f49cd753722ede215
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204567"
---
# <a name="enumerators"></a>Énumérateurs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette section répertorie les types de données d’énumérateur dans l’API de plug-in de contrôle de code source que le plug-in de contrôle de code source doit connaître.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Code de commande](../extensibility/command-code-enumerator.md)  
 Énumère les options pour les fonctions [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) et [SccPopulateList](../extensibility/sccpopulatelist-function.md) .  
  
 [Message](../extensibility/message-enumerator.md)  
 Énumère les indicateurs utilisés pour le rappel d’impression, [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).  
  
 [Code d’état de fichier](../extensibility/file-status-code-enumerator.md)  
 Contient des valeurs constantes nommées qui spécifient l’état d’un fichier sous contrôle de code source.  
  
 [Code d’état de répertoire](../extensibility/directory-status-code-enumerator.md)  
 Contient des valeurs constantes nommées qui spécifient l’état d’un répertoire sous contrôle de code source.  
  
## <a name="related-sections"></a>Sections connexes  
 [Création d’un plug-in de contrôle de code source](../extensibility/internals/creating-a-source-control-plug-in.md)  
 Définit le kit de développement logiciel (SDK) du plug-in de contrôle de code source et décrit les ressources incluses.  
  
 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)  
 Invite l’utilisateur à fournir des options avancées pour la commande donnée.  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 Examine la liste des fichiers pour connaître leur état actuel. En outre, utilise la `pfnPopulate` fonction pour notifier l’appelant lorsqu’un fichier ne correspond pas aux critères de `nCommand` .  
  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 Décrit la fonction de rappel utilisée par [SccOpenProject](../extensibility/sccopenproject-function.md) pour afficher les messages du plug-in de contrôle de code source via l’IDE.  
  
 [Plug-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)  
 Fournit une liste complète de tous les éléments de l’API de plug-in de contrôle de code source.
