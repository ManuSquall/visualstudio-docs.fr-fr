---
title: 'Procédure pas à pas : Création d’un Service WCF simple dans les Windows Forms | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WCF, walkthrough [Visual Studio]
- WCF, Visual Studio tools for
- WCF services
- WCF services, walkthrough
ms.assetid: 5fef1a64-27a4-4f10-aa57-29023e28a2d6
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: cacd1e15d2b20c4c24056416df4f9d25ea87474e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-a-simple-wcf-service-in-windows-forms"></a>Procédure pas à pas : Création d’un Service WCF simple dans les Windows Forms
Cette procédure pas à pas montre comment créer un simple service [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)], le tester et y accéder à partir d'une application Windows Forms.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="creating-the-service"></a>Création du service  
  
#### <a name="to-create-a-wcf-service"></a>Pour créer un service WCF  
  
1.  Dans le menu **Fichier** , pointez sur **Nouveau** , puis cliquez sur **Projet**.  
  
2.  Dans le **nouveau projet** boîte de dialogue, développez le **Visual Basic** ou **Visual C#** nœud et cliquez sur **WCF**, suivi par **WCF Bibliothèque de service**. Cliquez sur **OK** pour ouvrir le projet.  
  
     ![Le projet de bibliothèque du Service WCF](../data-tools/media/wcf1.PNG "wcf1")  
  
    > [!NOTE]
    >  Un service actif est créé, qui peut être testé et est accessible. Les deux étapes suivantes montrent comment vous pouvez modifier la méthode par défaut pour utiliser un autre type de données. Dans une application réelle, vous ajouteriez également vos propres fonctions au service.  
  
3.  ![Le fichier IService1](../data-tools/media/wcf2.png "wcf2")  
  
     Dans **l’Explorateur de solutions**, double-cliquez sur IService1.vb ou IService1.cs et recherchez la ligne suivante :  
  
     [!code-csharp[WCFWalkthrough#4](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.cs)]
     [!code-vb[WCFWalkthrough#4](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.vb)]  
  
     Modifier le type de le `value` paramètre en chaîne :  
  
     [!code-csharp[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.cs)]
     [!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.vb)]  
  
     Dans le code ci-dessus, notez les attributs `<OperationContract()>` ou `[OperationContract]`. Ces attributs sont obligatoires pour toute méthode exposée par le service.  
  
4.  ![Le fichier Service1](../data-tools/media/wcf3.png "wcf3")  
  
     Dans **l’Explorateur de solutions**, double-cliquez sur Service1.vb ou Service1.cs et recherchez la ligne suivante :  
  
     [!code-vb[WCFWalkthrough#5](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.vb)]
     [!code-csharp[WCFWalkthrough#5](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.cs)]  
  
     Modifier le type du paramètre value en chaîne :  
  
     [!code-csharp[WCFWalkthrough#2](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.cs)]
     [!code-vb[WCFWalkthrough#2](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.vb)]  
  
## <a name="testing-the-service"></a>Test du service  
  
#### <a name="to-test-a-wcf-service"></a>Pour tester un service WCF  
  
1.  Appuyez sur **F5** pour exécuter le service. A **Client Test WCF** formulaire s’affiche et charge le service.  
  
2.  Dans le **Client Test WCF** formulaire, double-cliquez sur le **GetData()** méthode sous **IService1**. Le **GetData** onglet s’affiche.  
  
     ![La méthode GetData&#40; &#41; méthode](../data-tools/media/wcf4.png "wcf4")  
  
3.  Dans le **demande** boîte, sélectionnez le **valeur** champ et type `Hello`.  
  
     ![Le champ de valeur](../data-tools/media/wcf5.png "wcf5")  
  
4.  Cliquez sur le **Invoke** bouton. Si un **avertissement de sécurité** boîte de dialogue s’affiche, cliquez sur **OK**. Le résultat s’affichera dans le **réponse** boîte.  
  
     ![Le résultat dans la zone réponse](../data-tools/media/wcf6.png "wcf6")  
  
5.  Sur le **fichier** menu, cliquez sur **Exit** pour fermer le formulaire de test.  
  
## <a name="accessing-the-service"></a>Accès au service  
  
#### <a name="to-reference-a-wcf-service"></a>Pour faire référence à un service WCF  
  
1.  Sur le **fichier** menu, pointez sur **ajouter** puis cliquez sur **nouveau projet**.  
  
2.  Dans le **nouveau projet** boîte de dialogue, développez le **Visual Basic** ou **Visual C#** nœud et sélectionnez **Windows**, puis sélectionnez **Application Windows Forms**. Cliquez sur **OK** pour ouvrir le projet.  
  
     ![Projet d’Application Windows Forms](../data-tools/media/wcf7.png "wcf7")  
  
3.  Avec le bouton droit **WindowsApplication1** et cliquez sur **ajouter une référence de Service**. Le **ajouter une référence de Service** boîte de dialogue s’affiche.  
  
4.  Dans le **ajouter une référence de Service** boîte de dialogue, cliquez sur **Discover**.  
  
     ![La boîte de dialogue Ajouter une référence de Service](../data-tools/media/wcf8.png "wcf8")  
  
     **Service1** s’affichera dans le **Services** volet.  
  
5.  Cliquez sur **OK** pour ajouter la référence de service.  
  
#### <a name="to-build-a-client-application"></a>Pour générer une application cliente  
  
1.  Dans **l’Explorateur de solutions**, double-cliquez sur **Form1.vb** ou **Form1.cs** pour ouvrir le Concepteur Windows Forms s’il n’est pas déjà ouvert.  
  
2.  À partir de la **boîte à outils**, faites glisser un `TextBox` (contrôle), un `Label` (contrôle) et un `Button` contrôle vers le formulaire.  
  
     ![Ajout de contrôles au formulaire](../data-tools/media/wcf9.png "wcf9")  
  
3.  Double-cliquez sur le contrôle `Button`, puis ajoutez le code suivant au gestionnaire d'événements `Click` :  
  
     [!code-csharp[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.cs)]
     [!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.vb)]  
  
4.  Dans **l’Explorateur de solutions**, avec le bouton droit **WindowsApplication1** et cliquez sur **définir comme projet de démarrage**.  
  
5.  Appuyez sur **F5** pour exécuter le projet. Entrez un texte et cliquez sur le bouton. Le message « Vous avez entré : » s'affichera, suivi du texte que vous avez entré.  
  
     ![Formulaire affichant le résultat](../data-tools/media/wcf10.png "wcf10")  
  
## <a name="see-also"></a>Voir aussi  
 [Services Windows Communication Foundation et services de données WCF dans Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)