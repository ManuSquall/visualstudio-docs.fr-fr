---
title: "Utilisation des membres Microsoft.VisualStudio.TestTools.UnitTesting dans les tests unitaires | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0fa335fd-e442-448f-913f-25a19df90a93
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "mlearned"
manager: "douge"
---
# Utilisation des membres Microsoft.VisualStudio.TestTools.UnitTesting dans les tests unitaires
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'Infrastructure de test unitaire prend en charge le test unitaire dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Utilisez les classes et les membres de l'espace de noms <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework> lorsque vous codez des tests unitaires.  Vous pouvez les utiliser lorsque vous avez écrit le test unitaire à partir de zéro ou lorsque vous affinez un test unitaire généré à partir de code que vous testez.  
  
## Groupes d'éléments  
 Afin de fournir une vue d'ensemble plus claire de l'Infrastructure de test unitaire, cette section organise les éléments de l'espace de noms UnitTesting en groupes de fonctionnalités connexes.  
  
> [!NOTE]
>  Les éléments d'attributs, dont les noms se terminent par la chaîne Attribut , peuvent être utilisés avec ou sans la chaîne Attribut.  Par exemple, les deux exemples de code suivants fonctionnent de manière identique :  
>   
>  `[TestClass()]`  
>   
>  `[TestClassAttribute()]`  
  
### Éléments utilisés pour les tests pilotés par les données  
 Utilisez les éléments suivants pour configurer des tests unitaires pilotés par les données.  Pour plus d'informations, consultez [Comment : créer un test unitaire piloté par des données](../test/how-to-create-a-data-driven-unit-test.md) et [Procédure pas à pas : utilisation d'un fichier de configuration pour définir une source de données](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md).  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataAccessMethod>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataSourceAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataSourceElement>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataSourceElementCollection>  
  
## Attributs utilisés pour établir un ordre d'appel  
 Un élément de code décoré avec l'un des attributs suivants est appelé au moment que vous spécifiez.  Pour plus d'informations, consultez [Anatomy of a Unit Test](http://msdn.microsoft.com/fr-fr/a03d1ee7-9999-4e7c-85df-7d9073976144).  
  
### Pour les assemblys  
 AssemblyInitialize et AssemblyCleanup sont appelés juste après le chargement de votre assembly et juste avant son déchargement.  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssemblyInitializeAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssemblyCleanupAttribute>  
  
### Pour les classes  
 ClassInitialize et ClassCleanup sont appelés juste après le chargement de votre classe et juste avant son déchargement.  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.ClassInitializeAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.ClassCleanupAttribute>  
  
### Pour les méthodes de test  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestInitializeAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestCleanupAttribute>  
  
## Attributs utilisés pour identifier des classes et des méthodes de test  
 Chaque classe de test doit avoir l'attribut TestClass et chaque méthode de test doit avoir l'attribut TestMethod.  Pour plus d'informations, consultez [Anatomy of a Unit Test](http://msdn.microsoft.com/fr-fr/a03d1ee7-9999-4e7c-85df-7d9073976144).  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestClassAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestMethodAttribute>  
  
## Classes Assert et exceptions connexes  
 Les tests unitaires peuvent vérifier un comportement d'application spécifique par leur utilisation de différents genres d'instructions, d'exceptions et d'attributs Assert.  Pour plus d'informations, consultez [Utilisation des classes Assert](../test/using-the-assert-classes.md).  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.Assert>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.CollectionAssert>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.StringAssert>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssertFailedException>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssertInconclusiveException>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.UnitTestAssertException>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.ExpectedExceptionAttribute>  
  
## La classe TestContext  
 Les attributs suivants et les valeurs qui leur sont assignées apparaissent dans la fenêtre de propriétés de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour une méthode de test particulière.  Ces attributs ne sont pas censés être accessibles par le biais du code du test unitaire.  Au lieu de cela, ils affectent la manière dont le test unitaire est utilisé ou exécuté, soit par vous par le biais de l'IDE de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], soit par le moteur de test de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Par exemple, certains de ces attributs apparaissent comme des colonnes dans la fenêtre du Gestionnaire de tests et la fenêtre Résultats des tests, ce qui signifie que vous pouvez les utiliser pour grouper et trier des tests et des résultats de tests.  TestPropertyAttribute est l'un de ces attributs ; il sert à ajouter des métadonnées arbitraires à des tests unitaires.  Vous pouvez par exemple l'utiliser pour stocker le nom d'une étape de test couverte par ce test, en marquant le test unitaire avec `[TestProperty("TestPass", "Accessibility")]`.  Ou vous pourriez l'utiliser pour stocker un indicateur du genre de test dont il s'agit : `[TestProperty("TestKind", "Localization")]`.  La propriété que vous créez à l'aide de cet attribut et la valeur de propriété que vous assignez sont toutes deux affichées dans la fenêtre de propriétés de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sous le titre **Spécifique au test**.  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.OwnerAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DeploymentItemAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DescriptionAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.HostTypeAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.IgnoreAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.PriorityAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestPropertyAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.WorkItemAttribute>  
  
## Classes de configuration de test  
  
-   <xref:Microsoft.TeamFoundation.TestManagement.Client.ObjectTypes>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestConfigurationSection>  
  
## Attributs utilisés pour générer des rapports  
 Les attributs de cette section établissent un rapport entre la méthode de test qu'ils décorent et des entités dans la hiérarchie de projet d'un projet d'équipe [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)].  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.CssIterationAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.CssProjectStructureAttribute>  
  
## Classes utilisées avec des accesseurs private  
 Comme indiqué dans [Using Publicize to Create a Private Accessor](http://msdn.microsoft.com/fr-fr/2056c6a7-6672-42a7-8f53-fead33c56deb), vous pouvez générer un test unitaire pour une méthode privée.  Cette génération crée une classe d'accesseur private qui instancie un objet de la classe PrivateObject.  La classe PrivateObject est une classe wrapper qui utilise la réflexion dans le cadre du processus d'accesseur private.  La classe PrivateType est semblable, mais elle est utilisée pour appeler des méthodes statiques privées au lieu de méthodes d'instance privées.  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.PrivateObject>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.PrivateType>  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework>