---
title: "Proc&#233;dure&#160;: cr&#233;er une application console de workflow | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 51a2eea7-921c-49f1-b358-68afc27f1ee9
caps.latest.revision: 16
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 16
---
# Proc&#233;dure&#160;: cr&#233;er une application console de workflow
[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] vous permet de créer des workflows pour l'exécution de processus système ou humains.[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] fournit l'aire de conception pour la création de ces workflows.Le [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] peut être utilisé pour créer des workflows depuis [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ou il peut être intégré dans d'autres applications pour réhéberger le concepteur.  
  
 Cette rubrique décrit comment utiliser le [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] dans [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] pour créer un workflow dans une application console.  
  
### Pour créer une application console de workflow  
  
1.  Lancez [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)].  
  
2.  Dans le menu **Fichier**, pointez sur **Nouveau**, puis sélectionnez **Projet**.  
  
     La boîte de dialogue **Nouveau projet** s'affiche.  
  
3.  Dans le volet **Modèles installés**, sélectionnez **Workflow** depuis les regroupements **Visual C\#** ou **Visual Basic**, selon le langage que vous préférez.  
  
4.  Dans le volet central, sélectionnez **Application console de workflow**.  
  
5.  Dans la zone **Nom**, entrez un nom descriptif associé à votre projet afin de faciliter son identification.  
  
6.  Dans la zone **Emplacement**, entrez le répertoire dans lequel vous désirez enregistrer votre projet ou bien cliquez sur **Parcourir** pour naviguer jusqu'à celui\-ci.  
  
7.  Dans la zone **Solution**, entrez le nom de la nouvelle solution.Cliquez sur **OK** pour créer l'application.  
  
    > [!NOTE]
    >  Si vous souhaitez ajouter une application console de workflow à une solution existante, ouvrez cette solution dans [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)], cliquez avec le bouton droit sur la solution dans l'**Explorateur de solutions** et sélectionnez **Ajouter**, puis **Nouveau projet** pour ouvrir la boîte de dialogue **Nouveau projet**.Procédez comme décrit ci\-dessus dans cette procédure.  
  
8.  Le modèle de projet crée une définition de workflow en XAML et la définition d'application console se trouve dans le code source.[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] s'ouvre et affiche la zone de dessin du workflow que vous avez créé.  
  
9. Pour composer un workflow, faites glisser les activités ou d'autres éléments de workflow de la **Boîte à outils** vers l'aire de conception dans votre workflow.  
  
## Voir aussi  
 [Création d'un projet de workflow](../workflow-designer/creating-a-workflow-project.md)