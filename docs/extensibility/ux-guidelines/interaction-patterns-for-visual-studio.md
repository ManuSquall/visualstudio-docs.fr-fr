---
title: Modèles d’interaction pour Visual Studio | Microsoft Docs
description: En savoir plus sur la bibliothèque de modèles d’interaction courants que vous pouvez utiliser lors de la création de nouvelles fonctionnalités pour Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 05/13/2020
ms.topic: reference
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 13a2ec4332cf8010dc5d214dfd61936725ac2063
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900549"
---
# <a name="interaction-patterns-for-visual-studio"></a>Modèles d’interaction pour Visual Studio
## <a name="overview"></a>Vue d’ensemble
 Un modèle de conception, en général, est le cœur d’une conception qui peut être appliqué dans des situations spécifiques pour résoudre des problèmes avec des ensembles de contraintes similaires. Les concepteurs de fonctionnalités et de systèmes utilisent ces modèles de conception comme points de départ, qui peuvent ensuite être adaptés à leur situation spécifique.

 Visual Studio dispose d’une bibliothèque de modèles d’interaction courants qui doivent être pris en compte lors de la création de nouvelles fonctionnalités. Il existe deux contextes principaux pour nos modèles de conception : client Visual Studio (devenv) et GitHub Codespaces (anciennement Visual Studio Online). Pour certains problèmes de conception, il existe un modèle omniprésent qui fonctionne bien dans toutes les situations. Toutefois, dans de nombreux cas, la solution peut être différente pour l’interface utilisateur qui est présentée dans un navigateur et celle qui est hébergée sur une application cliente.

### <a name="visual-studio-client-pattern-types"></a>Types de modèles du client Visual Studio

|Type de modèle|Description|Exemples|
|------------------|-----------------|--------------|
|**Modèles au niveau de l’application**|Modèles de haut niveau communs à l’application, qui déterminent ou affichent le contexte de l’application et qui contiennent des modèles composites et de contrôle dans ceux-ci|-Fenêtres outil<br />-Fenêtres de document|
|**Modèles composites**|Modèles courants qui peuvent s’étendre sur plusieurs modèles d’application, ou un modèle reconnu constitué de plusieurs contrôles dans une configuration distincte|-Basculement de vue<br />-Répertorier les générateurs<br />-Affichage des données<br />-Notifications<br />-Validation<br />-Modèles de sélection|
|**Modèles de contrôle**|Spécificités de la façon dont les contrôles de bas niveau sont censés se comporter|Arborescences<br />-Modification dans un contrôle Grid|

## <a name="application-patterns"></a>Modèles d’application
 À un niveau élevé, l’interface Visual Studio comprend plusieurs fenêtres, boîtes de dialogue, commandes et barres d’outils au sein d’un seul IDE. La hiérarchie Visual Studio détermine les menus du contexte et des lecteurs. Les points d’intégration clés dans l’interface utilisateur de l’IDE sont les fenêtres de document, les fenêtres outil, les projets, la structure de commande, l’éditeur de texte, la boîte à outils, le Fenêtre Propriétés et les options de > outils.

 Il existe des modèles d’utilisation de base pour chacun des principaux points d’intégration de l’interface utilisateur de l’IDE :

- [Menus et commandes pour Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)

- [Modèles d’application pour Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)

  - [Interactions entre les fenêtres](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)

  - [Fenêtres outil](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)

  - [Conventions de l’éditeur de document](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)

  - [Dialogues](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)

  - [Projets](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)

## <a name="common-control-patterns"></a>Modèles de contrôle communs
 Les modèles de contrôle concernent principalement la manière dont les contrôles individuels sont censés se comporter. Il s’agit d’une zone dans laquelle la cohérence est la plus importante.

 La plupart des contrôles courants dans Visual Studio doivent respecter les instructions de Windows pour les ordinateurs de bureau. Nos recommandations incluent uniquement les domaines dans lesquels nous devons augmenter les conventions courantes avec des interactions spécifiques à Visual Studio, ou des emplacements dans lesquels nous remplaçons entièrement les recommandations afin de personnaliser Visual Studio pour répondre aux besoins de nos utilisateurs sophistiqués.

- [Modèles de contrôle courants pour Visual Studio](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)

  - [Contrôles courants](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)

  - [Contrôles de texte](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

  - [Boutons et liens hypertexte](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

## <a name="composite-patterns"></a>Modèles composites
 Les utilisateurs s’attendent à accomplir des tâches de plusieurs façons. Dans la mesure du possible, les fonctionnalités doivent être conçues pour utiliser ces modèles à la fois pour l’interaction et la conception visuelle.

 Bien qu’il existe de nombreux modèles composites dans Visual Studio, voici quelques-uns des plus importants en ce qui concerne la cohérence :

- [Modèles composites pour Visual Studio](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)

  - [Interface utilisateur et aperçu en un objet](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

  - [Modèles de sélection](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

  - [Persistance et enregistrement des paramètres](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

  - [Entrée tactile](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)
