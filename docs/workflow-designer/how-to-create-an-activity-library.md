---
title: "Proc&#233;dure&#160;: cr&#233;er une biblioth&#232;que d&#39;activit&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 1eeebe74-7303-4345-8a83-fe37a26bc84b
caps.latest.revision: 12
caps.handback.revision: 12
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Proc&#233;dure&#160;: cr&#233;er une biblioth&#232;que d&#39;activit&#233;s
Les activités personnalisées permettent de modeler vos processus d'entreprise particuliers dans un workflow.Le modèle Bibliothèque d'activités dans [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] a été fourni pour vous permettre de créer visuellement de telles activités personnalisées à l'aide du [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)].  
  
### Pour créer une bibliothèque d'activités de workflow  
  
1.  Lancez [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)].  
  
2.  Dans le menu **Fichier**, pointez sur **Nouveau**, puis sélectionnez **Projet**.  
  
     La boîte de dialogue **Nouveau projet** s'affiche.  
  
3.  Dans le volet **Types de projet**, sélectionnez **Workflow** dans les projets **Visual C\#** ou les regroupements **Visual Basic** en fonction du langage choisi.  
  
4.  Dans le volet **Modèles**, sélectionnez **Bibliothèque d'activités**.  
  
5.  Dans la zone **Nom**, tapez un nom descriptif associé à votre projet afin de faciliter son identification.  
  
6.  Dans la zone **Emplacement**, tapez le répertoire dans lequel vous souhaitez enregistrer votre projet ou cliquez sur **Parcourir** pour naviguer jusqu'à lui.  
  
7.  Dans la zone **Solution**, tapez un nom descriptif pour votre solution, puis cliquez sur **OK**.  
  
    > [!NOTE]
    >  Si vous souhaitez ajouter une application console de workflow à une solution existante, ouvrez cette solution dans [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)], cliquez avec le bouton droit sur la solution dans l'**Explorateur de solutions** et sélectionnez **Ajouter**, puis **Nouveau projet** pour ouvrir la boîte de dialogue **Nouveau projet**.Procédez comme décrit ci\-dessus dans cette procédure.  
  
8.  Le modèle de projet crée une définition d'activité au format XAML.[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] s'ouvre et affiche la zone de dessin pour votre activité personnalisée.  
  
9. Faites glisser une activité de la **Boîte à outils** vers l'aire de conception pour l'inclure dans votre activité personnalisée.  
  
    > [!CAUTION]
    >  Une seule activité enfant est autorisée dans le corps de votre activité personnalisée ; toutefois, cette activité enfant peut être une activité composite, telle qu'une activité <xref:System.Activities.Statements.Sequence> ou une activité <xref:System.Activities.Statements.Flowchart>.  
  
## Voir aussi  
 [Procédure : créer une activité](../Topic/How%20to:%20Create%20an%20Activity.md)   
 [Création d'un projet de workflow](../workflow-designer/creating-a-workflow-project.md)