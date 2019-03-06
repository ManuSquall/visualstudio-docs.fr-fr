---
title: Utilisation des membres Microsoft.VisualStudio.TestTools.UnitTesting dans les tests unitaires
ms.date: 03/02/2018
ms.topic: reference
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 12c1b35288ac5857ac2971ffc6cbdddd40aa5c40
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55942178"
---
# <a name="use-the-mstest-framework-in-unit-tests"></a>Utiliser le framework MSTest dans les tests unitaires

Le framework [MSTest](<xref:Microsoft.VisualStudio.TestTools.UnitTesting>) prend en charge les tests unitaires dans Visual Studio. Utilisez les classes et les membres dans l’espace de noms <xref:Microsoft.VisualStudio.TestTools.UnitTesting> lorsque vous codez des tests unitaires. Vous pouvez également les utiliser lorsque vous affinez un test unitaire qui a été généré à partir du code.

## <a name="framework-members"></a>Membres du framework

Pour fournir une vue d’ensemble plus claire du framework de test unitaire, cette section présente les membres de l’espace de noms <xref:Microsoft.VisualStudio.TestTools.UnitTesting> sous forme de groupes de fonctionnalités connexes.

> [!NOTE]
> Les éléments d’attribut, dont les noms finissent par « Attribute », peuvent être utilisés avec ou sans la mention « Attribute » à la fin. Par exemple, les deux exemples de code suivants fonctionnent de manière identique :
>
> `[TestClass()]`
>
> `[TestClassAttribute()]`

### <a name="members-used-for-data-driven-testing"></a>Membres utilisés pour les tests pilotés par les données

Utilisez les éléments suivants pour configurer des tests unitaires pilotés par les données. Pour plus d’informations, consultez [Créer un test unitaire piloté par les données](../test/how-to-create-a-data-driven-unit-test.md) et [Utiliser un fichier de configuration pour définir une source de données](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataAccessMethod>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElement>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElementCollection>

## <a name="attributes-used-to-establish-a-calling-order"></a>Attributs utilisés pour établir un ordre d’appel

Un élément de code décoré avec l’un des attributs suivants est appelé au moment spécifié. Pour plus d’informations, consultez [Anatomie d’un test unitaire](https://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144).

### <a name="attributes-for-assemblies"></a>Attributs pour les assemblys

AssemblyInitialize et AssemblyCleanup sont appelés juste après le chargement de votre assembly et juste avant son déchargement.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyCleanupAttribute>

### <a name="attributes-for-classes"></a>Attributs pour les classes

ClassInitialize et ClassCleanup sont appelés juste après le chargement de votre classe et juste avant son déchargement.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassCleanupAttribute>

### <a name="attributes-for-test-methods"></a>Attributs pour les méthodes de test

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute>

## <a name="attributes-used-to-identify-test-classes-and-methods"></a>Attributs utilisés pour identifier les classes et méthodes de test

Chaque classe de test doit avoir l’attribut `TestClass`, et chaque méthode de test doit avoir l’attribut `TestMethod`. Pour plus d’informations, consultez [Anatomie d’un test unitaire](https://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute>

## <a name="assert-classes-and-related-exceptions"></a>Classes Assert et exceptions connexes

Les tests unitaires permettent de vérifier le comportement d’une application spécifique à l’aide de différents genres d’assertions, d’exceptions et d’attributs. Pour plus d’informations, consultez [Utilisation des classes Assert](../test/using-the-assert-classes.md).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute>

## <a name="the-testcontext-class"></a>Classe TestContext

Les attributs suivants et les valeurs qui leur sont assignées apparaissent dans la fenêtre Propriétés de Visual Studio pour une méthode de test particulière. Ces attributs ne sont pas censés être accessibles via le code du test unitaire. Au lieu de cela, ils affectent les façons dont le test unitaire est utilisé ou exécuté, par vous via l’IDE de Visual Studio ou par le moteur de test de Visual Studio. Par exemple, certains de ces attributs apparaissent sous forme de colonnes dans la fenêtre **Test Manager** et la fenêtre **Résultats des tests**, ce qui signifie que vous pouvez les utiliser pour regrouper et trier les tests et les résultats des tests. C’est le cas de <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>, le genre d’attribut qui vous permet d’ajouter des métadonnées arbitraires aux tests unitaires. Par exemple, vous pouvez l’utiliser pour stocker le nom d’une étape de test couverte par ce test, en marquant le test unitaire avec `[TestProperty("TestPass", "Accessibility")]`. Vous pouvez également l’utiliser pour stocker un indicateur du genre de test avec `[TestProperty("TestKind", "Localization")]`. La propriété que vous créez à l’aide de cet attribut et la valeur de propriété que vous assignez sont affichées dans la fenêtre **Propriétés** de Visual Studio sous le titre **Spécifique au test**.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DeploymentItemAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DescriptionAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.IgnoreAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.WorkItemAttribute>

## <a name="test-configuration-classes"></a>Classes de configuration de test

- <xref:Microsoft.TeamFoundation.TestManagement.Client.ObjectTypes>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection>

## <a name="attributes-used-to-generate-reports"></a>Attributs utilisés pour générer des rapports

Les attributs de cette section lient la méthode de test qu’ils décorent aux entités de la hiérarchie de projet d’un projet d’équipe Team Foundation Server.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssIterationAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssProjectStructureAttribute>

## <a name="classes-used-with-private-accessors"></a>Classes utilisées avec des accesseurs private

Vous pouvez générer un test unitaire pour une méthode privée. Cette génération crée une classe d’accesseur private, qui instancie un objet de la classe <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject>. La classe <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject> est une classe wrapper qui utilise la réflexion dans le cadre du processus d’accesseur private. La classe <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateType> est similaire, mais elle est utilisée pour appeler des méthodes statiques privées au lieu d’appeler des méthodes d’instance privées.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateType>

## <a name="see-also"></a>Voir aussi

- Documentation de référence <xref:Microsoft.VisualStudio.TestTools.UnitTesting>
