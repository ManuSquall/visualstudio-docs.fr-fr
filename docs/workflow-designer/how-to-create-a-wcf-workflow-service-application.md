---
title: "Proc&#233;dure&#160;: cr&#233;er une application de service de workflow WCF | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 12d675ac-27d8-4d86-ba16-6f7688f8c841
caps.latest.revision: 14
caps.handback.revision: 14
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Proc&#233;dure&#160;: cr&#233;er une application de service de workflow WCF
Les applications de service de workflow [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] sont des services de communications distribués qui passent des messages entre des clients et eux\-mêmes au\-delà des limites du processus.L'implémentation du contrat de service du côté service s'effectue de façon déclarative via des activités de workflow dans [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] d'une manière analogue à celle des services de workflow hérités dans le .NET Framework 3.5.  
  
### Pour créer une application de service de workflow WCF  
  
1.  Lancez [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)].  
  
2.  Dans le menu **Fichier**, pointez sur **Nouveau**, puis sélectionnez **Projet**.  
  
     La boîte de dialogue **Nouveau projet** s'affiche.  
  
3.  Dans le volet **Modèles installés**, sélectionnez **WCF** ou **Workflow** depuis les regroupements **Visual C\#** ou **Visual Basic** selon le langage de votre choix.  
  
4.  Dans le volet central, sélectionnez **Application de service de workflow WCF**.  
  
5.  Dans la zone **Nom**, entrez un nom descriptif associé à votre projet afin de faciliter son identification.  
  
6.  Dans la zone **Emplacement**, entrez le répertoire dans lequel vous désirez enregistrer votre projet ou bien cliquez sur **Parcourir** pour naviguer jusqu'à celui\-ci.  
  
7.  Dans la zone **Solution**, effectuez une sélection pour créer une solution, puis cliquez sur **OK**.  
  
    > [!NOTE]
    >  Si vous souhaitez ajouter une application console de workflow à une solution existante, ouvrez cette solution dans [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)], cliquez avec le bouton droit sur la solution dans l'**Explorateur de solutions** et sélectionnez **Ajouter**, puis **Nouveau projet** pour ouvrir la boîte de dialogue **Nouveau projet**.Procédez comme décrit ci\-dessus dans cette procédure.  
  
8.  Le modèle de projet crée une définition de service au format XAML.[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] s'ouvre en mode Design avec une activité <xref:System.Activities.Statements.Sequence> qui contient un ensemble d'activités <xref:System.ServiceModel.Activities.Receive> et <xref:System.ServiceModel.Activities.SendReply>.  
  
## Voir aussi  
 [Procédure : créer une activité](../Topic/How%20to:%20Create%20an%20Activity.md)   
 [Création d'un projet de workflow](../workflow-designer/creating-a-workflow-project.md)