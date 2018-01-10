---
title: Utilisation des membres Microsoft.VisualStudio.TestTools.UnitTesting dans les tests unitaires | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: 251843d3e5a32ddedfe4f9081bd52330a457fe24
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2018
---
# <a name="using-microsoftvisualstudiotesttoolsunittesting-members-in-unit-tests"></a>Utilisation des membres Microsoft.VisualStudio.TestTools.UnitTesting dans les tests unitaires
Le framework de test unitaire prend en charge le test unitaire dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Utilisez les classes et les membres de l’espace de noms <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework> quand vous codez des tests unitaires. Vous pouvez les utiliser quand vous écrivez un test unitaire de bout en bout, ou que vous affinez un test unitaire généré à partir du code que vous testez.  
  
## <a name="groups-of-elements"></a>Groupes d’éléments  
 Pour fournir une vue d’ensemble plus claire du framework de test unitaire, cette section présente les éléments de l’espace de noms UnitTesting sous forme de groupes de fonctionnalités connexes.  
  
> [!NOTE]
>  Les éléments d’attribut, dont les noms finissent par la chaîne Attribute, peuvent être utilisés avec ou sans la chaîne Attribute. Par exemple, les deux exemples de code suivants fonctionnent de manière identique :  
>   
>  `[TestClass()]`  
>   
>  `[TestClassAttribute()]`  
  
### <a name="elements-used-for-data-driven-testing"></a>Éléments utilisés pour les tests pilotés par les données  
 Utilisez les éléments suivants pour configurer des tests unitaires pilotés par les données. Pour plus d’informations, consultez [Guide pratique pour créer un test unitaire piloté par les données](../test/how-to-create-a-data-driven-unit-test.md) et [Procédure pas à pas : utilisation d’un fichier de configuration pour définir une source de données](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md).  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataAccessMethod  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataSourceAttribute 
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataSourceElement  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataSourceElementCollection  
  
## <a name="attributes-used-to-establish-a-calling-order"></a>Attributs utilisés pour établir un ordre d’appel  
 Un élément de code décoré avec l’un des attributs suivants est appelé au moment spécifié. Pour plus d’informations, consultez [Anatomie d’un test unitaire](http://msdn.microsoft.com/en-us/a03d1ee7-9999-4e7c-85df-7d9073976144).  
  
### <a name="for-assemblies"></a>Pour les assemblys  
 AssemblyInitialize et AssemblyCleanup sont appelés juste après le chargement de votre assembly et juste avant son déchargement.  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssemblyInitializeAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssemblyCleanupAttribute  
  
### <a name="for-classes"></a>Pour les classes  
 ClassInitialize et ClassCleanup sont appelés juste après le chargement de votre classe et juste avant son déchargement.  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.ClassInitializeAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.ClassCleanupAttribute  
  
### <a name="for-test-methods"></a>Pour les méthodes de test  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestInitializeAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestCleanupAttribute  
  
## <a name="attributes-used-to-identify-test-classes-and-methods"></a>Attributs utilisés pour identifier les classes et méthodes de test  
 Chaque classe de test doit avoir l’attribut TestClass, et chaque méthode de test doit avoir l’attribut TestMethod. Pour plus d’informations, consultez [Anatomie d’un test unitaire](http://msdn.microsoft.com/en-us/a03d1ee7-9999-4e7c-85df-7d9073976144).  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestClassAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestMethodAttribute  
  
## <a name="assert-classes-and-related-exceptions"></a>Classes Assert et exceptions connexes  
 Les tests unitaires permettent de vérifier le comportement d’une application spécifique à l’aide de différents genres d’instruction, d’exception et d’attribut Assert. Pour plus d’informations, consultez [Utilisation des classes Assert](../test/using-the-assert-classes.md).  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.Assert 
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.CollectionAssert  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.StringAssert  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssertFailedException  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssertInconclusiveException  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.UnitTestAssertException  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.ExpectedExceptionAttribute  
  
## <a name="the-testcontext-class"></a>TestContext, classe  
 Les attributs suivants et les valeurs qui leur sont assignées apparaissent dans la fenêtre Propriétés de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour une méthode de test particulière. Ces attributs ne sont pas censés être accessibles via le code du test unitaire. À la place, ils affectent la façon dont le test unitaire est utilisé ou exécuté, soit par vous au travers de l’IDE de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], soit par le moteur de test de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Par exemple, certains de ces attributs apparaissent sous forme de colonnes dans la fenêtre Test Manager et la fenêtre Résultats des tests, ce qui signifie que vous pouvez les utiliser pour regrouper et trier les tests et les résultats des tests. C’est le cas de TestPropertyAttribute, le genre d’attribut qui vous permet d’ajouter des métadonnées arbitraires aux tests unitaires. Par exemple, vous pouvez l’utiliser pour stocker le nom d’une étape de test couverte par ce test, en marquant le test unitaire avec `[TestProperty("TestPass", "Accessibility")]`. Vous pouvez également l’utiliser pour stocker un indicateur du genre de test : `[TestProperty("TestKind", "Localization")]`. La propriété que vous créez à l’aide de cet attribut et la valeur de propriété que vous assignez sont affichées dans la fenêtre Propriétés de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sous le titre **Spécifique au test**.  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.OwnerAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DeploymentItemAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DescriptionAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.HostTypeAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.IgnoreAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.PriorityAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestPropertyAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.WorkItemAttribute  
  
## <a name="test-configuration-classes"></a>Classes de configuration de test  
  
-   Microsoft.TeamFoundation.TestManagement.Client.ObjectTypes>  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestConfigurationSection  
  
## <a name="attributes-used-for-generating-reports"></a>Attributs utilisés pour générer des rapports  
 Les attributs de cette section lient la méthode de test qu’ils décorent aux entités de la hiérarchie de projet d’un projet d’équipe [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)].  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.CssIterationAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.CssProjectStructureAttribute  
  
## <a name="classes-used-with-private-accessors"></a>Classes utilisées avec des accesseurs private  
 Comme indiqué dans [Utilisation de Publicize pour créer un accesseur private](http://msdn.microsoft.com/en-us/2056c6a7-6672-42a7-8f53-fead33c56deb), vous pouvez générer un test unitaire pour une méthode privée. Cette génération crée une classe d’accesseur private, qui instancie un objet de la classe PrivateObject. La classe PrivateObject est une classe wrapper qui utilise la réflexion dans le cadre du processus d’accesseur private. La classe PrivateType est similaire, mais elle est utilisée pour appeler des méthodes statiques privées au lieu d’appeler des méthodes d’instance privées.  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.PrivateObject  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.PrivateType  
  
## <a name="see-also"></a>Voir aussi  
 Microsoft.VisualStudio.TestPlatform.UnitTestFramework
