---
title: 'Procédure pas à pas : Création d’un Service de langage hérité | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- language services [managed package framework], creating
ms.assetid: 6a5dd2c2-261b-4efd-a3f4-8fb90b73dc82
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6097177f1287b96914ccb872afa952e5fe3f4682
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47507334"
---
# <a name="walkthrough-creating-a-legacy-language-service"></a>Procédure pas à pas : création d’un service de langage hérité
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [procédure pas à pas : création d’un Service de langage hérité](https://docs.microsoft.com/visualstudio/extensibility/internals/walkthrough-creating-a-legacy-language-service).  
  
Utilisation des classes de langage de framework (MPF) package managé pour implémenter un service de langage dans [!INCLUDE[csprcs](../../includes/csprcs-md.md)] est simple. Vous avez besoin d’un VSPackage pour héberger le service de langage, le service de langage lui-même et un analyseur pour votre langue.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez [Visual Studio SDK](../../extensibility/visual-studio-sdk.md).  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Emplacements du modèle de projet de package Visual Studio  
 Vous trouverez le modèle de projet de Package Visual Studio dans trois emplacements différents de modèle dans le **nouveau projet** boîte de dialogue :  
  
1.  Sous l’extensibilité Visual Basic. Le langage par défaut du projet est Visual Basic.  
  
2.  Sous l’extensibilité C#. Le langage par défaut du projet est C#.  
  
3.  Sous l’extensibilité Autres types de projets. Le langage par défaut du projet est C++.  
  
### <a name="create-a-vspackage"></a>Créer un VSPackage  
  
1.  Créer un nouveau VSPackage s’affiche avec le modèle de projet de Package Visual Studio.  
  
     Si vous ajoutez un service de langage à un VSPackage existant, ignorez les étapes suivantes et accéder directement à la procédure « Créer la classe de Service de langage ».  
  
2.  Entrez MyLanguagePackage pour le nom du projet et cliquez sur **OK**.  
  
     Vous pouvez utiliser le nom de votre choix. Ces procédures détaillées ici supposent MyLanguagePackage comme nom.  
  
3.  Sélectionnez [!INCLUDE[csprcs](../../includes/csprcs-md.md)] en tant que la langue et l’option pour générer un fichier de clé. Cliquez sur **Suivant**.  
  
4.  Entrez les informations appropriées de l’entreprise et de package. Cliquez sur **Suivant**.  
  
5.  Sélectionnez **commande de Menu**. Cliquez sur **Suivant**.  
  
     Si vous ne souhaitez pas prendre en charge des extraits de code, vous pouvez simplement cliquez sur Terminer et ignorer l’étape suivante.  
  
6.  Entrez **insérer l’extrait de code** en tant que le **nom de commande** et `cmdidInsertSnippet` pour le **ID de commande**. Cliquez sur **Terminer**.  
  
     Le **nom de la commande** et **ID de commande** peut être tout ce que vous voulez, il s’agit uniquement d’exemples.  
  
### <a name="create-the-language-service-class"></a>Créer la classe de Service de langage  
  
1.  Dans **l’Explorateur de solutions**, avec le bouton droit sur le projet MyLanguagePackage, choisissez **ajouter**, **référence**, puis choisissez le **ajouter une nouvelle référence** bouton.  
  
2.  Dans le **ajouter une référence** boîte de dialogue, sélectionnez **Microsoft.VisualStudio.Package.LanguageService** dans le **.NET** onglet et cliquez sur **OK**.  
  
     Cette opération doit être effectuée qu’une seule fois pour le projet de package de langage.  
  
3.  Dans **l’Explorateur de solutions**, avec le bouton droit sur le projet VSPackage et sélectionnez **ajouter**, **classe**.  
  
4.  Assurez-vous que **classe** est sélectionné dans la liste des modèles.  
  
5.  Entrez **MyLanguageService.cs** pour le nom du fichier de classe et cliquez sur **ajouter**.  
  
     Vous pouvez utiliser le nom de votre choix. Ces procédures détaillées ici supposent `MyLanguageService` comme nom.  
  
6.  Dans le fichier MyLanguageService.cs, ajoutez le code suivant `using` instructions.  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#1](../../snippets/csharp/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/cs/mylanguageservice.cs#1)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#1](../../snippets/visualbasic/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/vb/mylanguageservice.vb#1)]  
  
7.  Modifier le `MyLanguageService` classe à dériver à partir de la <xref:Microsoft.VisualStudio.Package.LanguageService> classe :  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#2](../../snippets/csharp/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/cs/mylanguageservice.cs#2)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#2](../../snippets/visualbasic/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/vb/mylanguageservice.vb#2)]  
  
8.  Positionnez le curseur sur « LanguageService » et à partir de la **modifier**, **IntelliSense** menu, sélectionnez **implémenter une classe abstraite**. Cette opération ajoute le nombre minimal de méthodes nécessaires pour implémenter une classe de service de langage.  
  
9. Implémenter les méthodes abstraites, comme décrit dans [implémentation d’un Service de langage hérité](../../extensibility/internals/implementing-a-legacy-language-service2.md).  
  
### <a name="register-the-language-service"></a>Inscrire le Service de langage  
  
1.  Ouvrez le fichier MyLanguagePackagePackage.cs et ajoutez le code suivant `using` instructions :  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#3](../../snippets/csharp/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/cs/mylanguagepackagepackage.cs#3)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#3](../../snippets/visualbasic/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/vb/mylanguagepackagepackage.vb#3)]  
  
2.  Inscrire votre classe de service de langage, comme décrit dans [l’inscription d’un Service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service1.md). Cela inclut les attributs de ProvideXX et les sections de « Proffering du Service de langage ». Utilisez MyLanguageService où cette rubrique utilise TestLanguageService.  
  
### <a name="the-parser-and-scanner"></a>L’analyseur et l’analyseur  
  
1.  Implémenter un analyseur et le moteur d’analyse pour votre langage, comme décrit dans [Analyseur de Service de langage hérité et scanneur](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).  
  
     Comment implémenter votre analyseur et le moteur d’analyse dépend entièrement de vous et dépasse le cadre de cette rubrique.  
  
## <a name="language-service-features"></a>Fonctionnalités de Service de langage  
 Pour implémenter chaque fonctionnalité dans le service de langage, vous en général, dérivez une classe à partir de la classe de service de langage MPF appropriée implémentez toutes les méthodes abstraites en fonction des besoins et substituez les méthodes appropriées. Les classes vous créer et/ou dérivez est dépend des fonctionnalités que vous souhaitez prendre en charge. Ces fonctionnalités sont abordées en détail dans [fonctionnalités de Service de langage hérité](../../extensibility/internals/legacy-language-service-features1.md). La procédure suivante est l’approche générale à dériver une classe à partir des classes MPF.  
  
#### <a name="deriving-from-an-mpf-class"></a>Dérivation à partir d’une classe MPF  
  
1.  Dans **l’Explorateur de solutions**, avec le bouton droit sur le projet VSPackage et sélectionnez **ajouter**, **classe**.  
  
2.  Assurez-vous que **classe** est sélectionné dans la liste des modèles.  
  
     Entrez un nom pour le fichier de classe approprié et cliquez sur **ajouter**.  
  
3.  Dans le nouveau fichier de classe, ajoutez le code suivant `using` instructions.  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#4](../../snippets/csharp/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/cs/mysource.cs#4)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#4](../../snippets/visualbasic/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/vb/mysource.vb#4)]  
  
4.  Modifiez la classe à dériver à partir de la classe MPF souhaitée.  
  
5.  Ajoutez un constructeur de classe qui prend au moins les mêmes paramètres que le constructeur de la classe de base et passer les paramètres de constructeur une session sur le constructeur de classe de base.  
  
     Par exemple, le constructeur pour une classe dérivée de la <xref:Microsoft.VisualStudio.Package.Source> classe peut se présenter comme suit :  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#5](../../snippets/csharp/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/cs/mysource.cs#5)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#5](../../snippets/visualbasic/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/vb/mysource.vb#5)]  
  
6.  À partir de la **modifier**, **IntelliSense** menu, sélectionnez **implémenter une classe abstraite** si la classe de base a toutes les méthodes abstraites qui doivent être implémentées.  
  
7.  Sinon, positionner le signe insertion à l’intérieur de la classe et entrez la substitution de méthode.  
  
     Par exemple, tapez `public override` pour afficher la liste de toutes les méthodes qui peuvent être substituées dans cette classe.  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation d’un service de langage hérité](../../extensibility/internals/implementing-a-legacy-language-service1.md)

