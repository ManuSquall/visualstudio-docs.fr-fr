---
title: "Mod&#232;les d&#39;interaction pour Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# Mod&#232;les d&#39;interaction pour Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

## Vue d'ensemble  
 Un modèle de conception, en général, est le cœur d'une conception qui peut être appliquée dans des situations spécifiques pour résoudre des problèmes avec des ensembles similaires de contraintes. Concepteurs de fonctionnalités et système utilisent ces modèles de conception en tant que points, qui peuvent ensuite être adaptées à leur situation particulière de départ.  
  
 Visual Studio propose une bibliothèque de modèles interaction courants à prendre en compte lors de la création de nouvelles fonctionnalités. Il existe deux contextes de base pour les modèles de conception : Client Visual Studio \(devenv\) et Visual Studio Online. Pour certains problèmes de conception, il existe un motif d'omniprésent qui fonctionne correctement dans toutes les situations. Toutefois, dans de nombreux cas, la solution peut être différente de l'interface utilisateur qui est présenté dans un navigateur et qui est hébergé dans une application cliente.  
  
### Types de modèle Visual Studio Client  
  
|Type de modèle|Description|Exemples|  
|--------------------|-----------------|--------------|  
|**Modèles de niveau application**|Modèles de haut niveau communs à l'application, la détermination ou afficher le contexte de l'application et contenant composite et modèles de contrôle dans les|-   Fenêtres Outil<br />-   Fenêtres de document|  
|**Modèles composites**|Modèles courants qui peuvent englober des modèles d'application, ou un modèle reconnu composé de plusieurs contrôles dans une configuration distincte|-   Basculement entre les vues<br />-   Générateurs de liste<br />-   Affichage des données<br />-   Notifications<br />-   Validation<br />-   Modèles de sélection|  
|**Modèles de contrôle**|Détails sur les contrôles le plus bas niveau doivent se comporter|-   Vues de l'arborescence<br />-   Modification dans un contrôle de grille|  
  
## Modèles d'application  
 À un niveau élevé, l'interface Visual Studio comprend plusieurs windows, les boîtes de dialogue, commandes et barres d'outils dans un environnement IDE unique. La hiérarchie de Visual Studio détermine les menus de contexte et des lecteurs. Les points d'intégration clés dans l'interface utilisateur de l'IDE sont des fenêtres de document, les fenêtres Outil, projets, la structure de commande, l'éditeur de texte, la boîte à outils, la fenêtre Propriétés et outils \> Options.  
  
 Il existe des modèles d'utilisation de base pour chacun des points d'intégration essentiels dans l'interface utilisateur de l'IDE :  
  
-   [Menus et commandes de Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)  
  
-   [Modèles d'application pour Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)  
  
    -   [Interactions de la fenêtre](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)  
  
    -   [Fenêtres Outil](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)  
  
    -   [Conventions de l'éditeur de document](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)  
  
    -   [Boîtes de dialogue](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)  
  
    -   [Projets](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)  
  
## Modèles de contrôle commun  
 Modèles de contrôle sont principalement sur la manière dont les contrôles doivent se comporter. Il s'agit d'une zone dans laquelle la cohérence est plus critique.  
  
 Contrôles les plus courants dans Visual Studio doivent suivre les instructions de bureau Windows. Nos instructions inclure uniquement les zones dans lequel il faut augmenter les conventions courantes avec les interactions spécifiques à Visual Studio ou les emplacements dans lesquels nous remplacent les instructions entièrement afin de personnaliser Visual Studio pour répondre aux besoins de nos utilisateurs sophistiquées.  
  
-   [Modèles de contrôle courants de Visual Studio](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)  
  
    -   [Contrôles courants](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)  
  
    -   [Contrôles de texte](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)  
  
    -   [Boutons et des liens hypertexte](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)  
  
## Modèles composites  
 Il existe plusieurs façons dont les utilisateurs s'attendent à accomplir des tâches. Dans la mesure du possible, fonctionnalités doivent être conçues pour utiliser ces modèles pour l'interaction et de conception visuelle.  
  
 Bien qu'il existe de nombreux modèles composites dans Visual Studio, certaines des plus importantes en ce qui concerne la cohérence sont :  
  
-   [Modèles composites pour Visual Studio](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)  
  
    -   [L'interface utilisateur et la lecture sur les objets](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)  
  
    -   [Modèles de sélection](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)  
  
    -   [Persistance et l'enregistrement des paramètres](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)  
  
    -   [Entrée tactile](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)