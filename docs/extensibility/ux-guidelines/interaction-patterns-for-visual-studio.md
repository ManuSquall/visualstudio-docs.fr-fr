---
title: Modèles d’interaction pour Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af7a595190d0fb03c34b12bbace4127a8dd5518a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62431860"
---
# <a name="interaction-patterns-for-visual-studio"></a>Modèles d’interaction pour Visual Studio
## <a name="overview"></a>Vue d'ensemble
 Un modèle de conception, en général, est le cœur d’une conception qui peut être appliqué dans des situations spécifiques pour résoudre des problèmes avec des ensembles similaires de contraintes. Concepteurs de fonctionnalités et système utilisent ces modèles de conception comme alternatives qui peuvent ensuite être adaptées à leur situation particulière.

 Visual Studio propose une bibliothèque de modèles d’interaction commun à prendre en compte lors de la création de nouvelles fonctionnalités. Il existe deux contextes core nos modèles de conception : Client de Visual Studio (devenv) et Visual Studio Online. Pour certains problèmes de conception, il existe un modèle omniprésent qui fonctionne bien dans toutes les situations. Toutefois, dans de nombreux cas, la solution peut-être être différente pour l’interface utilisateur qui est présenté dans un navigateur et qui est hébergé sur une application cliente.

### <a name="visual-studio-client-pattern-types"></a>Types de modèles Visual Studio Client

|Type de modèle|Description|Exemples|
|------------------|-----------------|--------------|
|**Modèles de niveau application**|Modèles de haut niveau communes à l’application, détermination ou afficher le contexte de l’application et contenant composite et modèles de contrôle qu’ils contiennent|-Fenêtres Outil<br />-Fenêtres de document|
|**Modèles composites**|Modèles courants qui peuvent englober des modèles d’application ou un modèle reconnu constituées de plusieurs contrôles dans une configuration distincte|-Basculement entre les vues<br />-Générateurs de list<br />-Affichage des données<br />-   Notifications<br />-   Validation<br />-Les modèles sélection|
|**Modèles de contrôle**|Doivent se comporter plus de détails sur les contrôles comment de bas niveau|: Vues de l’arborescence<br />-Édition au sein d’un contrôle de grille|

## <a name="application-patterns"></a>Modèles d’application
 À un niveau élevé, l’interface de Visual Studio comprend plusieurs windows, les boîtes de dialogue, les commandes et les barres d’outils dans un IDE unique. La hiérarchie de Visual Studio détermine le contexte et les lecteurs des menus. Les points d’intégration clés dans l’interface utilisateur de l’IDE sont des fenêtres de document, les fenêtres Outil, projets, la structure de commande, l’éditeur de texte, la boîte à outils, la fenêtre Propriétés et outils > Options.

 Il existe des modèles d’utilisation de base pour chacun des points d’intégration essentiels dans l’interface utilisateur de l’IDE :

- [Menus et commandes pour Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)

- [Modèles d’application pour Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)

    - [Interactions de la fenêtre](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)

    - [Fenêtres Outil](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)

    - [Conventions de l’éditeur de document](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)

    - [Boîtes de dialogue](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)

    - [Projets](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)

## <a name="common-control-patterns"></a>Modèles de contrôle courants
 Modèles de contrôle sont principalement sur la manière dont les contrôles doivent se comporter. Il s’agit d’une zone dans laquelle la cohérence est essentiel.

 Contrôles les plus courants dans Visual Studio doivent suivre les instructions de bureau Windows. Nos instructions incluent uniquement les domaines dans lequel nous avons besoin d’augmenter les conventions courantes avec les interactions spécifique de Visual Studio, ou les emplacements dans lesquels nous remplacent les instructions entièrement afin d’adapter Visual Studio pour répondre aux besoins de nos utilisateurs sophistiquées.

- [Modèles de contrôle courants pour Visual Studio](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)

    - [Contrôles courants](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)

    - [Contrôles de texte](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

    - [Boutons et des liens hypertexte](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

## <a name="composite-patterns"></a>Modèles composites
 Il existe un nombre de façons dont les utilisateurs s’attendent à accomplir des tâches. Dans la mesure du possible, les fonctionnalités doivent être conçues pour utiliser ces modèles à la fois d’interaction et de conception visuelle.

 Bien qu’il existe de nombreux modèles composites dans Visual Studio, certaines des plus importantes en ce qui concerne la cohérence sont :

- [Modèles composites pour Visual Studio](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)

    - [L’interface utilisateur sur l’objet et la lecture](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

    - [Modèles de sélection](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

    - [Persistance et l’enregistrement des paramètres](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

    - [Entrée tactile](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)