---
title: Modèles d’interaction pour Visual Studio | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 094e16fea46e459dd64338ffa5daf3f7b98afb90
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31142430"
---
# <a name="interaction-patterns-for-visual-studio"></a>Modèles d’interaction pour Visual Studio
## <a name="overview"></a>Vue d'ensemble  
 Un modèle de conception, en général, est le cœur d’une conception qui peut être appliquée dans des situations spécifiques pour résoudre des problèmes avec des ensembles similaires de contraintes. Concepteurs de fonctionnalités et système utilisent ces modèles de conception comme points, qui peuvent ensuite être adaptées à leur situation spécifique de départ.  
  
 Visual Studio propose une bibliothèque de modèles d’interaction commun à prendre en compte lors de la création de nouvelles fonctionnalités. Il existe deux contextes de base pour nos modèles de conception : du Client Visual Studio (devenv) et Visual Studio Online. Pour certains problèmes de conception, il est un modèle omniprésent qui fonctionne bien dans toutes les situations. Toutefois, dans de nombreux cas, la solution peut-être être différente pour l’interface utilisateur qui est présenté dans un navigateur et qui est hébergé sur une application cliente.  
  
### <a name="visual-studio-client-pattern-types"></a>Types de modèle Visual Studio Client  
  
|Type de modèle|Description|Exemples|  
|------------------|-----------------|--------------|  
|**Modèles de niveau application**|Modèles de haut niveau communes à l’application, la détermination ou afficher le contexte de l’application et contenant composite et modèles de contrôle dans les|-Fenêtres Outil<br />-Fenêtres de document|  
|**Modèles composites**|Modèles courants qui peuvent être réparties entre les modèles d’application ou un modèle reconnu constitué de plusieurs contrôles dans une configuration distincte|-Basculement entre les vues<br />-Les générateurs liste<br />-Affichage des données<br />-Les notifications<br />-Validation<br />-Modèles de sélection|  
|**Modèles de contrôle**|Détails sur les contrôles comment de bas niveau doivent se comporter|: Vues de l’arborescence<br />-Modification au sein d’un contrôle de grille|  
  
## <a name="application-patterns"></a>Modèles d’application  
 À un niveau élevé, l’interface de Visual Studio comprend plusieurs fenêtres, boîtes de dialogue, commandes et barres d’outils dans un IDE unique. La hiérarchie de Visual Studio détermine les menus de contexte et des lecteurs. Les points d’intégration clés dans l’interface utilisateur de l’IDE sont des fenêtres de document, les fenêtres Outil, projets, la structure de la commande, l’éditeur de texte, la boîte à outils, la fenêtre Propriétés et outils > Options.  
  
 Il existe des modèles d’utilisation de base pour chacun des points d’intégration clés dans l’interface utilisateur de l’IDE :  
  
-   [Menus et commandes pour Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)  
  
-   [Modèles d’application pour Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)  
  
    -   [Interactions de la fenêtre](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)  
  
    -   [Fenêtres Outil](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)  
  
    -   [Conventions de l’éditeur de document](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)  
  
    -   [Boîtes de dialogue](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)  
  
    -   [Projets](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)  
  
## <a name="common-control-patterns"></a>Modèles de contrôle commun  
 Modèles de contrôle sont principalement sur la manière dont les contrôles doivent se comporter. Il s’agit d’une zone dans laquelle la cohérence est plus importante.  
  
 Contrôles les plus courants dans Visual Studio doivent suivre les instructions de bureau Windows. Nos instructions incluent uniquement les domaines dans lequel il faut augmenter conventions courantes avec les interactions spécifiques à Visual Studio ou les emplacements dans lesquels nous remplacent les instructions entièrement afin de personnaliser Visual Studio pour répondre aux besoins de nos utilisateurs sophistiquées.  
  
-   [Modèles de contrôle courants pour Visual Studio](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)  
  
    -   [Contrôles courants](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)  
  
    -   [Contrôles de texte](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)  
  
    -   [Boutons et des liens hypertexte](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)  
  
## <a name="composite-patterns"></a>Modèles composites  
 Il existe plusieurs façons pour que les utilisateurs s’attendent à accomplir des tâches. Dans la mesure du possible, les fonctionnalités doivent être conçues pour utiliser ces modèles à la fois d’interaction et de conception visuelle.  
  
 Bien qu’il existe de nombreux modèles composites dans Visual Studio, certains des plus importants en ce qui concerne la cohérence sont :  
  
-   [Modèles composites pour Visual Studio](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)  
  
    -   [L’interface utilisateur sur l’objet et la lecture](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)  
  
    -   [Modèles de sélection](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)  
  
    -   [Persistance et l’enregistrement des paramètres](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)  
  
    -   [Entrée tactile](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)