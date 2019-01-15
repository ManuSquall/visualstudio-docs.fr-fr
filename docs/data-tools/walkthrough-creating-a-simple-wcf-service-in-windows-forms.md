---
title: 'Procédure pas à pas : Création d’un service WCF simple dans Windows Forms'
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
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 466514f0bfd343dc985021a3a081739a91946f8e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53882063"
---
# <a name="walkthrough-create-a-simple-wcf-service-in-windows-forms"></a>Procédure pas à pas : Créer un service WCF simple dans les Windows Forms

Cette procédure pas à pas montre comment créer un simple service [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)], le tester et y accéder à partir d'une application Windows Forms.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="create-the-service"></a>Créer le service

### <a name="to-create-a-wcf-service"></a>Pour créer un service WCF

1.  Dans le menu **Fichier** , pointez sur **Nouveau** , puis cliquez sur **Projet**.

2.  Dans la boîte de dialogue **Nouveau projet**, développez le nœud **Visual Basic** ou **Visual C#**, puis cliquez sur **WCF** et sur **Bibliothèque du service WCF**. Cliquez sur **OK** pour ouvrir le projet.

     ![Projet Bibliothèque du service WCF](../data-tools/media/wcf1.png)

    > [!NOTE]
    >  Un service actif est créé, qui peut être testé et est accessible. Les deux étapes suivantes montrent comment vous pouvez modifier la méthode par défaut pour utiliser un autre type de données. Dans une application réelle, vous ajouteriez également vos propres fonctions au service.

3.  ![Fichier IService1](../data-tools/media/wcf2.png)

     Dans l’**Explorateur de solutions**, double-cliquez sur **IService1.vb** ou **IService1.cs**, et recherchez la ligne suivante :

     [!code-csharp[WCFWalkthrough#4](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.cs)]
     [!code-vb[WCFWalkthrough#4](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.vb)]

     Modifier le type de le `value` paramètre en chaîne :

     [!code-csharp[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.cs)]
     [!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.vb)]

     Dans le code ci-dessus, notez les attributs `<OperationContract()>` ou `[OperationContract]`. Ces attributs sont obligatoires pour toute méthode exposée par le service.

4.  ![Fichier Service1](../data-tools/media/wcf3.png)

     Dans l’**Explorateur de solutions**, double-cliquez sur **Service1.vb** ou **Service1.cs**, puis recherchez la ligne suivante :

     [!code-vb[WCFWalkthrough#5](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.vb)]
     [!code-csharp[WCFWalkthrough#5](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.cs)]

     Modifier le type de le `value` paramètre en chaîne :

     [!code-csharp[WCFWalkthrough#2](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.cs)]
     [!code-vb[WCFWalkthrough#2](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.vb)]

## <a name="test-the-service"></a>Tester le service

### <a name="to-test-a-wcf-service"></a>Pour tester un service WCF

1.  Appuyez sur **F5** pour exécuter le service. Un **Client Test WCF** formulaire s’affiche et charge le service.

2.  Dans le formulaire **Client test WCF**, double-cliquez sur la méthode **GetData()** sous **IService1**. Le **GetData** onglet s’affiche.

     ![La méthode GetData&#40; &#41; (méthode)](../data-tools/media/wcf4.png)

3.  Dans la zone **Demande**, sélectionnez le champ **Valeur** et tapez `Hello`.

     ![Champ de valeur](../data-tools/media/wcf5.png)

4.  Cliquez sur le bouton **Appeler**. Si un **avertissement de sécurité** boîte de dialogue s’affiche, cliquez sur **OK**. Le résultat s’affiche dans le **réponse** boîte.

     ![Résultat dans la zone Réponse](../data-tools/media/wcf6.png)

5.  Dans le menu **Fichier**, cliquez sur **Quitter** pour fermer le formulaire de test.

## <a name="access-the-service"></a>Accéder au Service

### <a name="to-reference-a-wcf-service"></a>Pour faire référence à un service WCF

1.  Dans le menu **Fichier**, pointez sur **Ajouter**, puis cliquez sur **Nouveau projet**.

2.  Dans le **nouveau projet** boîte de dialogue, développez le **Visual Basic** ou **Visual C#**  nœud, sélectionnez **Windows**, puis sélectionnez  **Windows Forms Application**. Cliquez sur **OK** pour ouvrir le projet.

     ![Projet Application Windows Forms](../data-tools/media/wcf7.png)

3.  Cliquez avec le bouton droit sur **WindowsApplication1**, puis cliquez sur **Ajouter une référence de service**. Le **ajouter une référence de Service** boîte de dialogue s’affiche.

4.  Dans la boîte de dialogue **Ajouter une référence de service**, cliquez sur **Découvrir**.

     ![Boîte de dialogue Ajouter une référence de service](../data-tools/media/wcf8.png)

     **Service1** affiche dans le **Services** volet.

5.  Cliquez sur **OK** pour ajouter la référence de service.

### <a name="to-build-a-client-application"></a>Pour générer une application cliente

1.  Dans l’**Explorateur de solutions**, double-cliquez sur **Form1.vb** ou **Form1.cs** pour ouvrir le Concepteur Windows Forms, s’il ne l’est pas déjà.

2.  À partir de la **boîte à outils**, faites glisser vers le formulaire un contrôle `TextBox`, un contrôle `Label` et un contrôle `Button`.

     ![Ajout de contrôles au formulaire](../data-tools/media/wcf9.png)

3.  Double-cliquez sur le contrôle `Button`, puis ajoutez le code suivant au gestionnaire d'événements `Click` :

     [!code-csharp[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.cs)]
     [!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.vb)]

4.  Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur **WindowsApplication1**, puis cliquez sur **Définir comme projet de démarrage**.

5.  Appuyez sur **F5** pour exécuter le projet. Entrez un texte et cliquez sur le bouton. L’étiquette affiche « vous avez entré : » et affiche le texte que vous avez entré.

     ![Formulaire affichant le résultat](../data-tools/media/wcf10.png)

## <a name="see-also"></a>Voir aussi

- [Services Windows Communication Foundation et services de données WCF dans Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)