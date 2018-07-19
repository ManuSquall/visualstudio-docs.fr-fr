---
title: Architecture de plug-in de contrôle de source | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, architecture
ms.assetid: 35351d4c-9414-409b-98fc-f2023e2426b7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 498f3aeb87855a0dac5afacc1baa7e2e816375f2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132389"
---
# <a name="source-control-plug-in-architecture"></a>Architecture de plug-in de contrôle de code source
Vous pouvez ajouter la prise en charge du contrôle de source pour le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE) en implémentant et en attachant un plug-in de contrôle de code source. L’IDE se connecte au contrôle de source de plug-in via l’API de plug-in du contrôle Source bien défini. L’IDE expose les fonctionnalités de contrôle de version du système de contrôle de code source en fournissant une interface utilisateur (IU) qui se compose de barres d’outils et les commandes de menu. Le plug-in de contrôle de code source implémente la fonctionnalité de contrôle de code source.  
  
## <a name="source-control-plug-in-resources"></a>Ressources de plug-in de contrôle de code source  
 Le plug-in de contrôle de code Source fournit des ressources pour aider à créer et connecter votre application de contrôle de version à la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Le plug-in de contrôle de code Source contient la spécification de l’API qui doit être implémentée par un plug-in de contrôle de code source afin qu’il peut être intégré dans le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Il contient également un exemple de code (écrit en C++) qui implémente une squelette source contrôle plug-in démonstration implémentation de fonctions essentielles compatibles avec l’API de plug-in de contrôle de Source.  
  
 La spécification de l’API de plug-in de contrôle de code Source vous permet de tirer parti de n’importe quel système de contrôle de source de votre choix si vous créez un DLL de contrôle de code source avec le jeu de fonctions implémentés conformément à l’API de plug-in de contrôle de Source requis.  
  
## <a name="components"></a>Composants  
 Le Package de l’adaptateur de contrôle Source dans le diagramme est le composant de l’IDE qui se traduit par la demande de l’utilisateur pour une opération de contrôle de code source dans un appel de fonction pris en charge par le plug-in de contrôle de code source. Pour ce faire, l’IDE et le plug-in de contrôle de code source doivent avoir une boîte de dialogue efficace qui transmet des informations dans les deux sens entre l’IDE et le plug-in. Pour cette boîte de dialogue puisse avoir lieu, les deux doivent parlent la même langue. L’API de plug-in de contrôle de Source décrites dans cette documentation est le vocabulaire commun pour cet échange.  
  
 ![Diagramme d’Architecture de contrôle de Code source de](../../extensibility/internals/media/vs_sccsdk_plug_in_arch.gif "vs_sccsdk_plug_in_arch")  
Diagramme architectural montrant une interaction entre VS et le contrôle de source de plug-in  
  
 Comme indiqué dans le diagramme d’architecture, le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] shell, comme le shell Visual Studio dans le diagramme, héberge des projets de travail de l’utilisateur et les composants associés, tels que les éditeurs et l’Explorateur de solutions. Le Package de l’adaptateur de Source contrôle gère l’interaction entre l’IDE et le plug-in de contrôle de code source. Le Package de l’adaptateur de contrôle Source fournit sa propre interface utilisateur du contrôle de code source. Il s’agit de l’interface utilisateur de niveau supérieur que l’utilisateur interagit avec afin de lancer et définir l’étendue d’une opération de contrôle de code source.  
  
 Le plug-in de contrôle de code source peut avoir sa propre interface utilisateur, ce qui peut être constitué de deux parties, comme indiqué dans l’illustration. La zone intitulée « Fournisseur UI » représente les éléments d’interface utilisateur personnalisée que vous, en tant qu’un créateur de plug-in de contrôle source, fournissez. Lorsque l’utilisateur appelle une opération de contrôle de source avancées, elles sont affichées directement par le plug-in de contrôle de code source. La zone intitulée « Interface d’assistance » est un ensemble de plug-in interface utilisateur fonctionnalités du contrôle source qui sont appelées indirectement via l’IDE. Le plug-in de contrôle de code source transmet les messages relatifs à l’interface utilisateur à l’IDE par le biais des fonctions de rappel spéciale fourni par l’IDE. L’application d’assistance de l’interface utilisateur facilitant l’intégration plus transparente avec l’IDE (souvent à l’aide d’un **avancé** bouton) et fournit ainsi une expérience utilisateur plus unifiée.  
  
 Un plug-in de contrôle de code source ne peut pas apporter des modifications à la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] d’environnement et, par conséquent, le Package de l’adaptateur de contrôle de Source ou de la source de contrôle de l’interface utilisateur fournie par l’IDE. Il doit permettre une utilisation maximale de la souplesse offerte par la mise en oeuvre des différentes fonctions d’API de plug-in de contrôle de code Source qui contribuent à une expérience intégrée pour l’utilisateur final. La section de référence de la documentation de l’API de plug-in de contrôle de code Source inclut des informations pour certaines fonctionnalités de plug-in du contrôle source avancées. Pour exploiter ces fonctionnalités, le plug-in de contrôle de code source doit déclarer ses fonctionnalités avancées à l’IDE pendant l’initialisation, et il doit implémenter des fonctions avancées spécifiques pour chaque fonctionnalité.  
  
## <a name="see-also"></a>Voir aussi  
 [Plug-ins de contrôle de code source](../../extensibility/source-control-plug-ins.md)   
 [Glossaire](../../extensibility/source-control-plug-in-glossary.md)   
 [Création d’un plug-in de contrôle de code source](../../extensibility/internals/creating-a-source-control-plug-in.md)