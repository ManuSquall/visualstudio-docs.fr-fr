---
title: Mise à jour vers MSTestV2
description: Découvrez comment effectuer une mise à jour de MSTestV1 vers MSTestV2
ms.custom: SEO-VS-2020
ms.date: 02/26/2021
ms.topic: conceptual
f1_keywords:
- vs.UnitTest.Migrate
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ffe45c444321a7efbaee0a2eb5729850a06c5910
ms.sourcegitcommit: 99b66b0f4ced46ead0b2506a103f974f40cc0076
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103366257"
---
# <a name="upgrade-from-mstestv1-to-mstestv2"></a>Mise à niveau de MSTestV1 vers MSTestV2

Vous pouvez mettre à niveau votre projet de test en reciblant la version MSTest référencée dans votre *. csproj* à partir de MSTestV1 vers MSTestV2. Toutes les fonctionnalités de MSTestV1 n’ayant pas été transmises à MSTestV2, certaines modifications peuvent être nécessaires pour résoudre les erreurs. Consultez [fonctionnalités MSTestV1 non prises en charge dans MSTestV2](#mstestv1-features-that-are-not-supported-in-mstestv2) pour comprendre quelles fonctionnalités ne fonctionneront plus. Certaines d’entre elles devront peut-être être supprimées de vos tests.

1. Supprimez la référence d’assembly à Microsoft. VisualStudio. QualityTools. UnitTestFramework de votre projet de test unitaire.
2. Ajoutez des références de package NuGet à MSTestV2, y compris les packages [MSTest. TestFrameWork](https://www.nuget.org/packages/MSTest.TestFramework) et [MSTest. TestAdapter](https://www.nuget.org/packages/MSTest.TestAdapter/) sur NuGet.org. Vous pouvez installer des packages dans la console du gestionnaire de package NuGet à l’aide des commandes suivantes :

    ```console
    PM> Install-Package MSTest.TestAdapter -Version 2.1.2
    PM> Install-Package MSTest.TestFramework -Version 2.1.2
    ```

### <a name="old-style-csproj-example"></a>Exemple de l’ancien style csproj

Exemple *. csproj* ciblant MSTestV1 :

```xml
<Reference Include="Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=10.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
  <Private>False</Private>
</Reference>
```

Exemple *. csproj* ciblant MSTestV2 :

```xml
<Reference Include="Microsoft.VisualStudio.TestPlatform.TestFramework, Version=14.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
  <HintPath>..\packages\MSTest.TestFramework.2.1.2\lib\net45\Microsoft.VisualStudio.TestPlatform.TestFramework.dll</HintPath>
</Reference>
```

> [!NOTE]
> Les projets de test codés de l’interface utilisateur ou les tests de charge Web ne sont pas compatibles avec MSTestV2. Ces types de projets ont été dépréciés. En savoir plus sur la désapprobation du [test codé de l’interface utilisateur](https://devblogs.microsoft.com/devops/changes-to-coded-ui-test-in-visual-studio-2019/) et la [désapprobation du test de charge Web](https://devblogs.microsoft.com/devops/cloud-based-load-testing-service-eol/).

### <a name="sdk-style-csproj-net-core-and-net-5"></a>Csproj de style SDK (.NET Core et .NET 5)

Si votre *. csproj* est le nouveau kit de développement logiciel (SDK) *. csproj* , vous utilisez probablement déjà MSTestV2. Vous pouvez trouver les packages NuGet pour [MSTestV2](https://www.nuget.org/packages/MSTest.TestFramework) et l' [adaptateur MSTestV2](https://www.nuget.org/packages/MSTest.TestAdapter/) sur NuGet.

Exemple :

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="16.7.1" />
  <PackageReference Include="MSTest.TestAdapter" Version="2.1.1" />
  <PackageReference Include="MSTest.TestFramework" Version="2.1.1" />
</ItemGroup>
```

## <a name="why-upgrade-to-mstestv2"></a>Pourquoi effectuer une mise à niveau vers MSTestV2 ?

Dans 2016, nous avons publié l’étape suivante dans l’évolution de l’infrastructure MSTest avec MSTestV2. Pour plus d’informations sur cette modification, consultez le billet de [blog](https://devblogs.microsoft.com/devops/taking-the-mstest-framework-forward-with-mstest-v2/)d’annonce.

* MSTestV2 est plus facile à acquérir et à mettre à jour, car il est fourni sous la forme d’un [package NuGet](https://www.nuget.org/packages/MSTest.TestFramework/).
* MSTestV2 est [Open source](https://github.com/microsoft/testfx).
* Prise en charge uniforme des plateformes d’application : MSTestV2 est une implémentation convergée qui offre une prise en charge d’application uniforme sur .NET Framework, .NET Core, ASP.NET Core et UWP. [En savoir plus](https://blogs.msdn.microsoft.com/devops/2016/09/01/announcing-mstest-v2-framework-support-for-net-core-1-0-rtm/).
* L’implémentation est entièrement multiplateforme (Windows, Linux, Mac). [En savoir plus](https://blogs.msdn.microsoft.com/devops/2017/04/05/mstest-v2-is-open-source/).
* MSTestV2 prend en charge le ciblage .NET Framework 4.5.0 et versions ultérieures, .NET Core 1,0 et versions ultérieures (applications Windows universelles 10 +), ASP.NET Core 1,0 et versions ultérieures et .NET 5 et versions ultérieures.
* Fournit un mécanisme d’extensibilité uniforme et unique pour les utilisateurs finaux. [En savoir plus](https://blogs.msdn.microsoft.com/devops/2017/07/18/extending-mstest-v2/).
* Fournit une `DataRow` prise en charge uniforme pour tous les projets de test basés sur MSTest. [En savoir plus](https://blogs.msdn.microsoft.com/devops/2017/02/25/mstest-v2-now-and-ahead/).
* Active le placement `TestCategory` de l’attribut au niveau d’une classe ou d’un assembly. [En savoir plus](https://blogs.msdn.microsoft.com/devops/2017/02/25/mstest-v2-now-and-ahead/).
* Les méthodes de test des classes de base définies dans un autre assembly sont désormais découvertes et exécutées à partir de la classe de test dérivée. Cette modification apporte un comportement cohérent avec les types de classe de test dérivés. Si ce comportement n’est pas requis pour des raisons de compatibilité, il peut être rétabli à l’aide des paramètres d’exécution suivants :

    ```xml
    <RunSettings>    
    <MSTest> 
      <EnableBaseClassTestMethodsFromOtherAssemblies>false</EnableBaseClassTestMethodsFromOtherAssemblies> 
    </MSTest> 
    </RunSettings>
    ```

* Fournit un contrôle plus précis de l’exécution en parallèle via [l’exécution parallèle de tests dans l’assembly](https://github.com/Microsoft/testfx-docs/blob/master/RFCs/004-In-Assembly-Parallel-Execution.md) . Cela permet l’exécution de tests dans un assembly en parallèle.
* La `TestCleanup` méthode sur un `TestClass` est appelée même si sa méthode correspondante `TestInitialize` échoue. [Détails du problème](https://github.com/Microsoft/testfx/issues/250).
* Le temps pris par `AssemblyInitialize` et `ClassInitialize` n’est pas compté en ce qui concerne la durée du test. Cette modification limite son impact sur un délai d’expiration de test.
* Les tests qui ne sont pas exécutables peuvent être configurés pour être marqués comme ayant échoué via la `MapNotRunnableToFailed` balise, qui fait partie du nœud adaptateur dans le `.runsettings` fichier.

    ```xml
    <RunSettings>    
    <MSTest> 
      <MapNotRunnableToFailed>true</MapNotRunnableToFailed> 
    </MSTest> 
    </RunSettings>
    ```

## <a name="mstestv1-features-that-are-not-supported-in-mstestv2"></a>Fonctionnalités MSTestV1 non prises en charge dans MSTestV2

*   Les tests ne peuvent pas être inclus dans un « test ordonné ».
*   L’adaptateur ne prend pas en charge la configuration par le biais d’un fichier *. testsettings* . Utilisez le nouveau [fichier *. RunSettings*](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md) pour la configuration de série de tests.
*   L’adaptateur ne prend pas en charge les listes de tests spécifiées en tant que fichier *. vsmdi* .
*   Le « projet de test codé de l’interface utilisateur » et les types « projet de test de performances Web et de charge » ne sont pas pris en charge. En savoir plus sur la désapprobation du [test codé de l’interface utilisateur](https://devblogs.microsoft.com/devops/changes-to-coded-ui-test-in-visual-studio-2019/) et la [désapprobation du test de charge Web](https://devblogs.microsoft.com/devops/cloud-based-load-testing-service-eol/).

## <a name="see-also"></a>Voir aussi

- [Configurer des séries de tests avec `.runsettings`](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
- [Test unitaire de votre code](../test/unit-test-your-code.md)
- [Déboguer des tests unitaires avec l’Explorateur de tests](../test/debug-unit-tests-with-test-explorer.md)
