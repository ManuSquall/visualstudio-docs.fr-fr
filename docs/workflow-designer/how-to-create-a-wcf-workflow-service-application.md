---
title: "Comment : créer une Application de Service de Workflow WCF | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 12d675ac-27d8-4d86-ba16-6f7688f8c841
caps.latest.revision: "14"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 62eeab72ab88094f7986bb29bd6f3a55ad6aeff6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-create-a-wcf-workflow-service-application"></a>Procédure : créer une application de service de workflow WCF
Les applications de service de workflow [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] sont des services de communications distribués qui passent des messages entre des clients et eux-mêmes au-delà des limites du processus. L'implémentation du contrat de service du côté service s'effectue de façon déclarative via des activités de workflow dans [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] d'une manière analogue à celle des services de workflow hérités dans le .NET Framework 3.5.  
  
### <a name="to-create-a-wcf-workflow-service-application"></a>Pour créer une application de service de workflow WCF  
  
1.  Démarrez [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)].  
  
2.  Sur le **fichier** menu, pointez sur **nouveau**, puis sélectionnez **projet...** .  
  
     La boîte de dialogue **Nouveau projet** s'affiche.  
  
3.  Dans le **modèles installés** volet, sélectionnez **WCF** ou **Workflow** à partir la **Visual C#** ou **Visual Basic** regroupements selon le langage de choix.  
  
4.  Dans le volet central, sélectionnez **Application de Service de Workflow WCF**.  
  
5.  Dans le **nom** , entrez un nom descriptif pour votre projet afin de faciliter son identification.  
  
6.  Dans le **emplacement** , entrez le répertoire dans lequel vous souhaitez enregistrer votre projet, ou cliquez sur la zone **Parcourir** pour naviguer jusqu'à lui.  
  
7.  Dans le **Solution** , sélectionnez soit créer une nouvelle solution, puis cliquez sur **OK**.  
  
    > [!NOTE]
    >  Si vous souhaitez ajouter une application console de workflow à une solution existante, ouvrez cette solution dans [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)], cliquez avec le bouton droit sur la solution dans **l’Explorateur de solutions**, puis sélectionnez **ajouter**, puis  **Nouveau projet...**  pour ouvrir le **nouveau projet** boîte de dialogue. Procédez comme décrit ci-dessus dans cette procédure.  
  
8.  Le modèle de projet crée une définition de service au format XAML. [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] s'ouvre en mode Design avec une activité <xref:System.Activities.Statements.Sequence> qui contient un ensemble d'activités <xref:System.ServiceModel.Activities.Receive> et <xref:System.ServiceModel.Activities.SendReply>.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : créer une activité](/dotnet/framework/windows-workflow-foundation/how-to-create-an-activity)   
 [Création d’un projet de flux de travail](../workflow-designer/creating-a-workflow-project.md)