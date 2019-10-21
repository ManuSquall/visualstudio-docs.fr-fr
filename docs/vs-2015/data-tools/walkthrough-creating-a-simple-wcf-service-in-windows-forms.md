---
title: 'Procédure pas à pas : création d’un service WCF simple dans Windows Forms | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- WCF, walkthrough [Visual Studio]
- WCF, Visual Studio tools for
- WCF services
- WCF services, walkthrough
ms.assetid: 5fef1a64-27a4-4f10-aa57-29023e28a2d6
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 366567a13ad23ab19ffd88f19997b92025abe952
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671076"
---
# <a name="walkthrough-creating-a-simple-wcf-service-in-windows-forms"></a>Procédure pas à pas : création d’un service WPF simple dans Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette procédure pas à pas montre comment créer un simple service [!INCLUDE[vsindigo](../includes/vsindigo-md.md)], le tester et y accéder à partir d'une application Windows Forms.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="creating-the-service"></a>Création du service

#### <a name="to-create-a-wcf-service"></a>Pour créer un service WCF

1. Dans le menu **Fichier** , pointez sur **Nouveau** , puis cliquez sur **Projet**.

2. Dans la boîte de dialogue **Nouveau projet**, développez le nœud **Visual Basic** ou **Visual C#** , puis cliquez sur **WCF** et sur **Bibliothèque du service WCF**. Cliquez sur **OK** pour ouvrir le projet.

     ![Le projet de bibliothèque du service WCF](../data-tools/media/wcf1.PNG "wcf1")

    > [!NOTE]
    > Un service actif est créé, qui peut être testé et est accessible. Les deux étapes suivantes montrent comment vous pouvez modifier la méthode par défaut pour utiliser un autre type de données. Dans une application réelle, vous ajouteriez également vos propres fonctions au service.

3. ![Fichier IService1](../data-tools/media/wcf2.png "wcf2")

     Dans **Explorateur de solutions**, double-cliquez sur IService1. vb ou IService1.cs et recherchez la ligne suivante :

     [!code-csharp[WCFWalkthrough#4](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1_2.cs#4)]
     [!code-vb[WCFWalkthrough#4](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1_2.vb#4)]

     Modifiez le type du paramètre `value` en `String` :

     [!code-csharp[WCFWalkthrough#1](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1.cs#1)]
     [!code-vb[WCFWalkthrough#1](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1.vb#1)]

     Dans le code ci-dessus, notez les attributs `<OperationContract()>` ou `[OperationContract]`. Ces attributs sont obligatoires pour toute méthode exposée par le service.

4. ![Le fichier Service1](../data-tools/media/wcf3.png "wcf3")

     Dans **Explorateur de solutions**, double-cliquez sur Service1. vb ou Service1.cs et recherchez la ligne suivante :

     [!code-csharp[WCFWalkthrough#5](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/service1_2.cs#5)]
     [!code-vb[WCFWalkthrough#5](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/service1_2.vb#5)]

     Modifiez le type du paramètre value en `String` :

     [!code-csharp[WCFWalkthrough#2](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/service1.cs#2)]
     [!code-vb[WCFWalkthrough#2](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/service1.vb#2)]

## <a name="testing-the-service"></a>Test du service

#### <a name="to-test-a-wcf-service"></a>Pour tester un service WCF

1. Appuyez sur **F5** pour exécuter le service. Un formulaire de **client test WCF** s’affiche et le service est chargé.

2. Dans le formulaire **Client test WCF**, double-cliquez sur la méthode **GetData()** sous **IService1**. L’onglet **GetData** s’affiche.

     ![La méthode&#40; &#41; GetData](../data-tools/media/wcf4.png "wcf4")

3. Dans la zone **Demande**, sélectionnez le champ **Valeur** et tapez `Hello`.

     ![Champ de valeur](../data-tools/media/wcf5.png "wcf5")

4. Cliquez sur le bouton **Appeler**. Si une boîte de dialogue d' **avertissement de sécurité** s’affiche, cliquez sur **OK**. Le résultat s’affichera dans la zone de **réponse** .

     ![Résultat dans la zone de réponse](../data-tools/media/wcf6.png "wcf6")

5. Dans le menu **Fichier**, cliquez sur **Quitter** pour fermer le formulaire de test.

## <a name="accessing-the-service"></a>Accès au service

#### <a name="to-reference-a-wcf-service"></a>Pour faire référence à un service WCF

1. Dans le menu **Fichier**, pointez sur **Ajouter**, puis cliquez sur **Nouveau projet**.

2. Dans la boîte de dialogue **nouveau projet** , développez le nœud **Visual Basic** ou **visuel C#**  , sélectionnez **Windows**, puis sélectionnez **Windows Forms application**. Cliquez sur **OK** pour ouvrir le projet.

     ![Windows Forms projet d’application](../data-tools/media/wcf7.png "wcf7")

3. Cliquez avec le bouton droit sur **WindowsApplication1**, puis cliquez sur **Ajouter une référence de service**. La boîte de dialogue **Ajouter une référence de service** s’affiche.

4. Dans la boîte de dialogue **Ajouter une référence de service**, cliquez sur **Découvrir**.

     ![Boîte de dialogue Ajouter une référence de service](../data-tools/media/wcf8.png "wcf8")

     **Service1** s’affichera dans le volet **services** .

5. Cliquez sur **OK** pour ajouter la référence de service.

#### <a name="to-build-a-client-application"></a>Pour générer une application cliente

1. Dans l’**Explorateur de solutions**, double-cliquez sur **Form1.vb** ou **Form1.cs** pour ouvrir le Concepteur Windows Forms, s’il ne l’est pas déjà.

2. À partir de la **boîte à outils**, faites glisser vers le formulaire un contrôle `TextBox`, un contrôle `Label` et un contrôle `Button`.

     ![Ajout de contrôles au formulaire](../data-tools/media/wcf9.png "wcf9")

3. Double-cliquez sur le contrôle `Button`, puis ajoutez le code suivant au gestionnaire d'événements `Click` :

     [!code-csharp[WCFWalkthrough#3](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/form1.cs#3)]
     [!code-vb[WCFWalkthrough#3](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/form1.vb#3)]

4. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur **WindowsApplication1**, puis cliquez sur **Définir comme projet de démarrage**.

5. Appuyez sur **F5** pour exécuter le projet. Entrez un texte et cliquez sur le bouton. Le message « Vous avez entré : » s'affichera, suivi du texte que vous avez entré.

     ![Formulaire présentant le résultat](../data-tools/media/wcf10.png "wcf10")

## <a name="see-also"></a>Voir aussi
 [Services Windows Communication Foundation et services de données WCF dans Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
