---
title: "Création d’un contrôle de Source de plug-in | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- plug-ins, source control
- source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: c7e69fa4-150e-469a-a6fc-fa1260bdbb07
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 679559b70096dc7ec3baa792ea98c0c3fea7cc67
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="creating-a-source-control-plug-in"></a>Création d’un contrôle de Source de plug-in
Le Kit de développement logiciel Visual Studio fournit des ressources qui vous permettent d’ajouter la fonctionnalité de contrôle de code source pour le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE). Il vous permet d’utiliser n’importe quelle DLL de plug-in qui est compatible avec l’API de plug-in de contrôle de Source décrites dans cette documentation.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Prise en main](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)  
 Décrit comment installer un plug-in de contrôle de code source et met en évidence les versions d’API de plug-in de contrôle de code Source disponibles actuellement.  
  
 [Architecture](../../extensibility/internals/source-control-plug-in-architecture.md)  
 Utilise un diagramme d’architecture pour expliquer l’intégration d’un contrôle de source de plug-in avec le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 [Guide de test pour les plug-ins de contrôle de code source](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)  
 Fournit des conseils sur la façon de tester l’installation et le fonctionnement d’un plug-in de contrôle de code source.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Création d’un VSPackage de contrôle de code source](../../extensibility/internals/creating-a-source-control-vspackage.md)  
 Explique comment créer un contrôle de source de package Visual Studio qui fournit les fonctionnalités de contrôle de code source non seulement, mais remplace [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’interface utilisateur de contrôle de code source.  
  
 [Plug-ins de contrôle de code source](../../extensibility/source-control-plug-ins.md)  
 Fournit une liste complète de tous les éléments dans l’API de plug-in de contrôle de Source.  
  
 [Contrôle de code source](../../extensibility/internals/source-control.md)  
 Décrit les options pour l’implémentation du contrôle de code source en tant qu’une fonctionnalité intégrée de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].