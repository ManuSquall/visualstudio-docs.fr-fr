---
title: 'Procédure pas à pas : Création d’un Service de langage hérité | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], creating
ms.assetid: 6a5dd2c2-261b-4efd-a3f4-8fb90b73dc82
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fb1fc7b6c35b2ee6ef3a767f7093f2fa0e4cb972
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31144932"
---
# <a name="walkthrough-creating-a-legacy-language-service"></a>Procédure pas à pas : Création d’un Service de langage hérité
Utilisation des classes de langage de package managé framework (MPF) pour implémenter un service de langage dans [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] est simple. Vous avez besoin d’un VSPackage pour héberger le service de langage, le service de langage lui-même et un analyseur pour votre langue.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez [Visual Studio SDK](../../extensibility/visual-studio-sdk.md).  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Emplacements du modèle de projet de package Visual Studio  
 Le modèle de projet Visual Studio Package sont accessibles dans trois emplacements différents de modèle dans le **nouveau projet** boîte de dialogue :  
  
1.  Sous l’extensibilité Visual Basic. Le langage par défaut du projet est Visual Basic.  
  
2.  Sous l’extensibilité C#. Le langage par défaut du projet est C#.  
  
3.  Sous l’extensibilité Autres types de projets. Le langage par défaut du projet est C++.  
  
### <a name="create-a-vspackage"></a>Créer un VSPackage  
  
1.  Créer un nouveau VSPackage s’affiche avec le modèle de projet de Package Visual Studio.  
  
     Si vous ajoutez un service de langage à un VSPackage existant, ignorez les étapes suivantes et accéder directement à la procédure « Créer la classe de Service de langage ».  
  
2.  Entrez le nom du projet MyLanguagePackage et cliquez sur **OK**.  
  
     Vous pouvez utiliser le nom de votre choix. Ces procédures décrites ici supposent MyLanguagePackage comme nom.  
  
3.  Sélectionnez [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] comme la langue et de l’option pour générer un fichier de clé. Cliquez sur **Suivant**.  
  
4.  Entrez les informations appropriées de l’entreprise et le package. Cliquez sur **Suivant**.  
  
5.  Sélectionnez **commande de Menu**. Cliquez sur **Suivant**.  
  
     Si vous ne souhaitez pas prendre en charge des extraits de code, vous pouvez simplement cliquez sur Terminer et ignorer l’étape suivante.  
  
6.  Entrez **insérer l’extrait de code** comme le **nom de la commande** et `cmdidInsertSnippet` pour le **ID de commande**. Cliquez sur **Terminer**.  
  
     Le **nom de la commande** et **ID de commande** peut être tout ce que vous voulez, il s’agit juste d’exemples.  
  
### <a name="create-the-language-service-class"></a>Créer la classe de Service de langage  
  
1.  Dans **l’Explorateur de solutions**, avec le bouton droit sur le projet MyLanguagePackage, choisissez **ajouter**, **référence**, puis choisissez le **ajouter une nouvelle référence** bouton.  
  
2.  Dans le **ajouter une référence** boîte de dialogue, sélectionnez **Microsoft.VisualStudio.Package.LanguageService** dans les **.NET** onglet et cliquez sur **OK**.  
  
     Cela doit être effectué qu’une seule fois pour le projet de package de langue.  
  
3.  Dans **l’Explorateur de solutions**, avec le bouton droit sur le projet VSPackage, puis sélectionnez **ajouter**, **classe**.  
  
4.  Assurez-vous que **classe** est sélectionné dans la liste des modèles.  
  
5.  Entrez **MyLanguageService.cs** pour le nom du fichier de classe et cliquez sur **ajouter**.  
  
     Vous pouvez utiliser le nom de votre choix. Ces procédures décrites ici supposent `MyLanguageService` comme nom.  
  
6.  Dans le fichier MyLanguageService.cs, ajoutez le code suivant `using` instructions.  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_1.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_1.vb)]  
  
7.  Modifier la `MyLanguageService` classe à dériver le <xref:Microsoft.VisualStudio.Package.LanguageService> classe :  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_2.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_2.vb)]  
  
8.  Positionnez le curseur sur « LanguageService » et à partir de la **modifier**, **IntelliSense** menu, sélectionnez **implémenter une classe abstraite**. Cette opération ajoute les méthodes minimales nécessaires pour implémenter une classe de service de langage.  
  
9. Implémenter les méthodes abstraites, comme décrit dans [implémentation d’un Service de langage hérité](../../extensibility/internals/implementing-a-legacy-language-service2.md).  
  
### <a name="register-the-language-service"></a>Inscrire le Service de langage  
  
1.  Ouvrez le fichier MyLanguagePackagePackage.cs et ajoutez le code suivant `using` instructions :  
  
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_3.vb)]
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_3.cs)]  
  
2.  Inscrire votre classe de service de langage, comme décrit dans [l’inscription d’un Service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service1.md). Cela inclut les attributs de ProvideXX et les sections de « Proffering le Service de langage ». Utilisez MyLanguageService où cette rubrique utilise TestLanguageService.  
  
### <a name="the-parser-and-scanner"></a>L’analyseur et l’analyseur  
  
1.  Implémenter un analyseur et l’analyseur pour votre langue, comme décrit dans [Analyseur de Service de langage hérité et analyseur](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).  
  
     Façon dont vous implémentez votre analyseur et l’analyseur dépend entièrement de vous et dépasse le cadre de cette rubrique.  
  
## <a name="language-service-features"></a>Fonctionnalités de Service de langage  
 Pour implémenter chaque fonctionnalité dans le service de langage, vous en général, dérivez une classe de la classe de service de langage MPF appropriée, implémentez toutes les méthodes abstraites selon les besoins et substituez les méthodes appropriées. Créer et/ou de dériver de classes est dépend des fonctionnalités que vous souhaitez prendre en charge. Ces fonctionnalités sont décrites en détail dans [fonctionnalités de Service de langage hérité](../../extensibility/internals/legacy-language-service-features1.md). La procédure suivante est l’approche générale à dériver une classe à partir des classes MPF.  
  
#### <a name="deriving-from-an-mpf-class"></a>Dérivation d’une classe MPF  
  
1.  Dans **l’Explorateur de solutions**, avec le bouton droit sur le projet VSPackage, puis sélectionnez **ajouter**, **classe**.  
  
2.  Assurez-vous que **classe** est sélectionné dans la liste des modèles.  
  
     Entrez un nom approprié pour le fichier de classe, cliquez sur **ajouter**.  
  
3.  Dans le nouveau fichier de classe, ajoutez le code suivant `using` instructions.  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_4.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_4.vb)]  
  
4.  Modifiez la classe à dériver de la classe MPF souhaitée.  
  
5.  Ajoutez un constructeur de classe qui prend au moins les mêmes paramètres que le constructeur de la classe de base et passer les paramètres du constructeur une session sur le constructeur de classe de base.  
  
     Par exemple, le constructeur d’une classe dérivée de la <xref:Microsoft.VisualStudio.Package.Source> classe peut se présenter comme suit :  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_5.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_5.vb)]  
  
6.  À partir de la **modifier**, **IntelliSense** menu, sélectionnez **implémenter une classe abstraite** si la classe de base a des méthodes abstraites qui doivent être implémentées.  
  
7.  Dans le cas contraire, placez le point d’insertion à l’intérieur de la classe et entrez la substitution de méthode.  
  
     Par exemple, tapez `public override` pour afficher la liste de toutes les méthodes qui peuvent être substituées dans cette classe.  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation d’un Service de langage hérité](../../extensibility/internals/implementing-a-legacy-language-service1.md)