---
title: 'Procédure pas à pas : création d’un service de langage hérité | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], creating
ms.assetid: 6a5dd2c2-261b-4efd-a3f4-8fb90b73dc82
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 694b1a53e72ca4e890e11befdc9b90f049e33dd1
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721779"
---
# <a name="walkthrough-creating-a-legacy-language-service"></a>Procédure pas à pas : création d’un service de langage hérité
L’utilisation des classes de langage de Managed package Framework (MPF) pour implémenter un service de langage dans [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] est simple. Vous avez besoin d’un VSPackage pour héberger le service de langage, le service de langage lui-même et un analyseur pour votre langue.

## <a name="prerequisites"></a>Configuration requise
 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez [Kit de développement logiciel (SDK) Visual Studio](../../extensibility/visual-studio-sdk.md).

## <a name="locations-for-the-visual-studio-package-project-template"></a>Emplacements du modèle de projet de package Visual Studio
 Le modèle de projet de package Visual Studio se trouve dans trois emplacements de modèle différents dans la boîte de dialogue **nouveau projet** :

1. Sous l’extensibilité Visual Basic. Le langage par défaut du projet est Visual Basic.

2. Sous l’extensibilité C#. Le langage par défaut du projet est C#.

3. Sous l’extensibilité Autres types de projets. Le langage par défaut du projet est C++.

### <a name="create-a-vspackage"></a>Créer un VSPackage

1. Créez un nouveau VSPackage avec le modèle de projet de package Visual Studio.

    Si vous ajoutez un service de langage à un VSPackage existant, ignorez les étapes suivantes et passez directement à la procédure « créer la classe de service de langage ».

2. Entrez MyLanguagePackage pour le nom du projet et cliquez sur **OK**.

    Vous pouvez utiliser le nom de votre choix. Les procédures décrites ici supposent que MyLanguagePackage est le nom.

3. Sélectionnez [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] comme langue et l’option permettant de générer un nouveau fichier de clé. Cliquez sur **Next**.

4. Entrez les informations appropriées sur la société et le package. Cliquez sur **Next**.

5. Sélectionnez la **commande de menu**. Cliquez sur **Next**.

    Si vous n’envisagez pas de prendre en charge les extraits de code, vous pouvez simplement cliquer sur Terminer et ignorer l’étape suivante.

6. Entrez l’extrait de code d' **insertion** comme **nom de commande** et `cmdidInsertSnippet` pour l’ID de **commande**. Cliquez sur **Finish**.

    Le **nom de commande** et l' **ID de commande** peuvent être les mêmes que vous le souhaitez. il s’agit simplement d’exemples.

### <a name="create-the-language-service-class"></a>Créer la classe de service de langage

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet MyLanguagePackage, choisissez **Ajouter**, **référence**, puis cliquez sur le bouton **Ajouter une nouvelle référence** .

2. Dans la boîte de dialogue **Ajouter une référence** , sélectionnez **Microsoft. VisualStudio. Package. LanguageService** dans l’onglet **.net** , puis cliquez sur **OK**.

     Cette opération ne doit être effectuée qu’une seule fois pour le projet de package de langue.

3. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet VSPackage, puis sélectionnez **Ajouter**, **classe**.

4. Assurez-vous que **classe** est sélectionné dans la liste modèles.

5. Entrez **MyLanguageService.cs** pour le nom du fichier de classe, puis cliquez sur **Ajouter**.

     Vous pouvez utiliser le nom de votre choix. Les procédures décrites ici supposent `MyLanguageService` comme nom.

6. Dans le fichier MyLanguageService.cs, ajoutez les directives `using` suivantes.

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_1.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_1.vb)]

7. Modifiez la classe `MyLanguageService` pour dériver de la classe <xref:Microsoft.VisualStudio.Package.LanguageService> :

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_2.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_2.vb)]

8. Placez le curseur sur « LanguageService » et, dans le menu **Edit**, **IntelliSense** , sélectionnez **implement abstract class**. Cela ajoute les méthodes minimales nécessaires pour implémenter une classe de service de langage.

9. Implémentez les méthodes abstraites, comme décrit dans [implémentation d’un service de langage hérité](../../extensibility/internals/implementing-a-legacy-language-service2.md).

### <a name="register-the-language-service"></a>Inscrire le service de langage

1. Ouvrez le fichier MyLanguagePackagePackage.cs et ajoutez les directives de `using` suivantes :

     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_3.vb)]
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_3.cs)]

2. Inscrivez votre classe de service de langage comme décrit dans [inscription d’un service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service1.md). Cela comprend les attributs ProvideXX et les sections « proffering the Language Service ». Utilisez MyLanguageService là où cette rubrique utilise TestLanguageService.

### <a name="the-parser-and-scanner"></a>Analyseur et analyseur

1. Implémentez un analyseur et un scanneur pour votre langue, comme décrit dans l’analyseur [et le scanneur du service de langage hérité](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).

     La façon dont vous implémentez votre analyseur et votre scanneur dépend entièrement du cadre de cette rubrique.

## <a name="language-service-features"></a>Fonctionnalités du service de langage
 Pour implémenter chaque fonctionnalité dans le service de langage, vous dérivez généralement une classe de la classe de service de langage MPF appropriée, implémentez les méthodes abstraites nécessaires et substituez les méthodes appropriées. Les classes que vous créez et/ou dérivez dépendent des fonctionnalités que vous envisagez de prendre en charge. Ces fonctionnalités sont décrites en détail dans [fonctionnalités du service de langage hérité](../../extensibility/internals/legacy-language-service-features1.md). La procédure suivante est l’approche générale de la dérivation d’une classe à partir des classes MPF.

#### <a name="deriving-from-an-mpf-class"></a>Dérivation à partir d’une classe MPF

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet VSPackage, puis sélectionnez **Ajouter**, **classe**.

2. Assurez-vous que **classe** est sélectionné dans la liste modèles.

     Entrez un nom approprié pour le fichier de classe, puis cliquez sur **Ajouter**.

3. Dans le nouveau fichier de classe, ajoutez les directives de `using` suivantes.

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_4.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_4.vb)]

4. Modifiez la classe pour qu’elle dérive de la classe MPF souhaitée.

5. Ajoutez un constructeur de classe qui accepte au moins les mêmes paramètres que le constructeur de la classe de base et transmettez les paramètres du constructeur au constructeur de la classe de base.

     Par exemple, le constructeur d’une classe dérivée de la classe <xref:Microsoft.VisualStudio.Package.Source> peut se présenter comme suit :

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_5.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_5.vb)]

6. Dans le menu **modifier**, **IntelliSense** , sélectionnez **implémenter une classe abstraite** si la classe de base a des méthodes abstraites qui doivent être implémentées.

7. Sinon, placez le signe insertion à l’intérieur de la classe et entrez la méthode à substituer.

     Par exemple, tapez `public override` pour afficher la liste de toutes les méthodes qui peuvent être substituées dans cette classe.

## <a name="see-also"></a>Voir aussi
- [Implémentation d’un service de langage hérité](../../extensibility/internals/implementing-a-legacy-language-service1.md)
