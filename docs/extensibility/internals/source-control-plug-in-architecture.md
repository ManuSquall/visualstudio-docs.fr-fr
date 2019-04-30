---
title: Architecture de plug-in de contrôle de source | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, architecture
ms.assetid: 35351d4c-9414-409b-98fc-f2023e2426b7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ff9c73ebbe976df7c3d25304280e743cad0423c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62908505"
---
# <a name="source-control-plug-in-architecture"></a>Architecture du plug-in de contrôle de code source
Vous pouvez ajouter la prise en charge du contrôle de source pour le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE) en implémentant et en joignant un plug-in de contrôle de code source. L’IDE se connecte au contrôle de source de plug-in via l’API de plug-in de contrôle Source bien défini. L’IDE expose les fonctionnalités de contrôle de version du système de contrôle de source en fournissant une interface utilisateur (IU) qui se compose de barres d’outils et commandes de menu. Le plug-in de contrôle de code source implémente la fonctionnalité de contrôle de code source.

## <a name="source-control-plug-in-resources"></a>Ressources Plug-in de contrôle de code source
 Le plug-in de contrôle de code Source fournit des ressources pour aider à créer et connecter votre application de contrôle de version à la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Le plug-in de contrôle de code Source contient la spécification d’API qui doit être implémentée par un plug-in de contrôle de code source afin qu’il peut être intégré dans le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Il contient également un exemple de code (écrit en C++) qui implémente une squelette source contrôle plug-in illustrant implémentation de fonctions essentielles conformes avec l’API de plug-in de contrôle de Source.

 La spécification de l’API de plug-in de contrôle de code Source vous permet de tirer parti de n’importe quel système de contrôle de source de votre choix si vous créez un DLL de contrôle de code source avec l’ensemble de fonctions implémentées conformément à l’API de plug-in de contrôle de Source nécessaire.

## <a name="components"></a>Composants
 Le Package de l’adaptateur de contrôle de code Source dans le diagramme est le composant de l’IDE qui se traduit par la demande de l’utilisateur pour une opération de contrôle de code source dans un appel de fonction pris en charge par le plug-in de contrôle de code source. Pour ce faire, l’IDE et le plug-in de contrôle de code source doivent avoir une boîte de dialogue efficace qui transmet des informations dans les deux sens entre l’IDE et le plug-in. Pour cette boîte de dialogue se déroulent, ils sont tous deux doivent parler la même langue. L’API de plug-in de contrôle de Source décrites dans cette documentation est le vocabulaire commun pour cet échange.

 ![Diagramme d’Architecture de contrôle de Code de la source](../../extensibility/internals/media/vs_sccsdk_plug_in_arch.gif "vs_sccsdk_plug_in_arch") diagramme architectural montrant une interaction entre VS et de contrôle de source de plug-in

 Comme indiqué dans le diagramme d’architecture, le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] shell, étiqueté comme interpréteur de commandes de Visual Studio dans le diagramme, héberge des projets de travail et les composants associés, tels que les éditeurs et l’Explorateur de solutions de l’utilisateur. Le Package de l’adaptateur de contrôle de code Source gère l’interaction entre l’IDE et le plug-in de contrôle de code source. Le Package de l’adaptateur de contrôle de code Source fournit sa propre interface utilisateur du contrôle de code source. Il est l’interface utilisateur de niveau supérieur que l’utilisateur interagit avec afin de lancer et définir l’étendue d’une opération de contrôle de code source.

 Le plug-in de contrôle de code source peut avoir sa propre interface utilisateur, ce qui peut être constitué de deux parties, comme illustré dans la figure. La zone intitulée « L’interface utilisateur du fournisseur » représente les éléments d’interface utilisateur personnalisée que vous, en tant qu’un créateur de plug-in de contrôle source, fournissez. Ceux-ci sont affichées directement par le plug-in de contrôle de code source lorsque l’utilisateur appelle une opération de contrôle de source avancées. La zone intitulée « L’interface utilisateur d’assistance » est un ensemble de fonctionnalités code source contrôle plug-in interface utilisateur qui sont appelées indirectement via l’IDE. Le plug-in de contrôle de code source transmet les messages liés à l’interface utilisateur à l’IDE par le biais des fonctions de rappel spéciale fournies par l’IDE. L’assistance de l’interface utilisateur facilitant l’intégration plus transparente avec l’IDE (souvent à l’aide d’un **avancé** bouton), fournissant ainsi une expérience utilisateur plus unifiée.

 Un plug-in de contrôle de code source ne peut pas apporter des modifications à la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de shell et, par conséquent, pour le Package de l’adaptateur de contrôle de code Source ou la source de contrôler l’interface utilisateur fournie par l’IDE. Il doit être une utilisation maximale de la souplesse offerte par la mise en oeuvre des différentes fonctions d’API de plug-in de contrôle de code Source qui contribuent à une expérience intégrée pour l’utilisateur final. La section de référence de la documentation de l’API de plug-in de contrôle Source inclut des informations pour certaines fonctionnalités de plug-in de contrôle de source avancées. Pour exploiter ces fonctionnalités, le plug-in de contrôle de code source doit déclarer ses fonctionnalités avancées à l’IDE pendant l’initialisation, et il doit implémenter des fonctions avancées spécifiques pour chaque fonctionnalité.

## <a name="see-also"></a>Voir aussi
- [Plug-ins de contrôle de code source](../../extensibility/source-control-plug-ins.md)
- [Glossaire](../../extensibility/source-control-plug-in-glossary.md)
- [Création d’un plug-in de contrôle de code source](../../extensibility/internals/creating-a-source-control-plug-in.md)