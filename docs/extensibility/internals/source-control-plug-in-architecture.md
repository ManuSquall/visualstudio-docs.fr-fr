---
title: Architecture plug-in de contrôle des sources (en anglais) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, architecture
ms.assetid: 35351d4c-9414-409b-98fc-f2023e2426b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f549ad2c4ee456860a08fbf20ccda813934a8582
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705106"
---
# <a name="source-control-plug-in-architecture"></a>Architecture du plug-in de contrôle de code source
Vous pouvez ajouter un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] support de contrôle des sources à l’environnement de développement intégré (IDE) en mettant en œuvre et en attachant un plug-in de contrôle source. L’IDE se connecte au plug-in de contrôle source via l’API de contrôle source bien défini. L’IDE expose les fonctionnalités de contrôle de version du système de contrôle source en fournissant une interface utilisateur (interface utilisateur) qui se compose de barres d’outils et de commandes de menu. Le plug-in de contrôle source implémente la fonctionnalité de contrôle source.

## <a name="source-control-plug-in-resources"></a>Ressources de recharge de contrôle des sources
 Le plug-in source Control fournit des ressources pour aider [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] à créer et connecter votre application de version à l’IDE. Le plug-in source De contrôle contient les spécifications de l’API qui doivent être [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] implémentées par un plug-in de contrôle source afin qu’il puisse être intégré dans l’IDE. Il contient également un échantillon de code (écrit en CMD) qui implémente un plug-in de contrôle source squelette démontrant la mise en œuvre de fonctions essentielles conformes à l’API de contrôle source.

 Les spécifications de l’API de contrôle source vous permettent de tirer parti de n’importe quel système de contrôle source de votre choix si vous créez un DLL de contrôle source avec l’ensemble de fonctions requis mis en œuvre conformément à l’API de contrôle source.

## <a name="components"></a>Components
 Le paquet d’adaptateur de contrôle des sources dans le diagramme est le composant de l’IDE qui traduit la demande de l’utilisateur pour une opération de contrôle source dans un appel de fonction soutenu par le plug-in de contrôle source. Pour ce faire, l’IDE et le plug-in de contrôle source doivent avoir un dialogue efficace qui transmet l’information d’avant en arrière entre l’IDE et le plug-in. Pour que ce dialogue ait lieu, ils doivent tous deux parler la même langue. L’API de contrôle source API décrit dans cette documentation est le vocabulaire commun pour cet échange.

 ![Diagramme d’architecture de contrôle de code de source](../../extensibility/internals/media/vs_sccsdk_plug_in_arch.gif "vs_sccsdk_plug_in_arch") Diagramme d’architecture montrant l’interaction entre VS et plug-in de contrôle de source

 Comme le montre le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] diagramme d’architecture, la coque, étiquetée comme coque VS dans le diagramme, héberge les projets de travail de l’utilisateur et les composants associés, tels que les éditeurs et Solution Explorer. Le paquet d’adaptateur de contrôle des sources gère l’interaction entre l’IDE et le plug-in de contrôle source. Le paquet d’adaptateur de contrôle source fournit sa propre interface utilisateur de contrôle source. C’est l’interface utilisateur de haut niveau avec laquelle l’utilisateur interagit afin d’initier et de définir la portée d’une opération de contrôle source.

 Le plug-in de contrôle source peut avoir sa propre interface utilisateur, qui peut se composer de deux parties comme indiqué dans la figure. La boîte étiquetée « Assurance-chômage du fournisseur » représente les éléments d’interface utilisateur personnalisés que vous, en tant que créateur de plug-in de contrôle source, fournissez. Ceux-ci sont affichés directement par le plug-in de contrôle source lorsque l’utilisateur invoque une opération avancée de contrôle de source. La boîte étiquetée "Helper UI" est un ensemble de fonctionnalités d’interface utilisateur de plug-in de contrôle de la source qui sont indirectement invoquées par l’IDE. Le plug-in de contrôle source transmet les messages liés à l’interface utilisateur à l’IDE par le biais de fonctions spéciales de rappel fournies par l’IDE. L’interface utilisateur d’aide facilite une intégration plus transparente avec l’IDE (souvent grâce à l’utilisation d’un bouton **Advanced)** et offre ainsi une expérience utilisateur final plus unifiée.

 Un plug-in de contrôle source [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ne peut pas apporter de modifications à la coque et, par conséquent, soit au paquet d’adaptateur de contrôle source ou à l’interface utilisateur de contrôle source fournie par l’IDE. Il doit faire un meilleur usage de la flexibilité offerte par la mise en œuvre des différentes fonctions d’API de contrôle source qui contribuent à une expérience intégrée pour l’utilisateur final. La section de référence de la documentation sur l’API rechargeable de contrôle des sources comprend des informations pour certaines capacités avancées de plug-in de contrôle des sources. Pour exploiter ces fonctionnalités, le plug-in de contrôle source doit déclarer ses capacités avancées à l’IDE lors de l’initialisation, et il doit implémenter des fonctions avancées spécifiques pour chaque capacité.

## <a name="see-also"></a>Voir aussi
- [Plug-ins de contrôle de code source](../../extensibility/source-control-plug-ins.md)
- [Glossaire](../../extensibility/source-control-plug-in-glossary.md)
- [Création d’un plug-in de contrôle de code source](../../extensibility/internals/creating-a-source-control-plug-in.md)
