---
title: 'Comment : créer une application de service de flux de travail WCF | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 12d675ac-27d8-4d86-ba16-6f7688f8c841
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9bf941babd943c6856809a13de847b62745b2056
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72605012"
---
# <a name="how-to-create-a-wcf-workflow-service-application"></a>Procédure : créer une application de service de workflow WCF
Les applications de service de workflow [!INCLUDE[indigo1](../includes/indigo1-md.md)] sont des services de communications distribués qui passent des messages entre des clients et eux-mêmes au-delà des limites du processus. L'implémentation du contrat de service du côté service s'effectue de façon déclarative via des activités de workflow dans [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] d'une manière analogue à celle des services de workflow hérités dans le .NET Framework 3.5.

### <a name="to-create-a-wcf-workflow-service-application"></a>Pour créer une application de service de workflow WCF

1. Démarrez [!INCLUDE[vs2010](../includes/vs2010-md.md)].

2. Dans le menu **fichier** , pointez sur **nouveau**, puis sélectionnez **projet...**.

     La boîte de dialogue **Nouveau projet** s’affiche.

3. Dans le volet **modèles installés** , sélectionnez **WCF** ou **Workflow** dans les regroupements **Visual C#** ou **Visual Basic** selon le langage de votre choix.

4. Dans le volet central, sélectionnez **application de service de flux de travail WCF**.

5. Dans la zone **nom** , entrez un nom descriptif pour votre projet afin de faciliter son identification.

6. Dans la zone **emplacement** , entrez le répertoire dans lequel vous souhaitez enregistrer votre projet ou cliquez sur **Parcourir** pour y accéder.

7. Dans la zone **solution** , sélectionnez créer une solution, puis cliquez sur **OK**.

    > [!NOTE]
    > Si vous souhaitez ajouter une application console de workflow à une solution existante, ouvrez cette solution dans [!INCLUDE[vs2010](../includes/vs2010-md.md)] , cliquez avec le bouton droit sur la solution dans **Explorateur de solutions**, puis sélectionnez **Ajouter**, puis **nouveau projet...** pour ouvrir la boîte de dialogue **nouveau projet** . Procédez comme décrit ci-dessus dans cette procédure.

8. Le modèle de projet crée une définition de service au format XAML. [!INCLUDE[wfd1](../includes/wfd1-md.md)] s'ouvre en mode Design avec une activité <xref:System.Activities.Statements.Sequence> qui contient un ensemble d'activités <xref:System.ServiceModel.Activities.Receive> et <xref:System.ServiceModel.Activities.SendReply>.

## <a name="see-also"></a>Voir aussi
 [Comment : créer une activité](https://msdn.microsoft.com/library/c09b1e99-21b5-4d96-9c04-ec31db3f4436) [créant un projet de workflow](../workflow-designer/creating-a-workflow-project.md)