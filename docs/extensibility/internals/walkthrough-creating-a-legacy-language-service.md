---
title: 'Procédure pas à pas : Création d’un service de langue héritée (fr) Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], creating
ms.assetid: 6a5dd2c2-261b-4efd-a3f4-8fb90b73dc82
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59ec18ab0c97ec89422e06f5b33804adcc750d5a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703685"
---
# <a name="walkthrough-creating-a-legacy-language-service"></a>Procédure pas à pas : création d’un service de langage hérité
Il est simple d’utiliser les cours de langue [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] du cadre de forfait géré (MPF) pour mettre en œuvre un service linguistique. Vous avez besoin d’un VSPackage pour accueillir le service linguistique, le service linguistique lui-même, et un analyseur pour votre langue.

## <a name="prerequisites"></a>Prérequis
 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, voir [Visual Studio SDK](../../extensibility/visual-studio-sdk.md).

## <a name="locations-for-the-visual-studio-package-project-template"></a>Emplacements du modèle de projet de package Visual Studio
 Le modèle de projet de paquet de studio visuel peut être trouvé dans trois emplacements différents de modèle dans la boîte de dialogue **de nouveau projet** :

1. Sous l’extensibilité Visual Basic. Le langage par défaut du projet est Visual Basic.

2. Sous l’extensibilité C#. Le langage par défaut du projet est C#.

3. Sous l’extensibilité Autres types de projets. Le langage par défaut du projet est C++.

### <a name="create-a-vspackage"></a>Créer un VSPackage

1. Créez un nouveau VSPackage avec le modèle de projet Visual Studio Package.

    Si vous ajoutez un service linguistique à un VSPackage existant, sautez les étapes suivantes et allez directement à la procédure « Créer la classe de service linguistique ».

2. Entrez MyLanguagePackage pour le nom du projet et cliquez **sur OK**.

    Vous pouvez utiliser le nom que vous voulez. Ces procédures détaillées ici supposent MyLanguagePackage comme le nom.

3. Sélectionnez [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] comme langue et la possibilité de générer un nouveau fichier clé. Cliquez sur **Suivant**.

4. Entrez les informations appropriées sur l’entreprise et l’emballage. Cliquez sur **Suivant**.

5. Sélectionnez **Menu Command**. Cliquez sur **Suivant**.

    Si vous n’avez pas l’intention de prendre en charge les extraits de code, vous pouvez simplement cliquer sur Finition et ignorer l’étape suivante.

6. **Entrez Insérer Snippet** comme **nom de commande** et `cmdidInsertSnippet` pour l’ID de **commande**. Cliquez sur **Terminer**.

    Le **nom de commande** et **l’ID de commande** peuvent être ce que vous voulez, ce ne sont que des exemples.

### <a name="create-the-language-service-class"></a>Créer la classe de service linguistique

1. Dans **Solution Explorer**, cliquez à droite sur le projet MyLanguagePackage, choisissez **Ajouter**, **Référence**, puis choisissez le bouton Ajouter une **nouvelle référence.**

2. Dans la boîte de dialogue **Add Reference,** sélectionnez **Microsoft.VisualStudio.Package.LanguageService** dans **l’onglet .NET** et cliquez **sur OK**.

     Cela ne doit être fait qu’une seule fois pour le projet de paquet linguistique.

3. Dans **Solution Explorer**, cliquez à droite sur le projet VSPackage et sélectionnez **Ajouter**, **Classe**.

4. Assurez-vous que **la classe** est sélectionnée dans la liste des modèles.

5. Entrez **MyLanguageService.cs** pour le nom du fichier de classe et cliquez sur **Ajouter**.

     Vous pouvez utiliser le nom que vous voulez. Ces procédures détaillées `MyLanguageService` ici supposent comme le nom.

6. Dans le fichier MyLanguageService.cs, ajoutez `using` les directives suivantes.

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_1.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_1.vb)]

7. Modifier `MyLanguageService` la classe pour <xref:Microsoft.VisualStudio.Package.LanguageService> dériver de la classe :

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_2.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_2.vb)]

8. Placez le curseur sur "LanguageService" et à partir du menu **Edit**, **IntelliSense,** **sélectionnez Implement Abstract Class**. Cela ajoute les méthodes minimales nécessaires à la mise en œuvre d’une classe de service linguistique.

9. Mettre en œuvre les méthodes abstraites décrites dans [la mise en œuvre d’un service de langue héritée](../../extensibility/internals/implementing-a-legacy-language-service2.md).

### <a name="register-the-language-service"></a>Enregistrer le service linguistique

1. Ouvrez le fichier MyLanguagePackagePackage.cs et `using` ajoutez les directives suivantes :

     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_3.vb)]
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_3.cs)]

2. Enregistrez votre classe de service linguistique tel que décrit dans [l’enregistrement d’un service de langue héritée](../../extensibility/internals/registering-a-legacy-language-service1.md). Cela comprend les attributs ProvideXX et les sections « Fournir le service linguistique ». Utilisez MyLanguageService où ce sujet utilise TestLanguageService.

### <a name="the-parser-and-scanner"></a>Le Parser et scanner

1. Implémentez un analyseur et un scanner pour votre langue tel que décrit dans [Legacy Language Service Parser et Scanner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).

     La façon dont vous implémentez votre analyseur et scanner est entièrement à vous et est au-delà de la portée de ce sujet.

## <a name="language-service-features"></a>Caractéristiques du service linguistique
 Pour implémenter chaque fonctionnalité du service linguistique, vous dérivez généralement une classe de la classe de service linguistique MPF appropriée, implémentez toutes les méthodes abstraites au besoin et l’emportez sur les méthodes appropriées. Les classes que vous créez et/ou dont vous dérivez dépendent des fonctionnalités que vous avez l’intention de prendre en charge. Ces fonctionnalités sont discutées en détail dans [Legacy Language Service Features](../../extensibility/internals/legacy-language-service-features1.md). La procédure suivante est l’approche générale pour retirer une classe des classes du MPF.

#### <a name="deriving-from-an-mpf-class"></a>Dérivé d’une classe MPF

1. Dans **Solution Explorer**, cliquez à droite sur le projet VSPackage et sélectionnez **Ajouter**, **Classe**.

2. Assurez-vous que **la classe** est sélectionnée dans la liste des modèles.

     Entrez un nom approprié pour le fichier de classe et cliquez sur **Ajouter**.

3. Dans le nouveau fichier de `using` classe, ajoutez les directives suivantes.

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_4.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_4.vb)]

4. Modifier la classe pour dériver de la classe MPF souhaitée.

5. Ajoutez un constructeur de classe qui prend au moins les mêmes paramètres que le constructeur de la classe de base et transmettez les paramètres du constructeur au constructeur de la classe de base.

     Par exemple, le constructeur d’une <xref:Microsoft.VisualStudio.Package.Source> classe dérivée de la classe peut ressembler à ce qui suit :

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_5.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_5.vb)]

6. À partir du menu **Edit**, **IntelliSense,** **sélectionnez Implémentez** la classe abstraite si la classe de base a des méthodes abstraites qui doivent être mises en œuvre.

7. Sinon, placez le caret à l’intérieur de la classe et entrez dans la méthode pour être remplacé.

     Par exemple, `public override` tapez pour voir une liste de toutes les méthodes qui peuvent être remplacées dans cette classe.

## <a name="see-also"></a>Voir aussi
- [Implémentation d’un service de langage hérité](../../extensibility/internals/implementing-a-legacy-language-service1.md)
