---
title: "Proc&#233;dure pas &#224; pas&#160;: Cr&#233;ation d’un Service de langage h&#233;rit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "services de langage (framework package managé), création"
ms.assetid: 6a5dd2c2-261b-4efd-a3f4-8fb90b73dc82
caps.latest.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 19
---
# Proc&#233;dure pas &#224; pas&#160;: Cr&#233;ation d’un Service de langage h&#233;rit&#233;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Utilisation des classes langage managé package framework \(MPF\) pour implémenter un service de langage dans [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] est simple. Vous avez besoin d’un VSPackage pour héberger le service de langage, le service de langage lui\-même et un analyseur pour votre langue.  
  
## Composants requis  
 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel \(SDK\) Visual Studio. Pour plus d'informations, consultez [Kit de développement logiciel Visual Studio](../../extensibility/visual-studio-sdk.md).  
  
## Emplacements du modèle de projet de package Visual Studio  
 Le modèle de projet Visual Studio Package figurent dans trois emplacements différents de modèle dans le **Nouveau projet** boîte de dialogue :  
  
1.  Sous l’extensibilité Visual Basic. Le langage par défaut du projet est Visual Basic.  
  
2.  Sous l’extensibilité C\#. Le langage par défaut du projet est C\#.  
  
3.  Sous l’extensibilité Autres types de projets. Le langage par défaut du projet est C\+\+.  
  
### Créez un VSPackage  
  
1.  Créez un VSPackage de nouveau avec le modèle de projet de Package Visual Studio.  
  
     Si vous ajoutez un service de langage à un VSPackage existant, ignorez les étapes suivantes et accéder directement à la procédure « Créer la classe de Service Language ».  
  
2.  Entrez le nom du projet MyLanguagePackage et cliquez sur **OK**.  
  
     Vous pouvez utiliser le nom que vous souhaitez. Ces procédures détaillées ici supposent MyLanguagePackage comme nom.  
  
3.  Sélectionnez [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] comme la langue et l’option pour générer un fichier de clé. Cliquez sur **Suivant**.  
  
4.  Entrez les informations appropriées de l’entreprise et le package. Cliquez sur **Suivant**.  
  
5.  Sélectionnez **commande**. Cliquez sur **Suivant**.  
  
     Si vous ne souhaitez pas prendre en charge les extraits de code, vous pouvez simplement cliquez sur Terminer et ignorez l’étape suivante.  
  
6.  Entrez **Insérer l’extrait de** comme le **nom de commande** et `cmdidInsertSnippet` pour le **ID de commande**. Cliquez sur **Terminer**.  
  
     Le **nom de la commande** et **ID de commande** peut être comme vous le souhaitez, ce sont des exemples.  
  
### Créer la classe de Service de langage  
  
1.  Dans **l’Explorateur de solutions**, avec le bouton droit sur le projet MyLanguagePackage, choisissez **Ajouter**, **référence**, puis choisissez le **Ajouter une nouvelle référence** bouton.  
  
2.  Dans le **Ajouter une référence** boîte de dialogue, sélectionnez **Microsoft.VisualStudio.Package.LanguageService** dans les **.NET** onglet, cliquez sur **OK**.  
  
     Cette opération doit être effectuée qu’une seule fois pour le projet de package du langage.  
  
3.  Dans **l’Explorateur de solutions**, avec le bouton droit sur le projet VSPackage et sélectionnez **Ajouter**, **classe**.  
  
4.  Assurez\-vous que **classe** est sélectionné dans la liste des modèles.  
  
5.  Entrez **MyLanguageService.cs** pour le nom du fichier de classe et cliquez sur **Ajouter**.  
  
     Vous pouvez utiliser le nom que vous souhaitez. Ces procédures détaillées ici supposent `MyLanguageService` comme nom.  
  
6.  Dans le fichier MyLanguageService.cs, ajoutez le code suivant `using` instructions.  
  
     [!code-cs[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_1.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_1.vb)]  
  
7.  Modifier la `MyLanguageService` classe de dérivation à partir de la <xref:Microsoft.VisualStudio.Package.LanguageService> classe :  
  
     [!code-cs[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_2.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_2.vb)]  
  
8.  Positionnez le curseur sur « LanguageService » et le **Modifier**, **IntelliSense** menu, sélectionnez **implémenter la classe abstraite**. Cela ajoute les méthodes minimales nécessaires pour implémenter une classe de service de langage.  
  
9. Implémenter les méthodes abstraites, comme décrit dans [L’implémentation d’un Service de langage](../../extensibility/internals/implementing-a-legacy-language-service2.md).  
  
### Inscrire le Service de langage  
  
1.  Ouvrez le fichier MyLanguagePackagePackage.cs et ajoutez le code suivant `using` instructions :  
  
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_3.vb)]
     [!code-cs[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_3.cs)]  
  
2.  Inscrire votre classe de service de langage, comme décrit dans [L’inscription d’un Service de langage](../../extensibility/internals/registering-a-legacy-language-service1.md). Cela inclut les attributs ProvideXX et les sections « Proffering du Service de langage ». Utilisez MyLanguageService où cette rubrique utilise TestLanguageService.  
  
### L’analyseur et le moteur d’analyse  
  
1.  Implémenter un analyseur et le moteur d’analyse pour votre langage, comme décrit dans [Scanneur et analyseur du Service de langage ancien](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).  
  
     Comment vous implémentez votre analyseur et le moteur d’analyse est dépend entièrement de vous et présentées dans cette rubrique.  
  
## Fonctionnalités du Service de langage  
 Pour implémenter chaque fonctionnalité dans le service de langage, vous généralement dérivez une classe de la classe de service de langage MPF appropriée, implémentez les méthodes abstraites que nécessaire et substituez les méthodes appropriées. Les classes que vous créerez et\/ou dérivez est dépend des fonctionnalités que vous souhaitez prendre en charge. Ces fonctionnalités sont décrites en détail dans [Fonctionnalités du Service de langage ancien](../../extensibility/internals/legacy-language-service-features1.md). La procédure suivante est l’approche générale à dériver une classe à partir des classes MPF.  
  
#### Dérivation d’une classe MPF  
  
1.  Dans **l’Explorateur de solutions**, avec le bouton droit sur le projet VSPackage et sélectionnez **Ajouter**, **classe**.  
  
2.  Assurez\-vous que **classe** est sélectionné dans la liste des modèles.  
  
     Entrez un nom pour le fichier de classe approprié et cliquez sur **Ajouter**.  
  
3.  Dans le nouveau fichier de classe, ajoutez le code suivant `using` instructions.  
  
     [!code-cs[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_4.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_4.vb)]  
  
4.  Modifiez la classe dérive de la classe MPF souhaitée.  
  
5.  Ajoutez un constructeur de classe qui prend au moins les mêmes paramètres que le constructeur de la classe de base et passer les paramètres de constructeur sur le constructeur de classe de base.  
  
     Par exemple, le constructeur d’une classe dérivée de la <xref:Microsoft.VisualStudio.Package.Source> classe peut se présenter comme suit :  
  
     [!code-cs[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_5.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_5.vb)]  
  
6.  À partir de la **Modifier**, **IntelliSense** menu, sélectionnez **implémenter la classe abstraite** si la classe de base a des méthodes abstraites qui doivent être implémentées.  
  
7.  Dans le cas contraire, placez le point d’insertion à l’intérieur de la classe et entrez la substitution de la méthode.  
  
     Par exemple, tapez `public override` pour afficher la liste de toutes les méthodes qui peuvent être substituées dans cette classe.  
  
## Voir aussi  
 [Implémentation d’un Service de langage hérité](../../extensibility/internals/implementing-a-legacy-language-service1.md)