---
title: Modèles d’interaction pour Studio Visuel (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac917aeb2530570b755e7f1e6fc6de00714a54b0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698373"
---
# <a name="interaction-patterns-for-visual-studio"></a>Modèles d’interaction pour Visual Studio
## <a name="overview"></a>Vue d'ensemble
 Un modèle de conception, en général, est le cœur d’une conception qui peut être appliquée dans des situations spécifiques pour résoudre des problèmes avec des ensembles similaires de contraintes. Les concepteurs de fonctionnalités et de systèmes utilisent ces modèles de conception comme points de départ, qui peuvent ensuite être adaptés à leur situation spécifique.

 Visual Studio a une bibliothèque de modèles d’interaction communs qui devraient être considérés lors de la construction de nouvelles fonctionnalités. Il existe deux contextes de base pour nos modèles de conception: Visual Studio Client (devenv) et Visual Studio Online. Pour certains problèmes de conception, il ya un modèle omniprésent qui fonctionne bien dans toutes les situations. Dans de nombreux cas, cependant, la solution peut être différente pour l’interface utilisateur qui est présenté dans un navigateur et ce qui est hébergé sur une application client.

### <a name="visual-studio-client-pattern-types"></a>Types de modèles Visual Studio Client

|Type de modèle|Description|Exemples|
|------------------|-----------------|--------------|
|**Modèles de niveau d’application**|Modèles de haut niveau communs à l’application, déterminant ou affichant le contexte de l’application, et contenant des modèles composites et de contrôle à l’intérieur d’eux|- Fenêtres d’outils<br />- Fenêtres documentaires|
|**Modèles composites**|Modèles courants qui peuvent s’étendre à travers les modèles d’application, ou un modèle reconnu composé de plusieurs contrôles dans une configuration distincte|- Voir la commutation<br />- Constructeurs de listes<br />- Affichage des données<br />- Notifications<br />- Validation<br />- Modèles de sélection|
|**Modèles de contrôle**|Détails sur la façon dont les contrôles de bas niveau sont censés se comporter|- Vues sur les arbres<br />- Montage dans un contrôle de grille|

## <a name="application-patterns"></a>Modèles d’application
 À un niveau élevé, l’interface Visual Studio comprend plusieurs fenêtres, dialogues, commandes et barres d’outils au sein d’un seul IDE. La hiérarchie Visual Studio détermine le contexte et anime les menus. Les principaux points d’intégration dans l’interface utilisateur de l’IDE sont les fenêtres de documents, les fenêtres d’outils, les projets, la structure de commande, l’éditeur de texte, la boîte à outils, la fenêtre Propriétés et les options > outils.

 Il existe des modèles d’utilisation de base pour chacun des points d’intégration clés de l’interface utilisateur de l’IDE :

- [Menus et commandes pour Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)

- [Modèles d’application pour Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)

  - [Interactions de fenêtre](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)

  - [Fenêtres d’outil](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)

  - [Conventions d’éditeur de documents](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)

  - [Boîtes de dialogue](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)

  - [Projets](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)

## <a name="common-control-patterns"></a>Modèles de contrôle communs
 Les modèles de contrôle portent principalement sur la façon dont les contrôles individuels sont censés se comporter. Il s’agit d’un domaine dans lequel la cohérence est la plus critique.

 La plupart des contrôles courants dans Visual Studio doivent suivre les directives de Desktop Windows. Nos lignes directrices ne comprennent que les domaines dans lesquels nous devons augmenter les conventions communes avec les interactions spécifiques à Visual Studio, ou les endroits dans lesquels nous supérons entièrement les lignes directrices afin d’adapter Visual Studio pour répondre aux besoins de nos utilisateurs sophistiqués.

- [Modèles de contrôle courants pour Visual Studio](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)

  - [Contrôles courants](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)

  - [Contrôles de texte](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

  - [Boutons et hyperliens](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

## <a name="composite-patterns"></a>Modèles composites
 Il existe un certain nombre de façons dont les utilisateurs s’attendent à accomplir des tâches. Dans la mesure du possible, les fonctionnalités doivent être conçues pour utiliser ces modèles à la fois pour l’interaction et la conception visuelle.

 Bien qu’il existe de nombreux modèles composites au sein de Visual Studio, certains des plus importants en ce qui concerne la cohérence sont les :

- [Modèles composites pour Visual Studio](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)

  - [L’interface utilisateur sur l’objet et le regard](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

  - [Modèles de sélection](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

  - [Paramètres de persistance et d’enregistrement](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

  - [Entrée tactile](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)
