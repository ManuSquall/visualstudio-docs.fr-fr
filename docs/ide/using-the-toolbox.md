---
title: "Utilisation de la boîte à outils | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.chooseitems
- vs.toolboxpages.activexcontrols
- VS.CHOOSEITEMS.windowsuixamlcomponents
- VS.chooseitems.silverlightcomponents
- VC.EDITORS.RIBBON
- vs.customizetoolbox
- VS.chooseitems.System.Workflow_Components
- vs.chooseitems.frameworkcomponents
- VS.ToolboxPages..NET_Framework_Components
- VS.chooseitems.Microsoft.VisualStudio.Toolbox.VsToolboxPage
- vs.chooseitems.comcomponents
- vs.toolboxpages.NGWS_components
helpviewer_keywords:
- toolbox, adding items
- Visual Studio, toolbox
- toolbox, tabs
- toolbox
ms.assetid: 82e7cb43-4d0b-4e17-b7b0-43f96c22c3c2
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f0945c5618e457005c0fba7e229b8e530efe6c74
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="using-the-toolbox"></a>Utilisation de la boîte à outils
Vous pouvez utiliser la boîte à outils pour ajouter des contrôles et d'autres éléments à votre projet. Vous pouvez glisser-déplacer différents contrôles sur la surface du concepteur que vous utilisez, puis les redimensionner et les positionner.  
  
 La boîte à outils accompagne les modes concepteur, tels que celui associé à un fichier XAML. La boîte à outils affiche uniquement les contrôles utilisables dans le concepteur actuel.  
  
 La version .NET Framework que cible votre projet détermine également les contrôles qui apparaissent dans la boîte à outils. Par défaut, les projets [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)] ciblent .NET Framework 4.5.1. Vous pouvez configurer votre projet de manière à ce qu’il cible une autre version du .NET Framework ; pour ce faire, sélectionnez le nœud du projet dans l’**Explorateur de solutions**, puis accédez à **Propriétés/Application/Framework cible**.  
  
## <a name="managing-the-toolbox-and-its-controls"></a>Gestion de la boîte à outils et de ses contrôles  
 Par défaut, la boîte à outils est réduite le long du côté gauche de l‘IDE de Visual Studio et apparaît quand le curseur se trouve au-dessus d‘elle. Vous pouvez épingler la boîte à outils (en cliquant sur l’icône **Épingler** dans la barre d’outils de la boîte à outils) afin qu’elle demeure ouverte quand vous déplacez le curseur. Vous pouvez également annuler l'ancrage de la fenêtre de la boîte à outils et la faire glisser n'importe où à l'écran. Vous pouvez masquer la boîte à outils, l'ancrer et annuler son ancrage ; pour ce faire, cliquez avec le bouton droit sur la barre d'outils de la boîte à outils, puis sélectionnez l'option concernée.  
  
 Vous pouvez réorganiser les éléments d'un onglet de la boîte à outils ou ajouter des onglets et des éléments personnalisés à l'aide des commandes suivantes du menu contextuel :  
  
-   **Renommer un élément** : renomme l’élément sélectionné.  
  
-   **Afficher tout** : affiche tous les contrôles possibles (pas seulement ceux qui s’appliquent au concepteur actuel).  
  
-   **Vue Liste** : affiche les contrôles sous forme de liste verticale. Si cette option est décochée, les contrôles apparaissent horizontalement.  
  
-   **Choisir les éléments** : ouvre la boîte de dialogue **Choisir des éléments de boîte à outils**, dans laquelle vous pouvez spécifier les éléments qui apparaissent dans la **boîte à outils**. Vous pouvez afficher ou masquer un élément en cochant ou en décochant sa case.  
  
-   **Trier les éléments par ordre alphabétique** : trie les éléments par leur nom.  
  
-   **Réinitialiser la barre d’outils** : restaure les paramètres et éléments par défaut de la boîte à outils.  
  
-   **Ajouter un onglet** : ajoute un nouvel onglet à la boîte à outils.  
  
-   **Monter** : déplace l’élément sélectionné vers le haut.  
  
-   **Descendre** : déplace l’élément sélectionné vers le bas.  
  
## <a name="creating-and-distributing-custom-toolbox-controls"></a>Création et distribution de contrôles de boîte à outils personnalisés  
 Vous pouvez créer un contrôle de boîte à outils personnalisé en Visual Basic ou Visual C#, et vous pouvez démarrer avec un modèle de projet basé sur [Windows Presentation Foundation](../extensibility/creating-a-wpf-toolbox-control.md) ou [Windows Forms](../extensibility/creating-a-windows-forms-toolbox-control.md). Vous pouvez ensuite distribuer votre contrôle à vos collègues ou le publier sur le web à l’aide du [programme d’installation de contrôles de boîte à outils](http://download.microsoft.com/download/8/3/6/836657BD-9CCB-4ED4-B9D2-FB769473B284/TCI_whitepaper.docx).