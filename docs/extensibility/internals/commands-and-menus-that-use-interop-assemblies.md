---
title: Commandes et des Menus qui utilisent des assemblys PIA | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ee9fa1faa52afb2ea6d8154b4767fcab2cee0981
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>Commandes et des Menus qui utilisent des assemblys d’interopérabilité
Un VSPackage qui implémente des commandes de menu et barre d’outils à l’aide des assemblys d’interopérabilité doit :  
  
-   Informe le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE) sur les commandes qu’il prend en charge et s’ils sont actuellement activés.  
  
-   Respecter les règles (contrat) pour la gestion des commandes.  
  
-   Implémenter la gestion des commandes à l’aide de manière explicite la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interface.  
  
 La liste suivante décrit comment effectuer ces tâches.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Déterminer l’état de la commande à l’aide d’assemblys d’interopérabilité](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)  
 Décrit la manière dont un VSPackage notifie l’IDE sur les commandes qu’il prend en charge et s’ils sont actuellement activés.  
  
 [Contrats de commande dans les assemblys d’interopérabilité](../../extensibility/internals/command-contracts-in-interop-assemblies.md)  
 Fournit une définition du contrat de commande de base utilisée par tous les packages VS, implémentation des commandes à l’aide des assemblys d’interopérabilité  
  
 [Implémentation](../../extensibility/internals/command-implementation.md)  
 Fournit une vue d’ensemble de la façon dont un VSPackage implémente une commande.  
  
 [Inscription des gestionnaires de commandes d’assemblys d’interopérabilité](../../extensibility/internals/registering-interop-assembly-command-handlers.md)  
 Décrit les entrées de Registre requises pour notifier l’IDE qu’un VSPackage fournit un gestionnaire de commandes.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Disponibilité](../../extensibility/internals/command-availability.md)  
 Décrit les critères utilisés par l’IDE pour déterminer les commandes VSPackage sont disponibles et quel objet les gère.  
  
 [Comment VSPackages ajoute des éléments de l’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Fournit des détails sur la création d’une interface utilisateur qui utilise [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] commande prise en charge.  
  
 [Routage des commandes dans VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)  
 Vue d’ensemble du processus utilisé pour associer un objet avec la demande de commande approprié.