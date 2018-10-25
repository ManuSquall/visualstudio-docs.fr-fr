---
title: Guide pratique pour configurer des tests unitaires et cibler une version antérieure du .NET Framework | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: adb6c011-5abd-41d2-8ead-08cd7579bf37
caps.latest.revision: 14
ms.author: gewarren
manager: douge
ms.openlocfilehash: 978f4e3edeb83d5980d793d74cf209e8e8f7205e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49892790"
---
# <a name="how-to-configure-unit-tests-to-target-an-earlier-version-of-the-net-framework"></a>Guide pratique pour configurer des tests unitaires et cibler une version antérieure du .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quand vous créez un projet de test dans Microsoft Visual Studio, la version la plus récente du .NET Framework est définie en tant que cible, par défaut. De plus, si vous mettez à niveau des projets de test à partir de versions antérieures de Visual Studio, ceux-ci sont mis à niveau pour cibler la version la plus récente du .NET Framework. En modifiant les propriétés du projet, vous pouvez recibler explicitement le projet vers des versions antérieures du .NET Framework.  
  
 Vous pouvez créer des projets de test unitaire qui ciblent des versions spécifiques du .NET Framework. La version ciblée doit correspondre à la version 3.5 (ou une version ultérieure) et ne peut pas être une version client. Visual Studio assure la prise en charge de base suivante pour les tests unitaires qui ciblent des versions spécifiques :  
  
- Vous pouvez créer des projets de test unitaire et les cibler vers une version spécifique du .NET Framework.  
  
- Vous pouvez exécuter des tests unitaires qui ciblent une version spécifique du .NET Framework à partir de Visual Studio sur votre machine locale.  
  
- Vous pouvez exécuter des tests unitaires qui ciblent une version spécifique du .NET Framework en utilisant MSTest.exe à partir de l’invite de commandes.  
  
- Vous pouvez exécuter des tests unitaires sur un agent de build dans le cadre d’une build.  
  
  **Test des applications SharePoint**  
  
  Les fonctionnalités listées ci-dessus vous permettent également d’écrire des tests unitaires et des tests d’intégration pour les applications SharePoint à l’aide de Visual Studio. [!INCLUDE[crabout](../includes/crabout-md.md)] le développement des applications SharePoint à l’aide de Visual Studio, consultez [Créer des solutions SharePoint](http://msdn.microsoft.com/library/4bfb1e59-97c9-4594-93f8-3068b4eb9631), [Génération et débogage de solutions SharePoint](http://msdn.microsoft.com/library/c9e7c9ab-4eb3-40cd-a9b9-6c2a896f70ae) et [Vérification et débogage du code SharePoint](http://msdn.microsoft.com/library/b5f3bce2-6a51-41b1-a292-9e384bae420c).  
  
  **Limitations**  
  
  Les limitations suivantes s’appliquent quand vous reciblez vos projets de test pour utiliser des versions antérieures du .NET Framework :  
  
- Dans .NET Framework 3.5, le multiciblage est pris en charge pour les projets de test qui contiennent uniquement des tests unitaires. .NET Framework 3.5 ne prend pas en charge d’autres types de test, par exemple le test codé de l’interface utilisateur ou le test de charge. Le reciblage est bloqué pour les types de test qui ne sont pas des tests unitaires.  
  
- L’exécution de tests qui ciblent une version antérieure du .NET Framework est prise en charge uniquement par l’adaptateur hôte par défaut. Elle n’est pas prise en charge par l’adaptateur hôte ASP.NET. Les applications ASP.NET qui doivent s’exécuter dans le contexte d’un Serveur de développement ASP.NET doivent être compatibles avec la version actuelle du .NET Framework.  
  
- La prise en charge de la collecte de données est désactivée quand vous exécutez des tests qui prennent en charge le multiciblage .NET Framework 3.5. Vous pouvez exécuter la couverture du code à l’aide des outils en ligne de commande Visual Studio.  
  
- Les tests unitaires qui utilisent .NET Framework 3.5 ne peuvent pas s’exécuter sur une machine distante.  
  
- Vous ne pouvez pas cibler les tests unitaires vers les précédentes versions client du framework.  
  
### <a name="re-targeting-to-a-specific-version-of-the-net-framework-for-visual-basic-unit-test-projects"></a>Reciblage vers une version spécifique du .NET Framework pour les projets de test unitaire Visual Basic  
  
1.  Créez un projet de test unitaire Visual Basic. Dans le menu **Fichier**, choisissez **Nouveau**, puis **Projet**.  
  
     La boîte de dialogue **Nouveau projet** s’affiche.  
  
2.  Sous **Modèles installés**, développez **Visual Basic**. Sélectionnez **Test**, puis sélectionnez le modèle **Projet de test**.  
  
3.  Dans la zone de texte **Nom**, tapez un nom pour votre projet de test Visual Basic, puis choisissez **OK**.  
  
4.  Dans l’Explorateur de solutions, choisissez **Propriétés** dans le menu contextuel du nouveau projet de test Visual Basic.  
  
     Les propriétés de votre projet de test Visual Basic s’affichent.  
  
5.  Sous l’onglet **Compiler**, choisissez **Options avancées de compilation**, comme indiqué dans l’illustration suivante.  
  
     ![Options avancées de compilation](../test/media/howtoconfigureunittest35frameworka.png "HowToConfigureUnitTest35FrameworkA")  
  
6.  Utilisez la liste déroulante **Framework cible (toutes les configurations)** pour remplacer le framework cible par **.NET Framework 3.5** ou une version ultérieure, comme indiqué dans la légende B de l’illustration suivante. Ne spécifiez pas de version client.  
  
     ![Framework cible, liste déroulante](../test/media/howtoconfigureunitest35frameworkstepb.png "HowToConfigureUniTest35FrameworkStepB")  
  
### <a name="re-targeting-to-a-specific-version-of-the-net-framework-for-visual-c-unit-test-projects"></a>Reciblage vers une version spécifique du .NET Framework pour les projets de test unitaire Visual C#  
  
1.  Créez un projet de test unitaire Visual C#. Dans le menu **Fichier**, choisissez **Nouveau**, puis **Projet**.  
  
     La boîte de dialogue **Nouveau projet** s’affiche.  
  
2.  Sous **Modèles installés**, développez **Visual C#**. Sélectionnez **Test**, puis sélectionnez le modèle **Projet de test**.  
  
3.  Dans la zone de texte **Nom**, tapez un nom pour votre projet de test Visual C#, puis choisissez **OK**.  
  
4.  Dans l’Explorateur de solutions, choisissez **Propriétés** dans le menu contextuel de votre nouveau projet de test Visual C#.  
  
     Les propriétés de votre projet de test Visual C# s’affichent.  
  
5.  Sous l’onglet **Application**, choisissez **Framework cible**, puis **.NET Framework 3.5** ou une version ultérieure dans la liste déroulante pour changer le framework cible, comme indiqué dans l’illustration suivante. Ne spécifiez pas de version client.  
  
     ![Framework cible, liste déroulante](../test/media/howtoconfigureunittest35frameworkcsharp.png "HowToConfigureUnitTest35FrameworkCSharp")  
  
### <a name="re-targeting-to-a-specific-version-of-the-net-framework-for-ccli-unit-test-projects"></a>Reciblage vers une version spécifique du .NET Framework pour les projets de test unitaire C++/CLI  
  
1.  Créez un projet de test unitaire C++. Dans le menu **Fichier**, sélectionnez **Nouveau**, puis cliquez sur **Projet**.  
  
     La boîte de dialogue **Nouveau projet** s’affiche.  
  
    > [!WARNING]
    >  Pour créer des tests unitaires C++/CLI basés sur une version antérieure du .NET Framework pour Visual C++, vous devez utiliser la version correspondante de Visual Studio. Par exemple, pour cibler .NET Framework 3.5, vous devez installer [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)] et [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)] Service Pack 1.  
  
2.  Sous **Modèles installés**, développez **Visual C++**. Sélectionnez **Test**, puis sélectionnez le modèle **Projet de test**.  
  
3.  Dans la zone de texte **Nom**, tapez un nom pour votre projet de test Visual C++, puis cliquez sur **OK**.  
  
4.  Dans l’Explorateur de solutions, choisissez **Décharger le projet** à partir de votre nouveau projet de test Visual C++.  
  
5.  Dans l’Explorateur de solutions, choisissez le projet de test Visual C++ déchargé, puis choisissez **Modifier \<nom_projet>.vcxproj**.  
  
     Le fichier .vcxproj s’ouvre dans l’éditeur.  
  
6.  Affectez la version 3.5 ou une version ultérieure à `TargetFrameworkVersion` dans le `PropertyGroup` nommé `"Globals"`. Ne spécifiez pas de version client :  
  
    ```  
    <PropertyGroup Label="Globals">  
        <TargetName>DefaultTest</TargetName>  
        <ProjectTypes>{3AC096D0-A1C2-E12C-1390-A8335801FDAB};{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}</ProjectTypes>  
        <ProjectGUID>{CE16D77A-E364-4ACD-948B-1EB6218B0EA3}</ProjectGUID>  
        <TargetFrameworkVersion>3.5</TargetFrameworkVersion>  
        <Keyword>ManagedCProj</Keyword>  
        <RootNamespace>CPP_Test</RootNamespace>  
      </PropertyGroup>  
  
    ```  
  
7.  Enregistrez et fermez le fichier .vcxproj.  
  
8.  Dans l’Explorateur de solutions, choisissez **Recharger le projet** dans le menu contextuel de votre nouveau projet de test Visual C++.  
  
## <a name="see-also"></a>Voir aussi  
 [Création et exécution de tests unitaires pour le code existant](http://msdn.microsoft.com/en-us/e8370b93-085b-41c9-8dec-655bd886f173)   
 [Créer des solutions SharePoint](http://msdn.microsoft.com/library/4bfb1e59-97c9-4594-93f8-3068b4eb9631)   
 [Génération et débogage de solutions SharePoint](http://msdn.microsoft.com/library/c9e7c9ab-4eb3-40cd-a9b9-6c2a896f70ae)   
 [Paramètres avancés du compilateur, boîte de dialogue (Visual Basic)](../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md)



