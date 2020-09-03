---
title: Architecture du plug-in de contrôle de code source | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705106"
---
# <a name="source-control-plug-in-architecture"></a>Architecture du plug-in de contrôle de code source
Vous pouvez ajouter la prise en charge du contrôle de code source à l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] environnement de développement intégré (IDE) en implémentant et en attachant un plug-in de contrôle de code source. L’IDE se connecte au plug-in de contrôle de code source via l’API de plug-in de contrôle de code source bien définie. L’IDE expose les fonctionnalités de contrôle de version du système de contrôle de code source en fournissant une interface utilisateur (IU) composée de barres d’outils et de commandes de menu. Le plug-in de contrôle de code source implémente la fonctionnalité de contrôle de code source.

## <a name="source-control-plug-in-resources"></a>Ressources de plug-in de contrôle de code source
 Le plug-in de contrôle de code source fournit des ressources pour vous aider à créer et à connecter votre application de gestion de versions à l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Le plug-in de contrôle de code source contient la spécification de l’API qui doit être implémentée par un plug-in de contrôle de code source afin qu’il puisse être intégré à l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Il contient également un exemple de code (écrit en C++) qui implémente une structure de plug-in de contrôle de code source illustrant l’implémentation des fonctions essentielles conformes à l’API de plug-in de contrôle de code source.

 La spécification de l’API de plug-in de contrôle de code source vous permet de tirer parti de n’importe quel système de contrôle de code source de votre choix si vous créez une DLL de contrôle de code source avec l’ensemble requis de fonctions implémentées conformément à l’API de plug-in de contrôle de code source.

## <a name="components"></a>Components
 Le package de l’adaptateur de contrôle de code source du diagramme est le composant de l’IDE qui traduit la demande de l’utilisateur d’une opération de contrôle de code source en un appel de fonction pris en charge par le plug-in de contrôle de code source. Pour que cela se produise, l’IDE et le plug-in de contrôle de code source doivent avoir une boîte de dialogue efficace qui transmet les informations entre l’IDE et le plug-in. Pour que cette boîte de dialogue ait lieu, ils doivent tous les deux parler le même langage. L’API de plug-in de contrôle de code source décrite dans cette documentation est le vocabulaire commun de cet échange.

 ![Diagramme de l’architecture de contrôle du code source](../../extensibility/internals/media/vs_sccsdk_plug_in_arch.gif "vs_sccsdk_plug_in_arch") Diagramme d’architecture montrant l’interaction entre le plug-in de contrôle de code source et VS

 Comme indiqué dans le diagramme d’architecture, le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Shell, étiqueté en tant que Shell vs dans le diagramme, héberge les projets de travail de l’utilisateur et les composants associés, tels que les éditeurs et les Explorateur de solutions. Le package de l’adaptateur de contrôle de code source gère l’interaction entre l’IDE et le plug-in de contrôle de code source. Le package de l’adaptateur de contrôle de code source fournit sa propre interface utilisateur de contrôle de code source. Il s’agit de l’interface utilisateur de niveau supérieur avec laquelle l’utilisateur interagit pour initialiser et définir la portée d’une opération de contrôle de code source.

 Le plug-in de contrôle de code source peut avoir sa propre interface utilisateur, qui peut se composer de deux parties, comme indiqué dans la figure. La zone intitulée « interface utilisateur du fournisseur » représente les éléments d’interface utilisateur personnalisés que vous, en tant que créateur de plug-in de contrôle de code source, fournissez. Celles-ci sont affichées directement par le plug-in de contrôle de code source lorsque l’utilisateur appelle une opération de contrôle de code source avancée. La zone intitulée « UI Helper UI » est un ensemble de fonctionnalités d’interface utilisateur de plug-in de contrôle de code source qui sont appelées indirectement via l’IDE. Le plug-in de contrôle de code source passe les messages relatifs à l’interface utilisateur à l’IDE via des fonctions de rappel spéciales fournies par l’IDE. L’interface utilisateur de l’application auxiliaire facilite une intégration plus transparente avec l’IDE (souvent via l’utilisation d’un bouton **avancé** ) et offre ainsi une expérience d’utilisateur final plus unifiée.

 Un plug-in de contrôle de code source ne peut pas apporter de modifications au [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Shell et, par conséquent, au package d’adaptateurs de contrôle de code source ou à l’interface utilisateur du contrôle de code source fourni par l’IDE. Elle doit bénéficier d’une utilisation maximale de la flexibilité offerte par l’implémentation des diverses fonctions d’API de plug-in de contrôle de code source qui contribuent à une expérience intégrée pour l’utilisateur final. La section de référence de la documentation sur l’API de plug-in de contrôle de code source contient des informations sur certaines fonctionnalités avancées de plug-in de contrôle de code source. Pour exploiter ces fonctionnalités, le plug-in de contrôle de code source doit déclarer ses fonctionnalités avancées dans l’IDE pendant l’initialisation, et il doit implémenter des fonctions avancées spécifiques pour chaque fonctionnalité.

## <a name="see-also"></a>Voir aussi
- [Plug-ins de contrôle de code source](../../extensibility/source-control-plug-ins.md)
- [Glossaire](../../extensibility/source-control-plug-in-glossary.md)
- [Création d’un plug-in de contrôle de code source](../../extensibility/internals/creating-a-source-control-plug-in.md)
