---
title: 'Procédure pas à pas : Création d’un Service WCF simple dans les Windows Forms | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF, walkthrough [Visual Studio]
- WCF, Visual Studio tools for
- WCF services
- WCF services, walkthrough
ms.assetid: 5fef1a64-27a4-4f10-aa57-29023e28a2d6
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e14944157a14be4a5e06c26464a4de2cdb2bff1b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47494846"
---
# <a name="walkthrough-creating-a-simple-wcf-service-in-windows-forms"></a>Procédure pas à pas : Création d’un Service WCF simple dans les Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [procédure pas à pas : création d’un Service WCF simple dans les Windows Forms](https://docs.microsoft.com/visualstudio/data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms).  
  
  
Cette procédure pas à pas montre comment créer un simple service [!INCLUDE[vsindigo](../includes/vsindigo-md.md)], le tester et y accéder à partir d'une application Windows Forms.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="creating-the-service"></a>Création du service  
  
#### <a name="to-create-a-wcf-service"></a>Pour créer un service WCF  
  
1.  Dans le menu **Fichier** , pointez sur **Nouveau** , puis cliquez sur **Projet**.  
  
2.  Dans le **nouveau projet** boîte de dialogue, développez le **Visual Basic** ou **Visual C#** nœud et cliquez sur **WCF**, suivie **WCF Bibliothèque de service**. Cliquez sur **OK** pour ouvrir le projet.  
  
     ![Le projet de bibliothèque de Service WCF](../data-tools/media/wcf1.PNG "wcf1")  
  
    > [!NOTE]
    >  Un service actif est créé, qui peut être testé et est accessible. Les deux étapes suivantes montrent comment vous pouvez modifier la méthode par défaut pour utiliser un autre type de données. Dans une application réelle, vous ajouteriez également vos propres fonctions au service.  
  
3.  ![Le fichier IService1](../data-tools/media/wcf2.png "wcf2")  
  
     Dans **l’Explorateur de solutions**, double-cliquez sur IService1.vb ou IService1.cs et recherchez la ligne suivante :  
  
     [ ! code-csharp [WCFWalkthrough #4] (.. /Snippets/CSharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/IService1 (2).cs n° 4)] [ ! code-vb [WCFWalkthrough #4] (.. /Snippets/VisualBasic/VS_Snippets_VBCSharp/wcfwalkthrough/VB/IService1 (2).vb n° 4)]  
  
     Modifiez le type du paramètre `value` en `String` :  
  
     [!code-csharp[WCFWalkthrough#1](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1.cs#1)]
     [!code-vb[WCFWalkthrough#1](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1.vb#1)]  
  
     Dans le code ci-dessus, notez les attributs `<OperationContract()>` ou `[OperationContract]`. Ces attributs sont obligatoires pour toute méthode exposée par le service.  
  
4.  ![Le fichier Service1](../data-tools/media/wcf3.png "wcf3")  
  
     Dans **l’Explorateur de solutions**, double-cliquez sur Service1.vb ou Service1.cs et recherchez la ligne suivante :  
  
     [ ! code-csharp [WCFWalkthrough #5] (.. /Snippets/CSharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/Service1 (2).cs #5)] [ ! code-vb [WCFWalkthrough #5] (.. /Snippets/VisualBasic/VS_Snippets_VBCSharp/wcfwalkthrough/VB/Service1 (2).vb #5)]  
  
     Modifiez le type du paramètre value en `String` :  
  
     [!code-csharp[WCFWalkthrough#2](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/service1.cs#2)]
     [!code-vb[WCFWalkthrough#2](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/service1.vb#2)]  
  
## <a name="testing-the-service"></a>Test du service  
  
#### <a name="to-test-a-wcf-service"></a>Pour tester un service WCF  
  
1.  Appuyez sur **F5** pour exécuter le service. Un **Client Test WCF** formulaire s’affiche et charge le service.  
  
2.  Dans le **Client Test WCF** formulaire, double-cliquez sur le **GetData()** méthode sous **IService1**. Le **GetData** onglet s’affiche.  
  
     ![La méthode GetData&#40; &#41; méthode](../data-tools/media/wcf4.png "wcf4")  
  
3.  Dans le **demande** boîte, sélectionnez le **valeur** champ et le type `Hello`.  
  
     ![Le champ de valeur](../data-tools/media/wcf5.png "wcf5")  
  
4.  Cliquez sur le **Invoke** bouton. Si un **avertissement de sécurité** boîte de dialogue s’affiche, cliquez sur **OK**. Le résultat s’affichera dans le **réponse** boîte.  
  
     ![Le résultat dans la zone de réponse](../data-tools/media/wcf6.png "wcf6")  
  
5.  Sur le **fichier** menu, cliquez sur **Exit** pour fermer le formulaire de test.  
  
## <a name="accessing-the-service"></a>Accès au service  
  
#### <a name="to-reference-a-wcf-service"></a>Pour faire référence à un service WCF  
  
1.  Sur le **fichier** menu, pointez sur **ajouter** puis cliquez sur **nouveau projet**.  
  
2.  Dans le **nouveau projet** boîte de dialogue, développez le **Visual Basic** ou **Visual C#** nœud et sélectionnez **Windows**, puis sélectionnez **Windows Forms Application**. Cliquez sur **OK** pour ouvrir le projet.  
  
     ![Projet d’Application de Windows Forms](../data-tools/media/wcf7.png "wcf7")  
  
3.  Avec le bouton droit **WindowsApplication1** et cliquez sur **ajouter une référence de Service**. Le **ajouter une référence de Service** boîte de dialogue s’affiche.  
  
4.  Dans le **ajouter une référence de Service** boîte de dialogue, cliquez sur **Discover**.  
  
     ![La boîte de dialogue Ajouter une référence de Service](../data-tools/media/wcf8.png "wcf8")  
  
     **Service1** s’affichera dans le **Services** volet.  
  
5.  Cliquez sur **OK** pour ajouter la référence de service.  
  
#### <a name="to-build-a-client-application"></a>Pour générer une application cliente  
  
1.  Dans **l’Explorateur de solutions**, double-cliquez sur **Form1.vb** ou **Form1.cs** pour ouvrir le Concepteur de formulaires Windows s’il n’est pas déjà ouvert.  
  
2.  À partir de la **boîte à outils**, faites glisser un `TextBox` contrôle, un `Label` contrôle et un `Button` contrôle vers le formulaire.  
  
     ![Ajout de contrôles au formulaire](../data-tools/media/wcf9.png "wcf9")  
  
3.  Double-cliquez sur le contrôle `Button`, puis ajoutez le code suivant au gestionnaire d'événements `Click` :  
  
     [!code-csharp[WCFWalkthrough#3](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/form1.cs#3)]
     [!code-vb[WCFWalkthrough#3](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/form1.vb#3)]  
  
4.  Dans **l’Explorateur de solutions**, avec le bouton droit **WindowsApplication1** et cliquez sur **définir comme projet de démarrage**.  
  
5.  Appuyez sur **F5** pour exécuter le projet. Entrez un texte et cliquez sur le bouton. Le message « Vous avez entré : » s'affichera, suivi du texte que vous avez entré.  
  
     ![Formulaire affichant le résultat](../data-tools/media/wcf10.png "wcf10")  
  
## <a name="see-also"></a>Voir aussi  
 [Services Windows Communication Foundation et services de données WCF dans Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

