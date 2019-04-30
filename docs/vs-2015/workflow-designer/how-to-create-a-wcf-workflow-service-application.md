---
title: 'Procédure : Créer une Application de Service de Workflow WCF | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 12d675ac-27d8-4d86-ba16-6f7688f8c841
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 40b1d2961fa0f0187d11bd87df54ff2ad3124275
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433522"
---
# <a name="how-to-create-a-wcf-workflow-service-application"></a>Procédure : Créer une application de service de workflow WCF
Les applications de service de workflow [!INCLUDE[indigo1](../includes/indigo1-md.md)] sont des services de communications distribués qui passent des messages entre des clients et eux-mêmes au-delà des limites du processus. L'implémentation du contrat de service du côté service s'effectue de façon déclarative via des activités de workflow dans [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] d'une manière analogue à celle des services de workflow hérités dans le .NET Framework 3.5.  
  
### <a name="to-create-a-wcf-workflow-service-application"></a>Pour créer une application de service de workflow WCF  
  
1. Démarrez [!INCLUDE[vs2010](../includes/vs2010-md.md)].  
  
2. Sur le **fichier** menu, pointez sur **New**, puis sélectionnez **projet...** .  
  
     La boîte de dialogue **Nouveau projet** s'affiche.  
  
3. Dans le **modèles installés** volet, sélectionnez **WCF** ou **Workflow** à partir de le le **Visual C#** ou **Visual Basic** regroupements selon le langage de choix.  
  
4. Dans le volet central, sélectionnez **Application de Service de Workflow WCF**.  
  
5. Dans le **nom** , entrez un nom descriptif pour votre projet pour faciliter l’identification.  
  
6. Dans le **emplacement** , entrez le répertoire dans lequel vous souhaitez enregistrer votre projet, ou cliquez sur **Parcourir** pour naviguer jusqu'à lui.  
  
7. Dans le **Solution** , sélectionnez soit créer une nouvelle solution, puis cliquez sur **OK**.  
  
    > [!NOTE]
    > Si vous souhaitez ajouter une application de console de workflow à une solution existante, ouvrez cette solution dans [!INCLUDE[vs2010](../includes/vs2010-md.md)], cliquez avec le bouton droit sur la solution dans **l’Explorateur de solutions**, puis sélectionnez **ajouter**, puis  **Nouveau projet...** Pour ouvrir le **nouveau projet** boîte de dialogue. Procédez comme décrit ci-dessus dans cette procédure.  
  
8. Le modèle de projet crée une définition de service au format XAML. [!INCLUDE[wfd1](../includes/wfd1-md.md)] s'ouvre en mode Design avec une activité <xref:System.Activities.Statements.Sequence> qui contient un ensemble d'activités <xref:System.ServiceModel.Activities.Receive> et <xref:System.ServiceModel.Activities.SendReply>.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour Créer une activité](http://msdn.microsoft.com/library/c09b1e99-21b5-4d96-9c04-ec31db3f4436)   
 [Création d’un projet de flux de travail](../workflow-designer/creating-a-workflow-project.md)